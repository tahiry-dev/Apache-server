# Apache-server
![rsz_apache2](https://user-images.githubusercontent.com/47100064/173199767-4f28c231-0bbc-4614-9f50-52e6fe55d1aa.jpg)

## INSTALLATION

- Mettre a jour la liste des paquets d'installation
   
   `apt-get update`
   
- Puis installer Apache2 avec APT

   `apt install apache2`
   
Après avoir laissé la commande s’exécuter, tous les paquets requis sont installés et nous pouvons le tester en tapant notre adresse IP pour le serveur web

## CONFIGURATION

Par défaut, Apache est livré avec un site de par défaut (celui que nous avons vu à l’étape précédente). 

Nous pouvons modifier son contenu dans 

`/var/www/html` 

ou ses paramètres en éditant son fichier Virtual Host qui se trouve dans 

`/etc/apache2/sites-enabled/000-default.conf`.

#### CREATION DE SITE WEB POUR TEST

Nous allons laisser la configuration par défaut de Apache et mettre en place notre propre configuration dans « hei.exemple.com».

Commençons donc par créer un dossier pour notre nouveau site Web dans `/var/www/” en exécutant

`sudo mkdir /var/www/hei/`

Maintenant que nous avons un répertoire créé pour notre site, on va avoir besoin  d'un fichier HTML. 
Allons dans notre nouvelle répertoire:

`cd /var/www/hei/`

et ajoutons le fichier html par:

`nano index.html`

Puis copier les codes suivantes:

    <html>
      <head>
        <title>HEI TEST</title>
      </head>
      <body>
        <p>Hello HEI PAGE</p>
      </body>
    </html>
 
#### CONFIGURATION DU HOST
Nous commençons cette étape en allant dans le répertoire des fichiers de configuration

`cd /etc/apache2/sites-available/`

Il faut maintenant faire une copie du dossier VirtualHost pour créer notre fichier de configuration.

`sudo cp 000-default.conf hei.conf`

On peut maintenant l'éditer

`sudo nano hei.conf`

Et y ajouté notre e-mail en cas d'erreur

`ServerAdmin votreEmail@exemple.com`

Le fichier par défaut "/var/www/hei/" ne contient pas un "ServerName", nous devrons donc l’ajouter et le définir en l'ajouté quelque ligne:

`ServerName hei.example.com`

#### Activation du fichier VirtualHost
Après avoir configuré notre site Web, nous devons activer le fichier de configuration et lancé le serveur. Pour ce faire, il faut utiliser les commandes suivantes:
  
  `sudo a2ensite hei.conf`
  
  `systemctl  reload apache2`
  


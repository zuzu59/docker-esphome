# docker_esphome
Petit docker-compose pour faire tourner ESPhome en stand alone sur son ordi ou un serveur du cloud

zf220925.1707


## Buts
Le but de ce projet c'est de pouvoir démarrer une instance Docker ESPhome pour pouvoir utiliser ESPhome en stand alone sur son ordi ou serveur cloud.


## Principes
ESPhome, est un environnement de développement pour la familles des microcontrôleur ESP. C'est très facile de développer pour un microcontrôleur ESP depuis ESPhome. Même que c'est plus facile que de développer qu'avec l'Arduino IDE, car ici, tout se passe dans un browser !

Généralement ESPhome *arrive* en bundle avec *Home Assistant*. Ici on peut l'utiliser sans devoir installer *Home Assistant*

https://esphome.io/


## Utilisation
### Installation
Comme cela fonctionne avec Docker, il faut installer en premier Docker sur sa machine !

Pour linux, on peut le faire très facilement ainsi:

```
curl -s -L https://raw.githubusercontent.com/zuzu59/deploy-proxmox/master/install_docker.sh | bash -s --
```

Pour les autres platteformes, il faut lire la documentation d'installation de Docker.

Après il faut récupérer ce dépôt avec:
```
cd ~/
git clone https://github.com/zuzu59/docker-esphome.git
cd docker-esphome
```


### Configuration de esphome
Il n'y a rien à configurer pour démarrer ESPhome, mais toute sa configuration ainsi que les projets ESPhome vont se trouver dans le dossier esphome enfant à ce projet. C'est donc ce dossier qu'il faudra sauvegarder si l'on désire garder ses projets ou *aller* sur une autre machine



### Démarrage
Pour le démarrer il faut simplement faire ceci:
```
./start.sh
```

### Utilisation de notre serveur S3
Et après quand cela à terminé de démarrer, on peut utiliser ESPhome tout simplement depuis son browser:

http://0.0.0.0:6052


### Arrêt
Pour l'arrêter, simplement:
```
./stop.sh
```

### Pour tout effacer !
Attention, ça efface vraiment toute la partie Docker sur la machine, donc faire **attention** s'il y a des autres utilisations de Docker !
```
./stop.sh
./purge.sh
sudo rm -rf data/ meta/
```


### Soyons foufou, faisons-le tourner sur Gitpod juste pour faire joujou !
Ce projet tourne très bien sur Gitpod pour juste voir comment cela fonctionne !

De plus on a une puisse dingue sur Gitpod, donc cela compile nettement plus rapidement que sur un *RASPI*

Il suffit juste de cliquer sur le *bouton* GITPOD sur Github pour démarrer Gitpod et après dans la fenêtre terminal de Gitpod, il faut le *démarrer* comme indiqué plus haut.

Le *firmware* de l'ESP compilé se trouve dans un dossier du style:

 /workspace/docker-esphome/esphome/config/.esphome/build/toto/.pioenvs/toto
 
 et il porte le nom de *firmware.bin*
 

## Sources
https://hub.docker.com/r/esphome/esphome

https://esphome.io/guides/getting_started_command_line.html

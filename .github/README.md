# Laradock.io

Go to laradock website for more information about laradock: https://laradock.io

This repository is a fork of http://github.com/laradock/laradock and contains the configuration to easily deploy the Forus backend.

## Guide to run forus-backend

- Clone forus repository via github or command line:

```
git clone https://github.com/teamforus/forus 
```

- Clone submodules: backend, frontend, laradock, notification recursively

```
git submodule update --init --recursive --remote 
```

- Install Docker Desktop

https://www.docker.com/products/docker-desktop

- cd into laradock/ and build and run mysql, nginx and phpmyadmin containers

```
docker-compose up -d nginx mysql phpmyadmin
```

- Enter workspace container 
```
docker-compose exec --user=laradock workspace bash
``` 

- run composer install and migrations
```
composer install
php artisan migrate --seed
```

extra:

- add forus.test to hosts to replace localhost:80
```
sudo nano /etc/hosts 
# add line to file:
127.0.0.1 forus.test
```


- to refresh db use:
```
php artisan migrate:refresh --seed
```
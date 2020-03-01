# Drupal 8 - Docker Local Development

Docker enviroment setting up for Drupal 8 local development

Drupal version: 8.8.2

## Clone this project

```sh
git clone https://github.com/dalenguyen/docker4drupal8.git
cd docker4drupal8
```

## Before bringing up containers

This command will install Drupal 8.8.2 to drupal/web folder. For Windows user, you can skip this step. Instead, you have download drupal 8 from the main website and put in under drupal/web folder.

```sh
sh drupal-install.sh
```

## Getting started

Manage the containers

```sh
docker-compose up -d
docker-compose down
```

## Change your hosts file 

Please update your /etc/hosts in order to visit the site and the dashboard

```sh
## Drupal 8 Docker
127.0.0.1       drupal8.localhost:8080
127.0.0.1       portainer.drupal8.localhost:8080
```

## Database management

Export database

```sh
docker exec drupal8_mysql /usr/bin/mysqldump -u root --password=password drupal > drupal/backup.sql
```

Import database

```sh
cat drupal/backup.sql  | docker exec -i drupal8_mysql /usr/bin/mysql -u root --password=password drupal
```

## Notes

DO NOT FORGET use correct hostname for mysql. host name of MySQL is to __drupal8_mysql__ when you install Drupal.
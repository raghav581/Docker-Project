# Docker-Project
Raghav
<br>This project is consist of two environments in docker.</br>
# 1. MySql
<br>Used to store the backend part of host website.</br>
# 2. Joomla
<br>Main host website.</br>

![Docker](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcSWDPX2omT-_AXyB3eE07KeJM5wm5FF6jL5xA&usqp=CAU)

```YAML
  
    version:  '3.1'

    services:
        dbos:
          image: mysql:5.7
          volumes:
            - mysql1_storage_new:/var/lib/mysql
          restart: always
          environment:
            MYSQL_ROOT_PASSWORD: rootpass
            MYSQL_USER: raghav
            MYSQL_PASSWORD: raghavsql
            MYSQL_DATABASE: mydb



        joomla_os:
          image: joomla
          restart: always
          depends_on:
            - dbos
          links:
            - dbos:mysql
          ports:
            - 8080:80
          environment:
            JOOMLA_DB_HOST: dbos
            JOOMLA_DB_USER: raghav
            JOOMLA_DB_PASSWORD: raghavjoomla
            JOOMLA_DB_NAME: mydb
          volumes:
            - db_storage_new:/var/www/html

    volumes:
        db_storage_new:
        mysql1_storage_new:
```

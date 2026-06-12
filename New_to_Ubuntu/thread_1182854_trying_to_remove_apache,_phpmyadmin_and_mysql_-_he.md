---
title: "trying to remove apache, phpmyadmin and mysql - help"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by kapi on 2009-06-09
Am trying to start from a fresh as have had nothing but problems.

so i want to unistall apache2, mysqlserver and phpmyadmin

not too sure of the commands though

---

### Post by jenkinbr on 2009-06-09
sudo apt-get remove apache2* mysql-server* phpmyadmin

if you want to also remove php, add 'php5*' to that list.

Hope this helps.

---

### Post by Celauran on 2009-06-09
I'd use purge over remove to make sure the config files are also removed.

```
sudo aptitude purge apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql phpmyadmin
```

---

### Post by jenkinbr on 2009-06-09
> **Celauran said:**
> I'd use purge over remove to make sure the config files are also removed.

```
sudo aptitude purge apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql phpmyadmin
```
Good point.

---


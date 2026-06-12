---
title: "Linux Ubuntu server questions"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by exiler200 on 2009-01-20
hello all im kinda new to linux...
i want to instal l2j on ubuntu i need to instal first some app's
my question is how can i install and run them?
app's:
Java
MySQL 5.0
Navicat premium

thx for help :)

P.S.: sry if there is another post for what i asked. i searched and didn't find them

---

### Post by linux_tech on 2009-01-20
to install java-
```
sudo apt-get install sun-java6-JDK
```

---

### Post by anewguy on 2009-01-20
I'm not at my Linux box right now to check, but I think MySql should be available via the synaptic package manager.  If you don't have access to that (e.g., you are running a server with no GUI) try:

sudo apt-get build-dep MySql

Sudo apt-get install MySql

Please note that were I have "MySql" you will need the full name of the product.

You may also want to install webmin on the server and then access your server via the web browser, where you can go to software and install MySql as well as any other package.

Dave :)

---

### Post by Sarmacid on 2009-01-20
Go to System -> Administration -> Synaptic package manager, there you can search for the software you need, or in a console
```
sudo apt-get install mysql-client mysql-server
```To install both client and server.

---


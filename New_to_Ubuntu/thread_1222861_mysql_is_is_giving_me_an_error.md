---
title: "mysql is is giving me an error"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by jain1 on 2009-07-25
im new to ubuntu .........n i lately installed mysql-client 5.0 
the installation went prefectly well .......but once i type mysql on the terminal i enter into mysql command
[FONT="Georgia"]mysql>[/FONT]
its all fine till here but once i enter
[FONT="Georgia"]mysql>create database emp;
[/FONT]

it showa me this error .........
[FONT="Georgia"]ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'emp'[/FONT]

pls reply ......i really want to have a learn it ......pls:confused:

---

### Post by bodhi.zazen on 2009-07-25
I can not tell for sure, but it appears as if the user you logged into mysql with does not have permission to modify the data base.

Do you know how to add users and databases to mysql ?

[http://www.scottklarr.com/topic/102/mysql-cheat-sheets/](http://www.scottklarr.com/topic/102/mysql-cheat-sheets/)

---

### Post by wojox on 2009-07-25
Try this:

```
mysql -u root -p mysql
```

---

### Post by jain1 on 2009-07-26
> **wojox said:**
> Try this:

```
mysql -u root -p mysql
```
hey......it worked well .......a lot of thanks .....
ya .....but can you pls explain wat >  mysql -u root -p mysql
this comand ment pls!!!!!!!

---

### Post by jain1 on 2009-07-26
> **bodhi.zazen said:**
> I can not tell for sure, but it appears as if the user you logged into mysql with does not have permission to modify the data base.

Do you know how to add users and databases to mysql ?

[http://www.scottklarr.com/topic/102/mysql-cheat-sheets/](http://www.scottklarr.com/topic/102/mysql-cheat-sheets/)
hey ........ur link those not work........but anyways thanks for the help

---

### Post by credobyte on 2009-07-26
> **jain1 said:**
> hey......it worked well .......a lot of thanks .....
ya .....but can you pls explain wat this comand ment pls!!!!!!!

Authenticated you as root ( MySQL administrator account ).

---

### Post by jain1 on 2009-07-26
hey guys this thread is solved so how am suppose to mark this thread as solved????:)

---


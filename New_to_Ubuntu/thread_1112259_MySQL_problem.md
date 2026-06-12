---
title: "MySQL problem"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by OMRebel on 2009-03-31
I have a a problem.  Somehow all of my MySQL users are gone (not even a root account exists).  I'm not sure what to do.  I figured out that my users were gone whenever I did the following:

mysql> UPDATE mysql.user SET Password=PASSWORD('mypassword')
    -> WHERE User='root';
Query OK, 0 rows affected (0.02 sec)
Rows matched: 0  Changed: 0  Warnings: 0

This isn't a good sign at all.  Whenever I tried to create an account, I get:

CREATE USER 'root'@'localhost' IDENTIFIED BY 'password';
ERROR 1290 (HY000): The MySQL server is running with the --skip-grant-tables option so it cannot execute this statement

Any suggestions would be great!  I have some rather large databases, so I don't want to have to remove MySQL and reinstall it.  

Thanks!

---

### Post by unutbu on 2009-03-31
```
sudo /etc/init.d/mysql stop
sudo mysqld --skip-grant-tables &
mysql
mysql> use mysql;
mysql> INSERT INTO user VALUES ('localhost','root',password('**newpassword**'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
mysql> INSERT INTO user VALUES ('127.0.0.1','root',password('**newpassword**'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
mysql> flush privileges;
mysql> quit
sudo killall mysqld
sudo /etc/init.d/mysql start

```
Change newpassword as appropriate.

---

### Post by OMRebel on 2009-03-31
Thanks for the quick response. This is what I get at the end:

brad@Linux-Test:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
brad@Linux-Test:~$ ERROR 1045 (28000): Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)

---

### Post by unutbu on 2009-03-31
On further reflection, it seems this might be the easiest way to fix your problem:
```

sudo apt-get --reinstall install mysql-server-5.0
```

I believe this will set up the root and debian-sys-maint users for you. You will be prompted for root's password. I doubt it would delete your databases in /var/lib/mysql, but it would be wise to back them up first anyway.

Below, I believe, is the manual way to achieve the same thing:

Type
```
sudo cat /etc/mysql/debian.cnf

```
Look for the password listed there

Next, check to make sure you have (or don't have) a debian-sys-maint user:

```
mysql -u root -p
mysql> select * from user where user='debian-sys-maint' \G

```
If you have a debian-sys-maint user, and if you think its password is wrong,
you can 

```
mysql> use mysql;
mysql> update user set Password='newpassword' where user='debian-sys-maint';
```

Change newpassword to the password listed in /etc/mysql/debian.cnf

If you have no debian-sys-maint user,

```
sudo /etc/init.d/mysql stop
sudo mysqld --skip-grant-tables &
mysql
mysql> use mysql;
mysql> INSERT INTO user VALUES ('localhost','debian-sys-main','newpassword','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','N','N','N','N','N','','','','',0,0,0,0);
mysql> flush privileges;
mysql> quit
sudo killall mysqld
sudo /etc/init.d/mysql start
```


Note that here we use 'newpassword' and not "password('newpassword')" because the password you see in /etc/mysql/debian.cnf is already encrypted.

---

### Post by OMRebel on 2009-03-31
Thank you so much for your help on this!

---


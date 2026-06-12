---
title: "MySQL is not operating properly"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by geek_of_doom on 2009-06-12
I have previously installed Apache 2.2.8 and PHP 5 on my machine. It is working perfectly.

I have decided to move on to MySQL, so, per instructions I found:

```
$ sudo apt-get install mysql-server
```The installation worked fine.

```
$ sudo apt-get install php5-mysql
```One again, the installation went smoothly.

However, MySQL has since given me grief.

```
$ mysqladmin create database_name
mysqladmin: CREATE DATABASE failed; error: 'Access denied for user ''@'localhost' to database 'database_name''
```I have tried adding a password, but no avail:

```
$ mysqladmin -u root password abc123
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
```

Am I missing something?

---

### Post by nandemonai on 2009-06-12
```
mysqladmin --user=root --password create test
```

--password means it will ask for a password, this is preferred as the password wont be displayed on the command line. 

'test' here being the database to be created.

If in doubt:

```
man mysqladmin
```

---

### Post by cariboo on 2009-06-12
You have to use the password that you created when you installed mysql. IF you forgot, or didn't setup a password during installation, you can run:

```
dpkg-reconfigure mysql-server-5.0
```

then once you have created the password you can access the mysql console by typing at the prompt:

```
mysql -u <username> -p
```

You will be asked to enter your password, it will not be echoed back to you.

---


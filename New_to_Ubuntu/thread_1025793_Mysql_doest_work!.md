---
title: "Mysql doest work!"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by sudeepk on 2008-12-30
I have installed Mysql server 5 and a mysql query browser.
When i try to access database from query browser by using the server hostname as localhost, it is giving me this error "could not connect to host 'localhost' Mysql error nr 1045 Access denied for user root@localhost"
please help me out.

---

### Post by cariboo on 2008-12-30
The first thing to check is to see if mysql is running. To do this open a Applications-->Accessories-->Terminal and type:

```
ps ax | grep mysql
```

if mysql is running you shlould get a result like this:

```
ps ax | grep mysql
 4486 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 4528 ?        Sl    22:53 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 4530 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
26021 pts/1    R+     0:00 grep mysql
```

If you get the above result, the next thing to do is to see if you can access the mysql console. In the same terminal type:

```
mysql -u root -p
```

enter the password you setup when you installed mysql, you should then have something like this on your screen:

```
mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9762
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>
```

If you get the above result then mysql is running. There must be a problem with the way you are trying to access the database.

Jim

---


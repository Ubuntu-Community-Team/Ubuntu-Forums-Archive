---
title: "How to set up MySQL for Bibus"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by annamoo on 2009-05-20
Hello.  I have installed Bibus with all the necessary mysql bits.  When it comes to set up it is asking for my password and various ports etc. - I have tried putting in my normal username and password to no avail.

What should I be telling it in the setup?

And what is MySQL anyway?

Thanks.

---

### Post by cariboo on 2009-05-20
Mysql is a database. Did you install mysql-server-5.0, if you did, use the password it asked you to set during installation. THe user is root, although the only program root has any permission for is mysql. To check if you have mysql-server installed correctly open an Applications-->Accessories-->Terminal and type:

```
mysql -u root -p
```

the program will ask you for the password you setup during installation. if everything was installed properly you should get something that looks like this:

```
 mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 33
Server version: 5.0.75-0ubuntu10 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>
```

use \q to quit.

---

### Post by annamoo on 2009-05-21
Thank you - I checked that and I have it installed correctly.

Should I create a new user/database for the Bibus application or just use root and "MySQL"/"information schema"?

---

### Post by porchrat on 2009-05-21
> **annamoo said:**
> Thank you - I checked that and I have it installed correctly.

Should I create a new user/database for the Bibus application or just use root and "MySQL"/"information schema"?

You probably need to use the mysql username and password there, not your linux username and password. The default port for MySQL servers is 3306, and unless you have altered the MySQL config file that shouldn't have changed.

I would imagine that you would need to create a separate database for Bibus to run against, as to the schema required well that is up to Bibus.

You can also setup a new user if you so desire, it is a good practice to not let everything run through root. You can learn how to setup a new user by reading the MySQL manual on the Sun website [here]("http://dev.mysql.com/doc/refman/5.1/en/adding-users.html").

EDIT: I did some looking around and it looks like Bibus actually contains a .sql file that creates the schema for you. You can find info on where it might be stored on this page [here]("https://wiki.kubuntu.org/Bibus").

Basically that page says: "create eg. bibus table and bibus user * create bibus db schema (table structure) by executing part of /usr/share/bibus/db_models/mysql_41.sql "

So there you have it, there should be a .sql file contained in /usr/share/bibus/db_models/mysql_41.sql (although that install guide is a little outdated so by now it is probably has a filename that is something like: /usr/share/bibus/db_models/mysql_50.sql or /usr/share/bibus/db_models/mysql_51.sql)

.sql files are basically written in a language called SQL (A language that MySQL uses) and if you run that file inside MySQL it will create tables for you.

---


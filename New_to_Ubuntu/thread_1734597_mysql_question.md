---
title: "mysql question"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by naved ..... on 2011-04-20
hii..
i have a question after installing mysql database where to perform coding for mysql in the terminal or we get a client version to perform the coding ??

---

### Post by r-senior on 2011-04-20
I usually use a combination of MySQL Query Browser and MySQL Administrator as GUI tools for working with MySQL. Both are in the repositories and installable from Synaptic, etc.

---

### Post by leg on 2011-04-20
If you have just installed mysql you start mysqld to have the server running & you can interact in cmd environment by using the mysqlclient or mysql apps. Both of these require that you can use them properly. If you want a more graphical environment you could try phpmyadmin which will give you a web based app to administer the database server and databases it contains. There is also an app called mysql workbench for managing the dbs but I am unsure where you can get that.

---

### Post by naved ..... on 2011-04-20
cant we use terminal to perform all the dbms quaries ??

---

### Post by cavh on 2011-04-20
Start with the tutorial:
[http://dev.mysql.com/doc/refman/5.1/en/tutorial.html]("http://dev.mysql.com/doc/refman/5.1/en/tutorial.html")

---

### Post by LOIREE on 2011-04-20
Why not try [http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php) ?

---

### Post by SeijiSensei on 2011-04-20
> **naved ..... said:**
> cant we use terminal to perform all the dbms quaries ??

Yes, you can use the mysql client and type your SQL queries directly at its prompt.

```
mysql -u username -p dbname
```

You'll be prompted for your password.  Omit the "-p" switch if username doesn't have a password.

Make sure mysql-client is installed as well as mysql-server.

---

### Post by dwasifar on 2011-04-20
If you want to query mysql directly from the linux command line, the syntax is:

mysql -u[username] -p[password] [dbname] -e "query text"

So for a simple example, to select from table "users" in a database called "mailusers", where the mysql user and password are "bob" and "pw123":

```
mysql -ubob -ppw123 mailusers -e "select * from users"
```

A semicolon is not necessary at the end of the query when doing it this way.

---


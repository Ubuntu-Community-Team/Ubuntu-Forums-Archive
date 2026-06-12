---
title: "[SOLVED] how to dump mysql database"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by my_everything78 on 2008-12-23
Hello everyone 

Can any body tell me how to dump data base to have a back up and then how to restore it ?

Thank you for your help :)

---

### Post by roelpeeters on 2008-12-23
You can do a google on mysqldump. Otherwise it is enough to copy the data files.

Restore you can do with the mysql command, reading the dump that was made with mysqldump.

---

### Post by jordanmthomas on 2008-12-23
For example:
```
mysqldump -u root -p DATABASENAME > DATABASENAME.sql
```
will dump and then 
```
mysql -u root -p SOMEDATABASENAME < DATABASENAME.sql
```
will restore it to a database called SOMEDATABASENAME

Hope this helps, if not maybe this will help you.
[http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html](http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html)

---

### Post by wieman01 on 2008-12-23
Simplest way to achieve that:

You can use mysqldump to create a simple backup of your database using the following syntax.

    > mysqldump -u [username] -p [password] [databasename] > [backupfile.sql]

          o [username] - this is your database username
          o [password] - this is the password for your database
          o [databasename] - the name of your database
          o [backupfile.sql] - the file to which the backup should be written.

Reference: [http://www.devshed.com/c/a/MySQL/Backing-up-and-restoring-your-MySQL-Database/]("http://www.devshed.com/c/a/MySQL/Backing-up-and-restoring-your-MySQL-Database/")

---

### Post by leg on 2008-12-23
Also try installing phpmyadmin and you can do it through that if you want to.

---

### Post by my_everything78 on 2008-12-23
Guys Thank you so much .
it is  so easy to apply :)

Best Regards

---


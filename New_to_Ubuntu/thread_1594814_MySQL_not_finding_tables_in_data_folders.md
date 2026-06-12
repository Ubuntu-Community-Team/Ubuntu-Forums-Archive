---
title: "MySQL not finding tables in data folders"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by revdocjohn on 2010-10-12
I've recently installed Ubuntu on a i386 notebook.

I have installed LAMP which went without a hitch and everything checks out.  

I have moved the folders containing my MySQL data into /var/lib/mysql/.  When I run MySQL (from the console as well as with phpMyAdmin) I can see the folders (that is, I can "use" them), but I can't find the tables  that are part of the database, in spite of the fact that the folders show them as present.  This renders the databases inaccessible and me frustrated.

phpMyAdmin shows the databases, but doesn't show the number of tables in parentheses as it does for the databases mysql and phpmyadmin.  In the MySQL console a "show tables" command yields this error message: "ERROR 1018 (HY000): Can't read dir of './databasename/' (errno: 13)"

Any suggestions?

Ubuntu 10.04LTS
MySQL 5.1.41-3ubuntu12.6

---

### Post by cmnorton on 2010-10-12
Just putting the data folder in place does not complete the task. You have to do a mysql import command.

---

### Post by revdocjohn on 2010-10-12
I thought so.  

The trouble is, what I have is the actual MySQL data files.  What the import program expects is a text file of some sort (CSV, SQL, etc.), but without being able to read the MySQL data files, I can't generate a text file.  But if I could read the MySQL files, I wouldn't need to generate a text file.  (They call this Catch-22.)

---

### Post by misafir2010 on 2010-12-20
Alt + F2:[FONT=monospace]
[/FONT]```
[FONT=monospace]gksu nautilus /var/lib/mysql
```[/FONT]

---


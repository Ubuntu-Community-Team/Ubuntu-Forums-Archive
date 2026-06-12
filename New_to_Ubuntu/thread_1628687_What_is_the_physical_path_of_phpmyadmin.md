---
title: "What is the physical path of phpmyadmin ?"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by nprahul on 2010-11-23
I installed phpmyadmin using the pre provided packages in ubuntu and to introduce myself i am a beginner user just shifted from Windows 7 

i am a php application developer and all my files currently are in xampp phpmyadmin

is there a way to mass import all those databases directly to ubuntu ?

i know that in phpmyadmin there is a data folder which has the physical files for our databases.

Any help would be greatly appreciated.

Thanks

Rahul Agrawal
Application Programmer
PHP/ASP.NET
[www.rahulagrawal.co.uk]("http://www.rahulagrawal.co.uk")

---

### Post by karlwbloedorn on 2010-11-23
I'm guessing that you are using a particular type of SQL server (MySQL, PostgreSQL, etc) Which is it?

As far as i'm aware, phpmyadmin only connects to your database server. (it doesn't store any of the data). It is meant to be a web GUI to SQL. Your databases should be stored in the SQL server.

---

### Post by yankysunny on 2010-11-23
In windows 7, backup the whole database and restore in ubuntu through command line. just same as u do in windows through command line.I am assuming that the database is MySQL

---

### Post by stmiller on 2010-11-23
Yep. You can import databases from command line, or with phpmyadmin.

If you installed it with apt-get, it is located at:

[http://yourserver/phpmyadmin](http://yourserver/phpmyadmin)

---


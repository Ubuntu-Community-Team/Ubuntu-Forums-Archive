---
title: "Remote Access of SQL in Ubuntu server 10.10"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by erloumervie on 2011-01-23
Anybody can help..

I installed ubuntu server 10.10 and joomla 1.5.22 and was successfully done.. My problem is how to update my sql in ubuntu server 10.10 because I want to upload my new sql in ubuntu server...

Thanks

erloumervie

---

### Post by erloumervie on 2011-01-23
How to remotely access my sql of ubuntu server 10.10? I want to update my sql sever 
in ubuntu.

Thank you..

Erloumervie

---

### Post by erloumervie on 2011-01-23
How to access remotely my SQL in ubuntu server. I want to upload new SQL datas to my 
ubuntu server sql. Please help...

Thank you..

Erloumervie

---

### Post by SeijiSensei on 2011-01-23
What SQL server are you running?  On what platform?  Is it available over the network?  

If you want to replicate an existing database, see if your database software allows you to make a textual "dump" of the data.  If you're running PostgreSQL or MySQL you can use the pg_dump or mysqldump utilities for this task.

If the database resides on a Windows server running Microsoft SQL Server, you might look into using Microsoft Access and the appropriate ODBC connectors to copy data from MS SQL to Ubuntu.

If you simply want to leave your data on the current server, but access it remotely from a Ubuntu host, you'll need to install a compatible client on the Ubuntu host or use ODBC tools.  For instance, if you have a server running MySQL, you can connect to it over the network with the "[mysql]("http://packages.ubuntu.com/maverick/mysql-client-5.1")" client program from the Ubuntu machine.

---

### Post by James78 on 2011-01-23
If you're using MySQL you can use phpMyAdmin to do it with an easy web interface.

---

### Post by erloumervie on 2011-01-23
Hello ubuntu users,

How to remotely access my sql in Ubuntu server 10.10..Anybody can help me..

Thanks

---

### Post by cariboo on 2011-01-23
Please don't create multiple threads on the same subject, I have merged your 4 threads, please report the post you want deleted.

---


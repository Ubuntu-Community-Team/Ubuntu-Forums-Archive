---
title: "Accessing A local SQL file"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2010-07-26
Having googled for hours I turn to you guys.
As the most intelegent people I know I have complete faith that you can answer my question.
I have an sql file on my hard drive. 1.5gb. Nothing will open it.
I've tried finding a converter but they insist on connectiong to the server. The server is no longer running all I have is the SQL file. 
Access format would be nice but anything I can play with is acceptable as long as I can access the data.
A linux or windows solution would be fine. I have XP, win7 and ubuntu9.10 
Can I also point out that I know very little about sql I was given the file to open.

---

### Post by tarps87 on 2010-07-26
Do you know what the SQL server was?

---

### Post by martygavin on 2010-07-26
first, scan ur reg. to ensure that it is intact and not corrupt. the file can be opened with several proggies, ie, notepad, mysql, and numerous other free proggies... just ensure that ur reg. is not corrupt first.

---

### Post by surfer on 2010-07-26
is it a text file with the sql commands in it? or a binary file? could you post the first few lines (if it's a text file)? what does the 'file' command think your file is?

---

### Post by bigmonmulgrew on 2010-07-26
I'm not entirely sure. SaaS has been mentioned. I'm not entirely sure what that is.
> **tarps87 said:**
> Do you know what the SQL server was?

---

### Post by bigmonmulgrew on 2010-07-26
Reg is fine. Note pag wont open it it.  Too big. Same for workpad and even Word. Open office writer just hangs.
> **martygavin said:**
> first, scan ur reg. to ensure that it is intact and not corrupt. the file can be opened with several proggies, ie, notepad, mysql, and numerous other free proggies... just ensure that ur reg. is not corrupt first.

---

### Post by bigmonmulgrew on 2010-07-26
By "file" command are you reffering to the linux command line? I'm not massively familiar with that.
I cant post the first few lines as its so large text editors wont open it.

> **surfer said:**
> is it a text file with the sql commands in it? or a binary file? could you post the first few lines (if it's a text file)? what does the 'file' command think your file is?

---

### Post by tarps87 on 2010-07-26
Try
```
tail ***pathToFile***
```

---

### Post by aeiah on 2010-07-26
im guessing this is a mysql dump file. if this is the case, you should be able to put it into a new mysql server and browse it with, say, phpmyadmin or something

---

### Post by bigmonmulgrew on 2010-07-26
Please excuse my ignorance. I believe that it is a dump file. How do I setup a mySQL server.
> **aeiah said:**
> im guessing this is a mysql dump file. if this is the case, you should be able to put it into a new mysql server and browse it with, say, phpmyadmin or something

---

### Post by WRDN on 2010-07-26
> **bigmonmulgrew said:**
> Please excuse my ignorance. I believe that it is a dump file. How do I setup a mySQL server.

It sounds like it may be a dump file i.e. database backup file.

You need to load it into the MySQL engine, which can then manipulate the databases that were created from the backup.

First, install MySQL server:

```
sudo apt-get install mysql-server
```

You will be asked to enter a password to login with.

At this point, you should be able to login to your mysql server:

```
mysql -u [username] -p
```

At first, you will need to replace [username] with root (the initial MySQL user). "-p" makes MySQL request a password from you (required to login) - type the same password you entered during installation.

Now MySQL is working, exit from it, and type:

```
mysql -u [username] -p < myfile.sql
```

Note this will only work if the dump file contains instructions to create the databases.
If it does not, you will need to login to MySQL, create the databases and then run the above command.

If you want to restore a particular database, you can type:

```
mysql -u [username] -p database_name < myfile.sql
```

---

### Post by bigmonmulgrew on 2010-07-26
Thanks for your help

I get this error message

```
ERROR 1046 (3D000) at line 22: No database selected
```

---


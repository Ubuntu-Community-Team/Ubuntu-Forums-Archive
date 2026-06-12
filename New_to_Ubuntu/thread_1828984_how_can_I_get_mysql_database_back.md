---
title: "how can I get mysql database back?"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by 007casper on 2011-08-20
I have the information_schema, and sitedatabase, I would like to get mysql back.  How do I do it?
```

+--------------------+
| Database           |
+--------------------+
| information_schema |
| sitedatabase       |
| mysql              |
+--------------------+
I need mysql.sql

```
by mistake I deleted the mysql database that have user information, and other useful information regarding the database.  I can still log in as root to the database, however, all the other users and their privileges got deleted.  

I did 'aptitude install mysql'  however, that didnt install mysql.sql database.

---

### Post by karlson on 2011-08-20
> **007casper said:**
> I have the information_schema, and sitedatabase, I would like to get mysql back.  How do I do it?
```

+--------------------+
| Database           |
+--------------------+
| information_schema |
| sitedatabase       |
| mysql              |
+--------------------+
I need mysql

```
by mistake I deleted the mysql database that have user information, and other useful information regarding the database.  I can still log in as root in the database, however, all the other users and their privileges got deleted.  

I did 'aptitude install mysql'  however, that didnt install mysql database.

mysql_install_db should create it, but unless you have the backup of the database you may be out of luck with restoring the privileges.

---

### Post by 007casper on 2011-08-20
thank you.  I couldnt really find anything on the net about recreating mysql.sql.  I just reinstalled it.

I am going to reinstate all users.

---


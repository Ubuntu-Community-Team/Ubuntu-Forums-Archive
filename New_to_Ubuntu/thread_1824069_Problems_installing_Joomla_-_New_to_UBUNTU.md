---
title: "Problems installing Joomla - New to UBUNTU"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by dobromir.mitkov on 2011-08-13
Hi I have this problem, installing joomla: I can't Find MySQL, and I cant Configure my Password and User name, because of this, my joomla instalation won't procede. As an user guide I use the Joomla instalation guide on ubuntu. 

**ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)**

I am an absolute novice in UBuntu, so treat me kindly please. :)

---

### Post by HalfEmptyHero on 2011-08-13
How did you install apache/php/mysql? The default username for mysql is root and there is no default password. Try using those settings.

---

### Post by dobromir.mitkov on 2011-08-13
Thank You I did it. It seems I didn't know, that 'root' is the user name. 

I said I am a nivice , didn't I? :P 

Thank you again, Joomla is already running.

> **HalfEmptyHero said:**
> How did you install apache/php/mysql? The default username for mysql is root and there is no default password. Try using those settings.

---

### Post by HalfEmptyHero on 2011-08-13
Glad I could help. If you want to secure mysql more, I suggest you run the following in the terminal.

sudo mysql_secure_installation

---

### Post by dobromir.mitkov on 2011-08-13
All done!  If you've completed all of the above steps, your MySQL
installation should now be secure.

Thank you Again. Now everything should be ok. 

Have a nice holiday! :D

> **HalfEmptyHero said:**
> Glad I could help. If you want to secure mysql more, I suggest you run the following in the terminal.

sudo mysql_secure_installation

---


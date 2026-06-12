---
title: "Resetting mysql-server root password"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by mevets on 2010-04-16
I install apache2 php5 mysql-server and phpmyadmin using apt. When I try to login to phpmyadmin it tells me the password for root is not correct.

I tried purging all those packages then installing again but I am not prompted to set a mysql-server password upon install. Also phpmyadmin cannot purge because it cant drop the tables in mysql cause I have the wrong password.

What can I do about this?

---

### Post by Jon Monreal on 2010-04-17
I believe you could just use
[FONT=monospace]```
[/FONT]sudo dpkg-reconfigure mysql-server-YOURVERSION
```
replacing YOURVERSION, of course.

---


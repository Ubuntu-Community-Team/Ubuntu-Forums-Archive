---
title: "problem in running mysql"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by sijran on 2010-08-15
when i run mysql - u root -p it runs but when i creeate database using CREATE DATABASE mydatabase it gives error as cannot find CREATE command. Also mysql prompt is not coming on command prompt.

---

### Post by DaithiF on 2010-08-15
Hi,
if you're not getting to a mysql prompt then you haven't actually logged in successfully.  that would also explain the message about not finding the CREATE command, you're presumably entering that into your shell rather than mysql.

have you a mysql root password set, and are you entering it when prompted after you enter mysql -u root -p

---


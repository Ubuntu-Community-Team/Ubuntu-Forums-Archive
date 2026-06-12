---
title: "mysqladmin -u root password"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by tryinghard on 2010-04-01
I'm install mysql with apt-get install mysql-server mysql-cliebt5.1 on my ubuntu 9.10
to ser the root password I enter mysqladmin -u root password 
I get ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
I can't find an answer anywhere. please help!

---

### Post by new_tolinux on 2010-04-02
As I can not change the password of my MySQL server currently, I tried this:
```
mysqladmin -u root -p password
```
Which does ask me for a password (-p) but does not accept the "password" command with this error:
```
mysqladmin: Too few arguments to change password
```
Therefore I guess this would be the correct command:
```
mysqladmin -u root -p password yournewpassword
```

---

### Post by The Cog on 2010-04-03
I don't think mysql will accept the password on the command line. You launch it with 
> mysql -u root -p
and then supply the password when prompted. The -p tells it to prompt for a password, not that a password follows.

---

### Post by new_tolinux on 2010-04-03
```
mysqladmin -u root -p password yournewpassword
```
In this piece of code the "password" isn't "password". "password" is the command to change the password to "yournewpassword".
-p does make mysql ask for the password which you have to type then.

---


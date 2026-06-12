---
title: "can't get Mysql working"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by carrarin on 2010-05-19
Hello everyone,

Last year I installed mysql on my system and putzed around with it. I think I changed some configuration files without knowing what I was doing. Anyways, for some reason I can't log on as user or root. 

If I could log on as root i think I could fix the problem. 

The exact error message that I get is this:

```
carrarin@netbook:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
carrarin@netbook:~$ 

```

I dont think I changed roots password, but I dont really remember.

---

### Post by wojox on 2010-05-19
It didn't even ask for your password? Try:

```
mysql -u root -p
```

---

### Post by carrarin on 2010-05-19
```
carrarin@netbook:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
carrarin@netbook:~$ 
```

Isn't the default root password nothing?

---

### Post by blue_print on 2010-05-19
MySQL root password is different from the root password. You can get this password from the file /roo/.my.cnf.  If this file not present, you can reset the password as per the info available in the link [http://www.howtoforge.com/reset-forgotten-mysql-root-password](http://www.howtoforge.com/reset-forgotten-mysql-root-password)

---

### Post by wojox on 2010-05-19
> **carrarin said:**
> ```
carrarin@netbook:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
carrarin@netbook:~$ 
```

Isn't the default root password nothing?

No you should have been prompted to set a password when you installed it. blue_print's link should work for you to reset the root password. :)

---

### Post by carrarin on 2010-05-20
I try to start the mysql daemon in safe mode, like the instructions say, and it seems to hang.

Here,


```
root@netbook:/home/carrarin# mysqld_safe --skip-grant-tables
100520 13:43:24 mysqld_safe Logging to '/var/lib/mysql/netbook.err'.
100520 13:43:24 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
```

This is all that appears on the screen. I dont get the mysql prompt. Why? 

Also, the instructions here:
[http://www.howtoforge.com/reset-forgotten-mysql-root-password](http://www.howtoforge.com/reset-forgotten-mysql-root-password)
said that if this doesn't work, I got bigger problems.

---

### Post by carrarin on 2010-05-20
I fixed it, I remember what my password was... Thanx anyways

---


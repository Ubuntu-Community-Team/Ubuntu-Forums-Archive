---
title: "MySQL problem"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by poisonmushroom on 2007-10-18
Yesterday i installed LAMP on my new linux box (ubuntu server edition) and tried putting an HTML file in /var/www to see if it worked and it did.

But then i shut it down, and today i started it and tried connecting using a browser but it didnt work so i did some checking with help from a friend (the error is:ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2))

I tried searching google but the solutions did not help, and some were too difficult for me to understand.

I went to /var/run/mysql, did the ls command and saw nothing, then i searched /var/lib/mysql and did not find any file called mysql.sock

What happened to this file? did it disappear?

Thank you.

---

### Post by tkharris on 2007-10-18
You might want to try something like:

```

/etc/init.d/mysql start
Or:
/etc/init.d/mysqld start

Or:
/etc/init.d/mysqld-safe start

```

---

### Post by poisonmushroom on 2007-10-18
thanks for the reply tkharris,

I used the command /etc/init.d/mysql start 
and got this message:
 * Starting MySQL database server mysqld                                 [fail]

Why did it fail?

---

### Post by tkharris on 2007-10-18
I have no idea why it failed.

You might want to look in /var/log/mysql.err though ;)

---

### Post by poisonmushroom on 2007-10-18
mysql.err and mysql.log files in /var/log are empty... this is weird :P

---

### Post by techknow on 2007-10-20
*bump*
I am having the same problem, any ideas anyone?

---


---
title: "Apache2 and PHP5 ?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by alket on 2009-04-14
I installed Apache2 and PHP5, but when i load a PHP file from loaclhost firefox doesn't recognize it

---

### Post by Iowan on 2009-04-14
What do you mean by "doesn't recognize it"? Does it try to download it, or does it generate another error message?
Check the **Troubleshooting PHP5** section in [this]("https://help.ubuntu.com/community/ApacheMySQLPHP") help page.

---

### Post by alket on 2009-04-15
it tries to download.

---

### Post by Arndt on 2009-04-15
> **babaroga said:**
> it tries to download.

Did you change the apache2.conf file? In my /etc/apache2/apache2.conf, I added the line

```
AddType application/x-httpd-php .php
```

---

### Post by CryptiniteDemon on 2009-04-15
trying opening it as localhost/filename.php  instead of file:///var/www/filename.php in the web browser.  

You're requesting files from your machine instead of actually requesting it through a port over tcp, which means apache won't be used & the php file won't be sent through the php processor.

---

### Post by alket on 2009-04-15
i run it from localhost, but i played a little bit with apache.conf file now it is not working.

---

### Post by freak42 on 2009-04-15
try one of the tutorials to get it installed correctly:

[http://www.google.ch/search?q=apache+php+ubuntu+8.10](http://www.google.ch/search?q=apache+php+ubuntu+8.10)

---


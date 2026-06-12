---
title: "Apache access.log file empty"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by borobudur on 2008-10-01
Hi, my Apache access.log file is empty. I was assuming that it could be a permission problem:
```
-rw-r-----  1 root adm        0 2008-08-17 06:53 access.log
```I found one apache process running under *apache* and several under *www-data*. 

I was hoping with changing the file owner to *www-data:adm* it would work but after a restart of apache I still have an empty access file. 

The error.log file is working fine (with the root owner) but I don't see any entry of problems writing on access.log.

Has anyone an idea?

---

### Post by superprash2003 on 2008-10-01
by default there shouldnt be any permissions issue.. try restarting apache and visiting the site locally [http://127.0.0.1](http://127.0.0.1) and now see.. are you looking under /var/log/apache2 ?

---

### Post by borobudur on 2008-10-01
I wrote that I restarted Apache; it's a real server machine, can't call localhost; yeap, access.log is under /var/log/apache2 (as default).

---

### Post by borobudur on 2008-10-22
*** bump ***

---


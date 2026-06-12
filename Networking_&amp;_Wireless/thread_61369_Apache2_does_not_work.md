---
title: "Apache2 does not work"
date: 2005-08-31
forum: Networking &amp; Wireless
---

### Post by ounas on 2005-08-31
On installing Apache2 all worked well for a while, now I get the following error.

"The connection was refused when attempting to connect to localhost"

On removing Apache2 and installing Apache 1, all works well 
Also now php fails in Apache 1.

Any ideas, what maybe wrong, Newbie here

Ounas :???:

---

### Post by ounas on 2005-08-31
Also get the following message on the console.

(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down


-Ounas ](*,)

---

### Post by DJ_Max on 2005-08-31
Normally that means port 80 is currently being used. PHP will fail if you were using the PHP4/Apache 2 package. Then you removed Apache2, which should have removed PHP4/Apache2

---

### Post by ounas on 2005-08-31
Found that I can login to Webmin using the normal

"https://?.?.com:10000/"

-Ounas :?  :?

---

### Post by DJ_Max on 2005-08-31
[QUOTE=ounas]Found that I can login to Webmin using the normal

"https://?.?.com:10000/"

-Ounas :?  :?[/QUOTE]
 Webmin has nothing to do with Apache, because it uses different ports, and webmin has it's own HTTPD.

Run ```
ps aux
```. Tell me if you see Apache running.

---

### Post by ounas on 2005-08-31
Removed Apache2 and Php4 with Synaptic, reinstalled Apache 1.1 and Php3.
Apache web server works, but cannot load .php files. Wants to load with Gedit or download

-Thanks DJ

-Ounas :???:  but getting clearer slowly

---

### Post by ounas on 2005-08-31
Yes Apache is running

-Ounas

---

### Post by DJ_Max on 2005-08-31
I wouldn't use PHP3. If you were using PHP4, I would tell you to install libapache-mod-php4. I don't see the like for PHP3.

---

### Post by ounas on 2005-08-31
Removed php4 and installed php3.


This php file does not load: testphp.php

<?php phpinfo(); ?>



-Ounas :???:

---

### Post by DJ_Max on 2005-08-31
Take a look here, this problem has been addressed several times.
[http://ubuntuforums.org/showthread.php?t=41687](http://ubuntuforums.org/showthread.php?t=41687)

---


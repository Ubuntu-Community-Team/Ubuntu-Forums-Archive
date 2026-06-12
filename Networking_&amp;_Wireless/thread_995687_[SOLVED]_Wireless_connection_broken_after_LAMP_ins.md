---
title: "[SOLVED] Wireless connection broken after LAMP install"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by UltimateNewbie on 2008-11-28
Hi, 

maby I miss posted [this]("http://ubuntuforums.org/showthread.php?p=6266871#post6266871") tread?

---

### Post by UltimateNewbie on 2008-11-28
**Repost:**

Hi,

I just installed Ubuntu for the first time, the reason is I want to learn PHP and MySQL to make groovie sites.  :smile:

But, after installing Apache, PHP, MySQL and phpMyAdmin using this guide:
[http://ubuntuexperiment.wordpress.co...che-php-mysql/]("http://ubuntuexperiment.wordpress.com/2008/11/10/installing-apache-php-mysql/")

I lost my wireless connection. Well, not straight away. Used some time to figure out how to make the file *fqdn *with content “*ServerName localhost*” into [I]/etc/apache2/conf.d
[/I]
It seems to me that connection got broken after adding fqdn file and rebooting. Anyone had the same trouble or know the solution, I'd be most grateful!

Thanks

---

### Post by UltimateNewbie on 2008-11-28
**Repost:**

Feel like updating the post a little:

The installation of Apache, PHP, mySQL and phpMyAdmin happened right after installing Ubuntu 8.10.
The internet connection worked fine also after this except phpMyAdmin did not work because I couldn't work out how to create the file *fqdn*. But wireless connection worked fine. I turned of the laptop.
Next day, I turned on the laptop, wireless works like a charm. And i scope the net and figure out that I can use 

*sudo su* 

in terminal to "be" root. 
From there i manage to create the file using

[I]gksu gedit /etc/apache2/conf.d/fqdn

tested that it worked to type [/I][http://localhost/randomfile.php](http://localhost/randomfile.php) [I]and turned of the machine. 
Next time i turned it back on.... BAM!! ..... connection gone. :P

Just keeps asking me for a WPA WPA2 passkey. The one Ive typed a hundred times is the right one, but keeps aksing me for the key as if the one I typed was wrong.

Help... Anybody... Hello... :P

Thanks[/I]

---

### Post by cariboo on 2008-11-28
Can you temporarily setup your wireless connection so that you don't need wpa just to see if you can connect?

Jim

---

### Post by UltimateNewbie on 2008-11-28
No, sorry.

The router is in my landlords house, and they're not home for a couple of months. 

Sry.

---

### Post by UltimateNewbie on 2008-11-29
Sorry for this one. Turned out it was fault by router. Managed to fix the problem. 

Thanks for your reply!

---


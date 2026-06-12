---
title: "Java not working Namaroka (Firefox 3.6)"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by newbie1029 on 2010-01-23
Anybody else experience?  Is there a fix? Thanks.

---

### Post by NCLI on 2010-01-23
You're better off using 3.5 for now, but if you really feel the need to do this, please post how you installed 3.6

---

### Post by moted on 2010-01-24
I've also run into the same problem and cannot seem to get it to work.  The plugin is detected by Firefox and is enabled, however java applets don't function.

---

### Post by the.phantom on 2010-01-25
i don't know how you upgraded?
i used ubuntuzilla's way ( and have for years)
using 3.6 firefox and latest t-bird his way

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

how to do ( i am a lightweight and works fine)

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)

---

### Post by LuisGMarine on 2010-01-25
Do you guys have the Java installed from the repos?  If so make sure you have the Java 6.0 Browser Plugin package installed.

Easiest way to check is open up the Ubuntu Software Center and type in Java and check if its installed.  If not install it and try the website again after restarting firefox.

---

### Post by nanotube on 2010-01-25
there's a bug in sun-java6-plugin package in karmic.

here's a quick workaround:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29)

---

### Post by moted on 2010-01-25
Unfortunately that is of no help.  The plugin is detected for me, however it just fails to properly load pages.

about:plugins:
Java(TM) Plug-in 1.6.0_18

    File name: libnpjp2.so
    The next generation Java plug-in for Mozilla browsers.


The same plugin works fine in 3.5

---


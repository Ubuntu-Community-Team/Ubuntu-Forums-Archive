---
title: "Backuppc Question"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by fearevilleet on 2007-12-20
I am trying to install backuppc via apt-get. The install seems to go, it assign me a user name and password and tells me to access the web interface. The install does not put anything in my apache folder [var/www] so I am not sure how to access the web interface.  I tried doing dpkg-reconfigure backuppc and it says theThis module is already enabled! I also purged the package and reinstalled it.  How would I access the backupppc interface to configure it?

---

### Post by Girya on 2007-12-25
sudo chmod 777 /etc/apache2/apache2.conf
sudo cat /etc/backuppc/apache.conf >> /etc/apache2/apache2.conf
sudo chmod 644 /etc/apache2/apache2.conf
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start

I was having the same problem as you. I don't why backuppc won't auto configure apache2 but I found this in a post by searching backuppc. it was posted by bgearig. It adds the required lines to the apache config file so apache can find backuppc. 

it worked great after doing this. Kevin

---


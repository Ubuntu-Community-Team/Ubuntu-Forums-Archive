---
title: "wget not working"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by zayindaleth on 2008-01-08
Hi all,

I am having a bit of a problem with my recently built linux server.
I can't seem to do much with it -- neither wget nor apt-get seem to be working.


That is to say, I can use apt-get, but it uses the CDrom and not the online repositories to get packages from, and wget simply times out ..

I can ping out, and resolve host names, but little more ..

Where should I be looking?
I have another linux server (runnign centos) which is working just fine, and I tried copying config files from one to the other with little luck.

Any help?

---

### Post by stalker145 on 2008-01-09
> **zayindaleth said:**
> Hi all,

I am having a bit of a problem with my recently built linux server.
I can't seem to do much with it -- neither wget nor apt-get seem to be working.


That is to say, I can use apt-get, but it uses the CDrom and not the online repositories to get packages from, and wget simply times out ..

I can ping out, and resolve host names, but little more ..

Where should I be looking?
I have another linux server (runnign centos) which is working just fine, and I tried copying config files from one to the other with little luck.

Any help?

Sorry, no thoughts on the wget problem at the moment, but as for apt-get, try the following:```
sudo nano /etc/apt/sources.list
``` and comment out the CDROM line (which should be at the top). Check all of your other repository listings to make sure the ones that you want are not commented (remove the #). Save and close. 

Then ```
sudo aptitude update
```and you *should* be able to install without the CDROM error.

Try using wget, apt-get, or aptitude to grab some stuff. If it doesn't work, check back and we'll kick off the fun.

---

### Post by zayindaleth on 2008-01-09
Hi there, and thank you for your reply --

I am able to ping my repositories, and have commented the CDROM (although it was only using the CD as its main source because I had the CD still in the drive)..

I am still unable to do anything.. I can ping, but can't download any data..

---


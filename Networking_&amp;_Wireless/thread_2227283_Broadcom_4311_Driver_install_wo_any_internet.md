---
title: "Broadcom 4311 Driver install w/o any internet"
date: 2014-06-01
forum: Networking &amp; Wireless
---

### Post by billy16 on 2014-06-01
Hi All,

I'm hoping someone can assist I've been out of the Ubuntu game for some years now and have recently decided to get my feet wet.  I installed alongside Windows 7 and am anticipating dumping 7 altogether.  I'm tired of having to do system restores every time updates are added.

Anyway, I have a Broadcom 4311 and am unable to connect to the internet in anyway whatsoever.  Even with a wired connection, I'm unable to connect which I find odd.

That being said, I'm receiving the error that the package cannot be found when I attempt to install the driver via the terminal as outlined in the Sticky.  Any help would be appreciated.  I still have internet via another laptop.  The only other off the wall thing I can think of is that I was last connected to the internet via windows and windows doesn't automatically release the IP.  However, I've restarted numerous times since then so it shouldn't be a problem to the best of my knowledge.  It really shouldn't be a problem for a wired connection.

Any help is greatly appreciated.

Dell Inspiron 1521 running Ubuntu v 14.04 and again wireless card is broadcom 4311

---

### Post by Hadaka on 2014-06-01
Hi billy16, since you have internet with another machine we can
send you the nonfree driver. Lets first take a look at a couple things
and see if it is possible to get it going as is, please COPY and paste,,
open a terminal ctrl/alt/t and do..
```
lspci -n | egrep '0200|0280' | awk '{print $3}'
lsmod | grep wl
rfkill list all | grep -i yes
```
post the output please
thanks

---

### Post by praseodym on 2014-06-01
Install the missing firmware file via software center:

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

---

### Post by chili555 on 2014-06-01
Here ya go! [http://askubuntu.com/questions/474872/help-with-network-on-ubuntu-14-04/474875#474875](http://askubuntu.com/questions/474872/help-with-network-on-ubuntu-14-04/474875#474875)

---

### Post by billy16 on 2014-06-01
Hadaka this is what I got but I'm good to go now.

awk: cannot open lsmod (No such file or directory)
grep: rfkill: No such file or directory
grep: list: No such file or directory
grep: all: No such file or directory

---

### Post by billy16 on 2014-06-01
Sorry Hadaka I jumped the gun Chili got me the post I needed and for the life of me couldn't find no matter the amount I tried.  

Thank you all so much for your help I was able to download it to a USB send it to the desktop and load via terminal with the instructions in the posts.

I'm good to go now that was driving me nuts looking.  However in retrospect it was more my stupidity as I should have searched for the non free driver download rather than searching for Linux based braodcom 4311 drivers.

Thank you all again!!!  You're Ubuntu Rock Stars!

---

### Post by Otto-C on 2014-06-01
Have a Dell Vostro 1000 laptop with bcm4311.  Have tried several of the suggestions to
activate my wireless. Will have to reinstall Ubuntu 12.04-4. Will your .deb driver work
here. Do you suppose.

tia
otto-c

---

### Post by jeremy31 on 2014-06-01
Otto-C, post results from ```
rfkill list
``````
lsmod
``` in terminal

---

### Post by Otto-C on 2014-06-02
Must postpone this project for a while, something came up. Will revisit.

---

### Post by chili555 on 2014-06-02
> **Otto-C said:**
>  Will your .deb driver work
here. Do you suppose.

tia
otto-cIt will work just fine.

---


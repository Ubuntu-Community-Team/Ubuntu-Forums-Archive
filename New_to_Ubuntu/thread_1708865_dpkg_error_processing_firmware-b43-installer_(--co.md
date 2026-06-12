---
title: "dpkg: error processing firmware-b43-installer (--configure):"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by Alif Radzi on 2011-03-17
dpkg: error processing firmware-b43-installer (--configure):

im having with the above problems..every software that i downloaded/install cant be use
please anyone can help me with this?? im new to this ubuntu world..just a few days using it

---

### Post by TechWiz2100 on 2011-03-17
try ```
sudo dpkg --configure -a
```

also keep in mind that you must be connected to the internet to use apt and more specifically use firmware-b43 unless you already have the firmware image sitting around on your computer.

---

### Post by Alif Radzi on 2011-03-17
tq btwy..however this msg pop out

Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer

---

### Post by TechWiz2100 on 2011-03-17
It seems your wireless card is not supported by B43 Firmware Cutter

Try ```
dpkg --purge -a
```
That should remove the pending package and allow you to update normally again

---

### Post by Alif Radzi on 2011-03-17
OMG..theres still probs occurs
when i want to install it

Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

p/s: do you think my laptop isn't compatible to use ubuntu? i really like it though..any other linux os would u recommend 2 me that's possibly can run efficiently in my laptop??
im using compaq presario cq40

---

### Post by bkratz on 2011-03-17
> **Alif Radzi said:**
> OMG..theres still probs occurs
when i want to install it

Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

p/s: do you think my laptop isn't compatible to use ubuntu? i really like it though..any other linux os would u recommend 2 me that's possibly can run efficiently in my laptop??
im using compaq presario cq40

Please see post 1 of this thread--look familiar!?

[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by Alif Radzi on 2011-03-18
owh my tq ^^ it's work like a charm..tq again for solving my problems

---

### Post by Alif Radzi on 2011-03-18
i got a new probs

E: Unable to locate package podcast
E: Unable to locate package client

any software that i want to download cant be downloaded?

---

### Post by TechWiz2100 on 2011-03-18
"podcast" is not a package and "client" is too generic to be the name of a program. You must type in the exact name of the package in order to install.

You can search the repos with ```
apt-cache search *
```
replacing * with whatever program you wish to install. Also searching in Applications > Ubuntu Software Center is a whole lot easier than using Apt when you don't know the exact names.

---


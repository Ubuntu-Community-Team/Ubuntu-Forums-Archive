---
title: "wireless not working ubuntu 10.04"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by nbusiness on 2010-12-24
I have Compaq Presario v6000 with wireless broadcom corporation bcm4311 802.11 b/g wlan rev 01

---

### Post by TeoBigusGeekus on 2010-12-24
Go with [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") on this one.

---

### Post by wep940 on 2010-12-24
Or the preferred way, if possible:
 
- check in System/Administration/Additional Drivers for a driver - it may have something like STA somewhere in the name. Be sure to activate any driver for wireless that shows there.
 
- or -
 
- temporarily hard-wire your PC to the router
- do:
 
sudo apt-get update
 
- now check for a driver in System/Administration/Additional Drivers
 
- you'll need to physically disconnect the hard-wire cable before trying your wireless again
 
I am an advocate of ndiswrapper/ndisgtk, but in this case they have drivers now that do work if you are able to access them.

---

### Post by nbusiness on 2010-12-24
[QUOTE=TeoBigusGeekus;10276687]Go with [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") on this one.[/QUOTE

akil@akil-laptop:~$ sudo dpkg -i ndiswrapper-common_*.deb
dpkg: error processing ndiswrapper-common_*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndiswrapper-common_*.deb
akil@akil-laptop:~$

---

### Post by nbusiness on 2010-12-24
Thanks alot works great.

---


---
title: "trying to install driver for dell wireless card / how to use &quot;make&quot;"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by trancine on 2009-12-07
I have a 64 bit dell precision m6400. it was running vista, but crashed after a few days, so I did a clean install of the latest ubuntu. I know nothing about linux, and can't get my wireless card working. Here's what I've done:
I ran a command to generate an html file listing all my hardware. I can supply the file, if necessary, but what I think is relevant is that the network controller, "BCM4322 802.11a/b/g/n Wireless LAN controller", was listed as working (or "claimed"), which according to the troubleshooting guide, meant that its driver (which was listed as "b43_pci-bridge"; I realize at some point I need to delete this) was installed but not working properly. I googled "BCM4322 802.11a/b/g/n Wireless LAN controller" and found here [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) a hybrid driver supplied by broadcom that would work w/ linux. I downloaded the tarred file onto a usb drive then put it on my linux computer and untarred it. But an early step of broadcom readme is to "Build the driver as a Linux loadable kernel module (LKM)" by typing "make". But when I type "make" I get:
"No targets specified and no makefile found. Stop."
I've been doing tons of searches to find out how to make "make" work. I think I've succesfully installed "build-essential" but still can't make "make" work. Could anybody help me with some very detailed instructions (i.e. written as if for a six year old)? thanks.

---

### Post by mvalviar on 2009-12-07
cd to the directory where you extracted the file then run make.

---


---
title: "ndiswrapper - Encore ENUWI-SG Wireless USB adapter problems"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by bone2006 on 2007-05-24
To start off, I got ndiswrapper to work with this usb adapter for ubuntu 6.10 and recently I took everything out and put in ubuntu 7.10 and I can't seem to get my wifi working.

I used the same drivers I had saved before and I installed ndiswrapper 1.18 the common and utilities.  This usb key has actually two drivers to install and here is what I did before and now it's not working

After the installation I did these commands with sudo:

ndiswrapper -i athfmwdl.inf
modprobe ndiswrapper
modprobe -r ndiswrapper
ndiswrapper -i net5523.inf
modprobe ndiswrapper

At this point when I do ndiswrapper -l to see what I have installed, I get this:

~$ ndiswrapper -l
Installed drivers:
athfmwdl                driver installed 
net5523         driver installed, hardware present 

I then edited the modules file to put ndiswrapper and rebooted and I tried typing in iwconfig and nothing shows up.  I tried editing the interface file as well and still nothing seems to work.  I rebooted a few times, but I can't seem to figure out why I can't get online, when this is exactly what I did with the older ubuntu, unless I'm mistaken.

Any help is greatly appreciated.

---


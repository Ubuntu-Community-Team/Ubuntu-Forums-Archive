---
title: "wireless with siemens gigaset 108 will not start automatically"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by Coleville on 2008-01-13
After some efforts i have installed manually my wireless connection with a siemens gigaset usb adapter 108 device. It works and i have a correct access to internet. The problem is that when i shut down the computer and start again, the device is not automatically recognized. 

To make it work, I have to unplugged the adapter, replug it and then use

modprobe ndiswrapper

in the terminal to relaunch the connection. Any idea to spare me that extra step? Thanks

---

### Post by Coleville on 2008-01-13
The problem is still there when i use

echo 'ndiswrapper' | sudo tee -a /etc/modules

I still have to replug the gigaset, but then it will start without the modprobe command

---

### Post by JNMann on 2008-03-27
I've been trying to get my Gigaset 108 working in Ubuntu also.  As a 'newbie' I'm struggling to understand how to do this, any chance you could give me a few pointers?  Incidentaly, I always have to unplug my 108 in WinXP every boot.

Many thanks,
Justin :-)

---


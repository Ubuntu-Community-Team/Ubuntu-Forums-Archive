---
title: "Can't load ndiswrapper module"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by saz on 2006-08-27
Hey, 

I use a Linksys WUSB54Gv4 wireless card and in order to install it, i followed the exactly rules as in: [http://www.ubuntuforums.org/showthread.php?t=192588]("This forum sticky post")

I'm sure i've done everything allright, cuz i repeated so many times.. The only diference is that i use "ndiswrapper-1.23" (stable).

The problem is that even though on ndiswrapper it says that the driver and the hardware, both, are present, on System>Admin>Network the wireless device (wlan0) does not appear!

I thought that maybe the ndiswrapper module wasn't being loaded, so when i tried to load it using "modprobe ndiswrapper" i got the following error:

> root@sazito:/home/sa# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-386/misc/ndiswrapper.ko): Invalid argument

I really don't know what to do, I hope someone will be able to help me!

Thnks

---


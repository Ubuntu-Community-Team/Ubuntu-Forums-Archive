---
title: "Problems with wireless on Dell laptop - Edgy"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by chapmc on 2006-11-17
I really don't know where to post this.  I am a newbie but my problem is getting the wireless adapter in a Dell B130 laptop to connect.  I have done a lot of web searching and have tried several different solutions to no avail.   It does seem tho that there are lots of problems with the Dell 1370 mini pci card and linux.  I read about Ndiswrapper and using windows drivers but it all sounds complicated and also sounds like I would have to set up the SID and WEP in a control file.  When I travel I want to be able to find a hotspot and connect without modifying a control file.  I have about decided I will just forget about wifi on ubuntu and use windows when I need it.  (I have ethernet connection at home and it works fine).

Am I missing something?  Does anyone know of a program that would work with my internal wifi card and will find hotspots and allow easy connection?

Many thanks for any opinions.

---

### Post by stinkypudding on 2006-11-17
I run Edgy on a B120 with wireless.   I use ndiswrapper and network manager to connect to my network and other networks when I'm mobile.   I have the BCM4318 wireless card, which I imagine is what you're using.   Try this link, it may be helpful:

[http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318)

---

### Post by chapmc on 2006-11-17
Thank you very much for the info.  I will give it a try.

---

### Post by chapmc on 2006-11-17
OK I tried it like the thread said but now the pci 1 says "unassigned" and there is no wireless entry in the "networking" window.

I would like for someone to help me diagnose this but I don't want to do it now.  I will post something at a later time.  I think I need to check the boot log but I don't know where it is.

---


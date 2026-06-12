---
title: "No matter what nothing works!!"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by Shawn7 on 2008-07-21
ALright I've posted a couple of times about my wireless problem and got some good input but I still cant get my laptop connected wiressly. I have a dell Inspiron E1705 and It uses the bcmw94312 wlan mini pci card and no matter whatI've done all the ndiswrapper stuff I cant get it to connect through my router I need some major help cause I dont want to have to uninstall ubuntu 8.04 but If I cant get it to connect I have no other choice , oh by the way this is my first ever install with linux so if that helps.

---

### Post by scorp123 on 2008-07-21
Broadcom devices ("bcm ....") suck badly under Linux because Broadcom Inc. just won't release any details on how to make it work.

I avoid Broadcom wherever I can and only buy Laptops with Intel WiFi chips .... those usually work out of the box.

If you can return your laptop ... do it.

---

### Post by rogier.de.groot on 2008-07-21
My laptop (which I'm using right now) has a Broadcom wireless card, which works fine on Ubuntu 8.04 and Linux Mint 5.0 (which I'm running right now, it is based on Ubuntu 8.04). As long as I use Windows drivers via ndiswrapper and disable (blacklist) the 'ssb' module which interferes with ndiswrapper.

---

### Post by steveneddy on 2008-07-21
> **rogier.de.groot said:**
> My laptop (which I'm using right now) has a Broadcom wireless card, which works fine on Ubuntu 8.04 and Linux Mint 5.0 (which I'm running right now, it is based on Ubuntu 8.04). As long as I use Windows drivers via ndiswrapper and disable (blacklist) the 'ssb' module which interferes with ndiswrapper.

Good advise.

---

### Post by Friccy on 2008-07-22
> **Shawn7 said:**
> ALright I've posted a couple of times about my wireless problem and got some good input but I still cant get my laptop connected wiressly. I have a dell Inspiron E1705 and It uses the bcmw94312 wlan mini pci card and no matter whatI've done all the ndiswrapper stuff I cant get it to connect through my router I need some major help cause I dont want to have to uninstall ubuntu 8.04 but If I cant get it to connect I have no other choice , oh by the way this is my first ever install with linux so if that helps.

Hi! I had the same problem.
It looks like Broadcom is not supporting Linux, so you have to use the Windows drivers.
Follow this thread and hope will work for you as it did for me. It saved Ubuntu on my new laptop. I was so nervous, that I wanted to uninstall it.
[http://ubuntuforums.org/showthread.php?t=813363](http://ubuntuforums.org/showthread.php?t=813363)
Good luck!

---


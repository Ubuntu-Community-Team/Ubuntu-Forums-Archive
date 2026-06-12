---
title: "Need help getting snu5600 working"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by tomplast on 2006-12-28
Hi.

Could anyone help me getting my wireless network working. My wireless router seems to work fine (have never used one before but i can login to it (through a wired connection).

The problem is that my second computer should connect to the wireless network through a USB adapter called Philips SNU5600. I have no experience from this and I haven't got further then to have found out (hopefully) that Philips SNU5600 should (in theory at least) work with the ZD1211B driver.

I would accept any solution, either if it's open source or closed. Thank you.

---

### Post by c.dric on 2006-12-28
check the second post in this thread : 
[http://ubuntuforums.org/showthread.php?t=314360&highlight=snu5600](http://ubuntuforums.org/showthread.php?t=314360&highlight=snu5600)

it looks like there may be a how-to for that hardware.

---

### Post by tomplast on 2006-12-28
> **c.dric said:**
> check the second post in this thread : 
[http://ubuntuforums.org/showthread.php?t=314360&highlight=snu5600](http://ubuntuforums.org/showthread.php?t=314360&highlight=snu5600)

it looks like there may be a how-to for that hardware.

Nope I followed the guide but when I run iwconfig it finds no wlan0 :/

Somehow it's working now...

---

### Post by damole1 on 2007-02-20
Maybe too late but i do snu5600 works whith  ndiswrapper-1.37 and a driver found on the installation cd.
Assuming you have ndiswrapper already installed copy the folder /snu5600/driver in your home.In that folder there is only 1 file with .inf (cpwgu.inf) extension but it doesn't works:(  so,rename file Driver.2K adding .inf (=Driver.2K.inf) and try to use it!My T23 with Kubuntu 6.10 like it :) 
bye

P.S. I've tried ZD1121b driver before with no results.

---

### Post by tomplast on 2007-07-02
Now I just got it working by just loading these modules:

zd1211rw
zd1211rw-mac80211

And I who have tried compiling and messing around to get it work :P

---


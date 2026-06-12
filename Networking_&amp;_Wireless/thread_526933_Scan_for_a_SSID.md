---
title: "Scan for a SSID"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by will71110 on 2007-08-16
I have a Broadcom "AirForce One" WIFI and I want to scan for an SSID.  Well when I use "iwlist scan" I get that the interface doesn't support scanning : no such device.  Any ideas?

---

### Post by Spr0k3t on 2007-08-16
From the sound of it, your wireless network adapter is not configured properly.  Have you been able to connect before?

---

### Post by will71110 on 2007-08-16
No.  It seems I cant use the standard drives that came with ubuntu.   Was reading that I have to run ndiswrapper I think.  I havent been able to DL this because I'm without internet on my laptop. (home router blew up, waiting on another one)

---

### Post by Spr0k3t on 2007-08-17
The best suggestion I can give you there is to download and compile the latest sources from the ndiswrapper source tree.

[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

Have you done an "lspci" to get an idea of the chipset you are using?  You may be able to install the bcm43xx package and it would work for you then.

---


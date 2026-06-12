---
title: "[SOLVED] Unable to use any security on WiFi"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by ayanefan on 2008-11-16
Hi there!

I'm just setting up my work PC in my home office and have a bit of a problem.  I just installed Ubuntu 8.10 with all the updates but I cannot get my wireless cards to connect using any wireless security.  I have a Dlink wua-2340 USB card that I configured using the NDISWRAPPER, it did load successfully.  I can see my local Linksys Router (SRX400 Bios 1.00.20 should be the latest) and ESSID.  

-When I connected with WPA, it would ask me for my passphrase but never worked, kept asking over and over.
-When I connected with WEP, same thing.
-I disabled the security and setup the router to accept the MAC address only (got it through iwconfig) would not connect.
-Now I removed all security on the router (open to all) and it connects, I'm typing this up with the unsecured connection (oh God!).

Any idea what may be happening?  Thank you in advance.
-ayanefan

PS- I tried with a Belkin PCI Wireless G card too and would not connect either.  I'm not using any special application to connect to wireless, just the default Ubuntu Network configuration.

---

### Post by ayanefan on 2008-11-16
Please lock this thread, I found the same discussion 5 posts below.
[http://ubuntuforums.org/showthread.php?t=963379](http://ubuntuforums.org/showthread.php?t=963379)

---

### Post by ayanefan on 2008-11-16
Fixed my problem with the link above,  used the following line:
[B]
sudo apt-get install linux-backports-modules-intrepid-generic[/B]

I can now use WEP and MAC address security but WPA is still not available.  

I hope this helps others.
Thanks!:popcorn:

---


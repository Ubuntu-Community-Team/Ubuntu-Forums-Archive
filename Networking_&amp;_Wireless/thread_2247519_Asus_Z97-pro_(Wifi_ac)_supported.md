---
title: "Asus Z97-pro (Wifi ac) supported?"
date: 2014-10-08
forum: Networking &amp; Wireless
---

### Post by eezacque on 2014-10-08
Does Ubuntu support motherboard Asus Z97-pro (Wifi ac), or does it take a lot of four-letter words?

---

### Post by Vladlenin5000 on 2014-10-09
Hi, welcome.

What is the Asus Z97-pro WiFi card?

(Yes, we could look it up but you're the one asking therefore it is your homework)

---

### Post by eezacque on 2014-10-10
Asus Z97-pro (wifi ac) as in [http://www.asus.com/Motherboards/Z97PROWiFi_ac/](http://www.asus.com/Motherboards/Z97PROWiFi_ac/)

And, no, this is not a wifi card but a motherboard, but some kind soul moved this here from the Hardware section   ;)

---

### Post by Vladlenin5000 on 2014-10-10
It's a question of networking & wireless so I think it's better here.
The link only show the WiFi characteristics, not which chipset it has. Most are natively supported already, including many modern ac cards/chips and those should work just fine.
If you already have Ubuntu installed you can follow the instructions here - [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) - to run the wireless script for a full system network info with many details not usually available other way (you can run the commands of the script one by one and end up with the same information; the script is way more practical). You can also run it from a live session.
If you have Windows installed then at the devices manager both the human readable name and the Product ID + Vendor ID will be there. Please post back your findings.
If no OS at all, as mentioned above, just run any Ubuntu in a live session and follow instructions for the wireless script.

---

### Post by eezacque on 2014-10-24
It works. I had to use the Broadcom 802.11 Linux STA wireless driver, included in the distro, but everything else seems to work straight out of the box.

---

### Post by Vladlenin5000 on 2014-10-24
I'm glad it's working with minimum effort.
Please use the thread tools to mark this one as solved so others may benefit.

---


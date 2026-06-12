---
title: "Help with simple wifi access point setup."
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by tufkal on 2006-09-05
I recently got fed up with my router from Linksys and decided to turn my linux server into a router as well.  I installed a fresh copy of Dapper and went to work figuring out how to do it.

Me internet is eth0, and my LAN is eth1.  In the end, I apt-get'd firestarter and dhcp3-server, and have everyhing working now after a little finagling :)

The next step is to use my nice Atheros (madwifi) card to add wireless to my router box.  Firestarter does not include the scripting to use multiple interfaces so I guess I'm doing it manually.

After searching the forums, i found a few threads surrounding this but most were too vague or overly complex for what I'm trying to do.  I already have DHCP setup.  I already have the routing/NAT setup.  I can ifconfig my card into master mode, set an IP, and even connect to it from my laptop.  But to get them all to work together is where i'm failing.

I know that I can use hostapd and wpa_supplicant to add WPA/EAP/etc authentication, and I may do that at some point in the future.  Maybe radius if im feeling lucky.  But right now I dont want any of that.  Once I get the basics working I will move on to authentication.  

Can anyone give me a point in the right direction?

---

### Post by tufkal on 2006-09-05
Anyone?  Please? :D

---


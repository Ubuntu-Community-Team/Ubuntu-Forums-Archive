---
title: "Can't configure wifi on Thinkpad T60 with Atheros AR5BXB6"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by g0nzo on 2007-11-04
Hi,

Ubuntu 7.10 successfully finds my wireless card (lspci says that it's Atheros AR5BXB6) and wireless network. But when I enter the WEP key and set it to use DHCP, it simply can't connect.

When using Windows it works without any problems.

Any ideas or (preferably) working solutions? :)

---

### Post by g0nzo on 2007-11-05
Uhm... any ideas? :)

---

### Post by g0nzo on 2007-11-06
Switching to pump instead of dhclient3 fixed the problem - more info here - [http://ubuntuforums.org/showpost.php?p=3711747&postcount=85](http://ubuntuforums.org/showpost.php?p=3711747&postcount=85)

---


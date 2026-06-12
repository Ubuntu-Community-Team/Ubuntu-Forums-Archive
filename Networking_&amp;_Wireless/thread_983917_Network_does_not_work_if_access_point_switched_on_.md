---
title: "Network does not work if access point switched on after computer"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by Mark224 on 2008-11-16
Networking does not start properly if I power the computer up before the access point.  I am using a LinkSys USB wireless adaptor with ndiswrapper and WPA2 security.  I have manually configured the networking (using wpa_supplicant.conf & /etc/network/interfaces etc).

The outputs from ifconfig and iwconfig look normal and my routing table is fine.  However, if I try to ping something, I get "destination unreachable".  If I reboot it works but I would like a fix for this.

---

### Post by Mark224 on 2009-01-16
Bump

---

### Post by g0rd99 on 2009-01-16
Your computer is probably receiving it's DNS automatically via DHCP. It can be checked with ifconfig, comparing your net address after booting both with and without the AP switched on. You may have to accept turning on the AP first.

---

### Post by Mark224 on 2009-01-23
I am not using DHCP - everything is configured manually.

It's also more fundamental than DNS since I can't even ping the router using its IP address.

The wireless SSID shows up using "iwconfig" but there is no connectivity.

---


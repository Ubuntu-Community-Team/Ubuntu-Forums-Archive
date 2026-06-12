---
title: "No dhcp option in network-admin application"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by lbarcala on 2007-03-27
I have a problem with DHCP and network-admin (System/Admin/Networking). When I go to the properties of an interface, I have only static IP option, and I cannot choose DHCP. If I edit /etc/network/interfaces, and put "iface eth0 inet dhcp", DHCP works fine, but network-admin does not allow to select DHCP the same.

How can I enable DHCP at network-admin? Any clues to solve the problem?

I have updated from Breezy to Dapper (It is not a clean Dapper installation), but I don't know if it worked in Breezy (I didn't use DHCP before).

---

### Post by Big_Croc7 on 2007-03-28
With the network window open, select your ethernet connection and click properties, then under configuration you should have the option of either a static address or of using DHCP - or do you mean DHCP isn't in the list? (I've never seen that before!)

---

### Post by lbarcala on 2007-04-01
Indeed, DHCP isn't in the list (only static IP option is shown).

---


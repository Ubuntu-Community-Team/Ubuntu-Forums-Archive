---
title: "resolv.conf"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by spx3 on 2008-01-19
hi
 I'm using debian 
 my /etc/resolv.conf gets overwritten for me every time I change it
 how do I make so that changes stay permanent ?

---

### Post by sqrt2 on 2008-01-20
The most likely program to overwrite your /etc/resolv.conf is your DHCP client. You could remove the "domain-name-servers" option from "request" in /etc/dhcp3/dhclient.conf to stop that. (Re-initialize your network interface after doing so.)

If you want more flexibility, take a look at the "resolvconf" package.

---


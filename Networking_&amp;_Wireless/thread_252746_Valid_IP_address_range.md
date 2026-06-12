---
title: "Valid IP address range"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by aizen on 2006-09-07
I need to change the address of my network subnet which cannot be 192.168.0.
I found the address ranges I can use but I don't know where to go in order to change it on Ubuntu. If anyone can help me I will be greatful.

---

### Post by Iowan on 2006-09-07
I presume you're talking static addresses - DHCP would issue the correct range (or the DHCP server would need to be edited).  **/etc/networks/interfaces** would have that information as would administration>networking (or something like that - I'm not near my Ubuntu box).

---


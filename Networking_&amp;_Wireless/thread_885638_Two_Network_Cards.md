---
title: "Two Network Cards"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by choboja on 2008-08-10
Hi,
My setup was working (of sorts - there is an issue with the GIGABYTE onboard lan only working on about 50% of boots), but since my last update I've been left with only one working network device.
"lshw -C network" reports both devices and lists the second as "UNCLAIMED"?
Is there anything I need to do to get both devices working? 
I want to (and had) both ports working with a firewall providing access from one network to the other.
Thanks in advance.  


Gigabyte GA-G31M-S2L, Ubuntu 8.04, 2.6.24.20-generic

---

### Post by Iowan on 2008-08-11
Post **/etc/network/interfaces** file and results of **ifconfig -a**.  Probably more involved than simple configuration, but start there.

---


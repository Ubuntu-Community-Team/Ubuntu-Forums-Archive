---
title: "Belkin Wireless RT61"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by neilford on 2007-01-16
I have a Belkin Wireless PCI Card with an RT61 chipset. I have been trying to get the wireless to work with 6.10
I am very close. The only issue I can see at the moment is I cannot seem to connect to a network. I assigned my default essid in the rt61sta.dat file. It didn' take. When I run iwconfig I see ESSID:"". When I run iwlist ra0 scanning, I see all the networks around me including my own. I tried assigning the network using
sudo iwconfig ra0 essid my-network, but no go. 

I ran dmesg and got: 

ra0: no IPV6 routers present
ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
What is wrong here? Thanks.

neilford

---

### Post by neilford on 2007-01-17
bump

---


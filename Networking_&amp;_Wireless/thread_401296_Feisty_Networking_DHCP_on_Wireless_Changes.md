---
title: "Feisty Networking DHCP on Wireless Changes"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by impactdni on 2007-04-04
Just curious, is there any easy way to make Feisty automatically run dhcp on the selected interface when changing my wireless network?

Currently, I use the network manager, switch my wireless network (laptop moves around a lot), but then after doing that, have to open a terminal and run dhclient on wlan0.  Is there any way to tack that onto the set of iwconfig's its already doing when switching networks?

---

### Post by bdidihey on 2007-04-04
I have a similar issue on Feisty, I have to do a sudo ifdown eth1 / sudo ifup eth1 for it to get an IP address.

iwconfig show assocation with the AP- but no IP ADDRESS... 

Worked fine on 6.10

Ideas appreciated :)

---


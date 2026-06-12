---
title: "Installing Senao NL-2511cd Ext 2."
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by Dementor75 on 2008-09-03
I'm trying to get my Senao NL-2511cd workin in ubuntu 8.04

When i insert the card it loads the orinoco drivers, and i want the hostap.

So i googled and found out that i have to blacklist the orinoco drivers so they wont get loaded.

But then, the card is not seen at all.

I installed the hostap driver through synaptic.

I tried doing this:

modprobe hostap_cs

and then the card is shown but (although it only lists only 1 AP which i cannot connect)

And when i try airmon-ng start wlan 0 i get this message:

> root@DHCP:~# airmon-ng


Interface	Chipset		Driver

wifi0		Atheros		madwifi-ng
ath0		Atheros		madwifi-ng VAP (parent: wifi0)
wlan0&#65533;"		Unknown		Unknown (MONITOR MODE NOT SUPPORTED)
Nickname:""		Unknown		Unknown (MONITOR MODE NOT SUPPORTED)

root@DHCP:~# 


Why does the card not work properly? Did i forget something?

Oh yeah, i also have a Atheros AR5007eg installed in the laptop working with the madwifi drivers. This card runs perfectly.
can they conflict???


Thanx in advance

---


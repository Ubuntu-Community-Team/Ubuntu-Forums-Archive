---
title: "network.interface file"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by kditty on 2007-03-23
can anyone tell me what is wrong with my network.interface file? here are the contents below. when i boot up it will not connect, i have to go to the network settings and connect manually, iface ath0 inet dhcp is the network id like to connect to.

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


iface ath0 inet dhcp
wireless-essid broom
wireless-key (removed)


iface ath0 inet dhcp
wireless-essid broom




auto ath0

---

### Post by swamytk on 2007-03-23
You include "auto eth0" if it is your default ethernet card. If ath0 is the only interface (wireless) remove the duplicate entry of "iface ath0 ...."


> **kditty said:**
> can anyone tell me what is wrong with my network.interface file? here are the contents below. when i boot up it will not connect, i have to go to the network settings and connect manually, iface ath0 inet dhcp is the network id like to connect to.

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


iface ath0 inet dhcp
wireless-essid broom
wireless-key (removed)


iface ath0 inet dhcp
wireless-essid broom




auto ath0

---

### Post by airtonix on 2007-03-23
ja and your format is not consistant....

on the second device....eth0 needs to have its "auto eth0" precedding it on the previous line

same with ath0
and remove the duplicate entry for ath0

---


---
title: "wireless not working at startup"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by luke1 on 2007-03-16
When I boot ubuntu (edgy eft) my wireless card (wg311v2) isnt connected to the router, but does after i go to system, administration, networking and deselect and reselect the wireless connection. its running on the acx 111 driver and it would be really helpful if someone could tell me how i can make it connect immediately rather than needing to constantly disable and renable, any help appreciated

---

### Post by Kobalt on 2007-03-17
I think you need the 'auto wlan0' option in your /etc/network/interfaces file. Could you please post the output of the following command line so that I can guide you on what/where to add this option :
```
cat /etc/network/interfaces
```

---

### Post by luke1 on 2007-03-18
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid Home Network
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX










auto wlan0

---


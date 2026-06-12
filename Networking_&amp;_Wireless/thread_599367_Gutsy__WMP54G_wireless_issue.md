---
title: "Gutsy : WMP54G wireless issue"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by Kim Ming Yap on 2007-11-01
In summary:

1) AMD 64 bit machine & Gutsy
2) WMP54G

Problem is each time i shutdown and reboot, the wireless network could be sometimes on and sometimes off.

However on the administration-> network : the wireless icon always shows activated.

If i could access the internet after a reboot i am happy but if i could not then i have to each time deactivate and reactivate the wireless icon on the adminstration -> network manually. This is a pain and so unpredictable.

Please help.

configuration on /etc/network/interfaces

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


iface ra1 inet dhcp
wireless-essid LinksysKMY
wireless-key 12345678

auto ra1

iface ra0 inet dhcp
wireless-key 12345678
wireless-essid LinksysKMY

auto eth0

auto ra0

---


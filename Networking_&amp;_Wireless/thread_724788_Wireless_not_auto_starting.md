---
title: "Wireless not auto starting"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by ozindfw on 2008-03-15
It all works, but but only after I use 

KWiFIManager|Configuration Editor|General Settings|Activate

sudo dhclient

The interfaces file is:

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
allow-hotplug eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

wireless_mode managed
wireless-essid xxxxxxx
wireless-key xxxxxxxxxx

Installing Wicd  has no effect, I still need to use the sequence above to get it to work.  What am I missing?

Oz

---


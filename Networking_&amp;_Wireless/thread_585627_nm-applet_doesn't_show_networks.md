---
title: "nm-applet doesn't show networks"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by corrosion on 2007-10-21
As written on title, it doesnt show wireless networks as it was shoing before with 7.04. I didnt touch /etc/network/interfaces anyway I looked and it seems OK. I upgraded from feisty to 7.10. What can I do? Thank you!

The archive (i made not itinerant to make wifi connect to ap):

:/etc/network# cat interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid philips

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid philips


iface ppp0 inet ppp
provider ppp0

---


---
title: "DNS not updating correctly when using wired Ethernet"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by NetworkGuy on 2006-11-14
Hi All,

I'm wondering if someone can point me in the correct direction to fix a minor problem I'm experiencing.

My laptop uses both wired and wireless connections.  All of these connections are using DHCP.   When I use my wireless card, my DNS entries in resolv.conf are updated correctly.  However when I use my wired interface (eth0), while my IP address is correct for the network I'm on, my DNS entries in resolv.conf do not update and retain the old nameserver information.  since I'm in control of the DHCP server I use at my business, I can verify that DNS information is passed in the DHCP communications.

This was happening with Dapper and still appears to happen with me on Edgy.

Thanks all.  


contents of /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Something_other_than_this

---


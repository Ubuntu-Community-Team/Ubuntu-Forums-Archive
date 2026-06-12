---
title: "Bridging wireless and ehternet kills ethernet connection"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by Silver Streak on 2007-02-14
I've been trying to bridge my wireless card (ath0) to my ethernet connection (eth0) so that I can make an access point, namely for Nintendo WiFi Connection use. :) I'm running Dapper with an older kernel, because the last time I upgraded the kernel, I got the X BSoD. Here's a sample /etc/networking/interfaces file looks like as I'm trying to do this:

```
auto lo
iface lo inet loopback

(#)auto eth0
(#)iface eth0 inet dhcp

(#)auto ath0
(#)iface ath0 inet (static, dhcp, manual)
(#)wireless-mode master
(#)address (Address)
(#)netmask 255.255.255.0
(#)broadcast (Broadcast Address)
(#)wireless-essid (ESSID)

auto br0
iface br0 inet dhcp
bridge_ports eth0 ath0

```

(Note that the () marks means that I've tried it with and without, or with different options. Those are NOT in my file when I restart.)

However, when I restart my networking interfaces, I cannot access the internet from the computer, and wireless devices can only connect to the point, not to the internet. In this case, I have to stop the bridge, delete the bridge, uncomment the ethernet and comment the bridge, and restart. Is there something I'm doing wrong? Do I need a kernel module? I'm stumped about this.

---


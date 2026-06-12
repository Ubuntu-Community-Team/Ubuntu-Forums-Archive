---
title: "DirecWay Optimization Help"
date: 2005-05-17
forum: Networking &amp; Wireless
---

### Post by MonkeyWrench32 on 2005-05-17
I found [this](http://www.dslreports.com/faq/satellite/7.%20Tips%20for%20Non-Windows%20Users) over at Broadband Reports for optimizing my DirecWay settings:

> One way system:

Place the following in /etc/rc.local or /etc/boot.local depending on your linux distribution.

echo 134900 >> /proc/sys/net/core/rmem_default
echo 134900 >> /proc/sys/net/core/rmem_max
echo 64 >> /proc/sys/net/ipv4/ip_default_ttl
echo 0 >> /proc/sys/net/ipv4/tcp_timestamps
echo 1 >> /proc/sys/net/ipv4/tcp_sack
echo 1 >> /proc/sys/net/ipv4/tcp_window_scaling
ifconfig eth0 mtu 1460 

Since Ubuntu doesn't have an rc.local or boot.local, how can I go about doing this?  Also, I get a "permission denied" error when running any of the commands (except the mtu one) in the terminal (with or without sudo).

---

### Post by MonkeyWrench32 on 2005-05-17
[QUOTE=MonkeyWrench32]I found [this](http://www.dslreports.com/faq/satellite/7.%20Tips%20for%20Non-Windows%20Users) over at Broadband Reports for optimizing my DirecWay settings:

 

Since Ubuntu doesn't have an rc.local or boot.local, how can I go about doing this?  Also, I get a "permission denied" error when running any of the commands (except the mtu one) in the terminal (with or without sudo).[/QUOTE]
 Bump.  Help me please!

---

### Post by MonkeyWrench32 on 2005-05-19
Last chance bump.

---


---
title: "Feisty Wireless Won't Start at Boot"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by timking on 2007-04-29
Dell Inspiron E1505, IPW3945, Fresh Feisty Install

I have to run wlassistant after starting Feisty to get wireless to work.  Here is my /etc/network/interfaces:

```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth1
iface eth1 inet dhcp
wireless-essid XXXXX
wireless-key XXXXXXXXXX

```

---


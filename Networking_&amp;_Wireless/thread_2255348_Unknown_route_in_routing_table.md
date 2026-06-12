---
title: "Unknown route in routing table"
date: 2014-12-04
forum: Networking &amp; Wireless
---

### Post by mike265 on 2014-12-04
I have several static routes in my /etc/network/interfaces file, however none seem to be working. I have a route in my routing table I have never seen before

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.10.10.1      0.0.0.0         UG    100    0        0 eth1
[COLOR=#000000][highlight][/COLOR]localnet        *               255.255.255.0   U     0      0        0 eth1[COLOR=#000000][/highlight][/COLOR]

```

If I delete the localnet route and reboot the server, all my routes appear in the routing table. However, the localnet route reappears even though I deleted it. If I reboot again, all my routes are gone and localnet route is still there. How can I remove localnet route permanently.


Thank You!

---

### Post by mike265 on 2014-12-04
Figured it out. Had to edit my /etc/hosts file and my /etc/networks file

---


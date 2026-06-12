---
title: "Problems with dhcp: Can't allocate interface ethlease"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by sv75 on 2007-11-01
My KNetworkManager failed to obtain dhcp from eth0 (wire network). When trying manually: 
```

$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.5
...
Can't allocate interface ethlease {
  interface .
Failed to bring up eth0.

$ grep eth0 /etc/network/interfaces
auto eth0
iface eth0 inet dhcp

```

What is that "ethlease"? Ok, lets try dhclient:

```

$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
...
Listening on LPF/eth0/00:16:36:3b:71:61
Sending on   LPF/eth0/00:16:36:3b:71:61
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.37.1
bound to 192.168.37.20 -- renewal in 1477 seconds.

```

Ops, it works. Ok, now with Network manager...
```

$ grep eth0 /etc/network/interfaces
auto eth0
#iface eth0 inet dhcp
$ sudo /etc/init.d/NetworkManager start
 * Starting network events dispatcher NetworkManagerDispatcher                                           [ OK ]
 * Starting network connection manager NetworkManager                                                    [ OK ]

```

Gear is running and running in knetworkmanagr and never stops... 

Google know nothing about "ethlease", but I found some info with "etlease". Nothing useful thought.

I'm using 7.10 but it starts after some upgrade in 7.04

Any advices, please?

---


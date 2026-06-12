---
title: "openvpn routing problem"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by trothigar on 2008-04-27
Hi,

before hardy and during much of hardy beta, i used a vpn (openvpn) without problem. Now it seems that my routing table is doing something rather odd, and I was wondering if anyone could explain why?

route -n before connecting ( I go through a proxy at 10.3.1.1 as well.)
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.4.11.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.4.11.254     0.0.0.0         UG    0      0        0 eth0

```route -n after connecting (I connect via openvpn command line tool)
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.8.0.5       0.0.0.0         255.255.255.255 UH    0      0        0 tun0
172.8.0.1       172.8.0.5       255.255.255.255 UGH   0      0        0 tun0
10.4.11.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.4.11.254     0.0.0.0         UG    0      0        0 eth0

```As I said the vpn works fine on windows boxes and worked on Ubuntu up until a few days ago, so I dont think its a problem with server config.


Thanks,


Trothigar

---


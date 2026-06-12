---
title: "connect: Network is unreachable"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by expatCM on 2008-01-06
When I try to reach the Internet from a network client I get “connect: Network is unreachable
”. I do not understand why since everything seems to be set up.

I have not set up the firewall yet so this cannot be blocking anything so I am a bit stuck.  Any ideas?

**Interfaces on server**
```
Interface	Network	Netmask		Gateway	Broadcast
eth0		192.168.1.0	255.255.255.0		192.168.1.1	192.168.1.255
eth1		10.0.0.0	255.255.255.0		192.688.1.1	10.0.0.255
```

**Routing from server**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth1
192.168.1.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1    0.0.0.0         UG    100    0        0 eth0

```

**Routing from client**
```
Destination     		Gateway         Genmask         Flags Metric Ref    Use Iface

10.0.0.0                	*               	255.255.255.0    U          0      0        0 eth0

link-local             	*               	255.255.0.0         U       1000   0        0 eth0
```

---


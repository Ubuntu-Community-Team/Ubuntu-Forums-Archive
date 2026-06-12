---
title: "Gateways for two subnets"
date: 2014-02-24
forum: Networking &amp; Wireless
---

### Post by elara on 2014-02-24
I have two network devices in two different subnets. eth0 has access to both subnets 0 and 1 via external configurations (I cannot access) and eth1 has only access to its own subnet 1. Both devices have a static IP configured in /etc/network/interfaces with the eth1 default gateway

```

iface eth0 inet static
        address 10.155.249.2
        netmask 255.255.255.0
        broadcast 10.155.249.255

auto eth1
iface eth1 inet static
        address 129.187.255.169
        netmask 255.255.255.248
        broadcast 129.187.255.175
        gateway 129.187.255.174

```

Although every device in subnet 0 can access subnet 1, the answer is lost somewhere on the way. If I try to reach network 1 with other devices in network 0 (e.g. ping), I get a timeout. According to tcpdump, the request reaches the system, but apparently it does not reply with eth0, because the default gateway is on eth1; see routing table:

```

Destination            Gateway             Genmask           Flags   MSS Window  irtt Iface
0.0.0.0            129.187.255.174   0.0.0.0         UG        0 0          0 eth1
10.155.249.0       0.0.0.0           255.255.255.0   U         0 0          0 eth0
129.187.255.168    0.0.0.0           255.255.255.248 U         0 0          0 eth1

```

I guess, I understand the problem so far and I think I need an explicit route to the subnet 10.155.249.0 for eth0, but I do not know exactly how it should look like.

---

### Post by elara on 2014-03-05
*bump*

---


---
title: "Two default gateways"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by djails on 2007-05-24
Hi,
I have two network cards in my PC running feisty.  /etc/network/interfaces looks like this:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth1
iface eth1 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1

auto eth2
iface eth2 inet static
address 192.168.0.47
netmask 255.255.255.0

```

The problem is that when I restart the network ifs (/etc/init.d/networking restart), I end up with two default gateways in the routing table, even though /etc/network/intferfaces doesnt explicitly define a default gw for eth2.
```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth2
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
```

Since 192.168.0.1 isnt a gateway, I cant access anything outside 192.168.[10].x

I checked "man interfaces" which doesnt mention anything about NOT setting up default gateways when bringing an interface up. The only workaround I found was to create a script :
```
cat /usr/bin/remove_def_gw
#!/bin/bash
route del default gw 192.168.0.1

```
and change the definition for eth2 in /etc/network/interfaces to:
```
auto eth2
#iface eth2 inet dhcp
iface eth2 inet static post-up /usr/bin/remove_def_gw
address 192.168.0.47
netmask 255.255.255.0

```

Ugly but it does the job...
Does anyone know how to control default gateway settings in /etc/network/interfaces (other than the "gateway" directive) so that enabling eth2 does NOT set up a default gateway in the routing table ?

thanks

---

### Post by vjeko on 2007-05-24
Try setting up a localhost as a defualt gateway on eth2... not sure if this is going to work.

---


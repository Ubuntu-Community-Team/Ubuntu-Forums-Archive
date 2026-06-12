---
title: "Default route not working when configuring routing tables via iproute2"
date: 2016-03-08
forum: Networking &amp; Wireless
---

### Post by gsc on 2016-03-08
Hi,


I am having some weird issues with my network route config on my Ubuntu 15.10 server.


I have the following configured on my interfaces.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

 # dns-* options are implemented by the resolvconf package, if installed

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
  address 10.10.10.10
  netmask 255.255.255.0
  dns-nameservers 10.10.11.100 10.10.12.100
       post-up ip route add 10.10.10.0/24 dev eth0 src 10.10.10.10 table rttbl1
        post-up ip route add default via 10.10.10.1 dev eth0 table rttbl1
        post-up ip rule add from 10.10.10.10/32 table rttbl1
        post-up ip rule add to 10.10.10.10/32 table rttbl1

auto eth1
iface eth1 inet static
  address 10.10.10.11
  netmask 255.255.255.0
  dns-nameservers 10.10.11.100 10.10.12.100
       post-up ip route add 10.10.10.0/24 dev eth1 src 10.10.10.11 table rttbl2
       post-up ip route add default via 10.10.10.1 dev eth1 table rttbl2
       post-up ip rule add from 10.10.10.11/32 table rttbl2
       post-up ip rule add to 10.10.10.11/32 table rttbl2

```

and this is my rt_tables

```

#
# reserved values
#
255 local
254 main
253 default
0 unspec
#
# local
#
#1 inr.ruhep
1  rttbl1
2  rttbl2

```

But when I try to ping anything outside of 10.10.10.0 I get network unreacheable. It seems that the default gateway on the rttbl1 and rttbl2 are not being used.

```

ip route list table rttbl2


default via 10.10.10.1 dev eth1
10.10.10.0/24 dev eth1  scope link  src 10.10.10.11

```
```

ip route list table rttbl1


default via 10.10.10.1 dev eth0
10.10.10.0/24 dev eth0  scope link  src 10.10.10.10

```
```


PING 10.10.11.100 (10.10.11.100) from 10.10.10.10 eth0: 56(84) bytes of data.
From 10.10.10.10 icmp_seq=1 Destination Host Unreachable
From 10.10.10.10 icmp_seq=2 Destination Host Unreachable
From 10.10.10.10 icmp_seq=3 Destination Host Unreachable
From 10.10.10.10 icmp_seq=4 Destination Host Unreachable

```
```

PING 10.10.11.100 (10.10.11.100) from 10.10.10.11 eth0: 56(84) bytes of data.
From 10.10.10.11 icmp_seq=1 Destination Host Unreachable
From 10.10.10.11 icmp_seq=2 Destination Host Unreachable
From 10.10.10.11 icmp_seq=3 Destination Host Unreachable
From 10.10.10.11 icmp_seq=4 Destination Host Unreachable

```

---

### Post by gsc on 2016-03-08
Some more info
```

ip route list table all


default via 10.10.10.1 dev eth0  table rttbl1
10.10.10.0/24 dev eth0  table rttbl1  scope link  src 10.10.10.10
default via 10.10.10.1 dev eth1  table rttbl2
10.10.10.0/24 dev eth1  table rttbl2  scope link  src 10.10.10.11
10.10.10.0/24 dev eth1  proto kernel  scope link  src 10.10.10.11
10.10.10.0/24 dev eth0  proto kernel  scope link  src 10.10.10.10
192.168.122.0/24 dev virbr0  proto kernel  scope link  src 192.168.122.1
broadcast 127.0.0.0 dev lo  table local  proto kernel  scope link  src 127.0.0.1
local 127.0.0.0/8 dev lo  table local  proto kernel  scope host  src 127.0.0.1
local 127.0.0.1 dev lo  table local  proto kernel  scope host  src 127.0.0.1
broadcast 127.255.255.255 dev lo  table local  proto kernel  scope link  src 127.0.0.1
broadcast 10.10.10.0 dev eth1  table local  proto kernel  scope link  src 10.10.10.11
broadcast 10.10.10.0 dev eth0  table local  proto kernel  scope link  src 10.10.10.10
local 10.10.10.11 dev eth1  table local  proto kernel  scope host  src 10.10.10.11
local 10.10.10.10 dev eth0  table local  proto kernel  scope host  src 10.10.10.10
broadcast 10.10.10.255 dev eth1  table local  proto kernel  scope link  src 10.10.10.11
broadcast 10.10.10.255 dev eth0  table local  proto kernel  scope link  src 10.10.10.10
broadcast 192.168.122.0 dev virbr0  table local  proto kernel  scope link  src 192.168.122.1
local 192.168.122.1 dev virbr0  table local  proto kernel  scope host  src 192.168.122.1
broadcast 192.168.122.255 dev virbr0  table local  proto kernel  scope link  src 192.168.122.1
fe80::/64 dev eth1  proto kernel  metric 256  pref medium
unreachable default dev lo  table unspec  proto kernel  metric 4294967295  error -101 pref medium
local ::1 dev lo  table local  proto none  metric 0  pref medium
local fe80::9a4b:e1ff:fe0b:8966 dev lo  table local  proto none  metric 0  pref medium
ff00::/8 dev eth1  table local  metric 256  pref medium
unreachable default dev lo  table unspec  proto kernel  metric 4294967295  error -101 pref medium

```
```

root@HPATTLABCLOUD:~# ping 10.10.11.100
connect: Network is unreachable

```

---


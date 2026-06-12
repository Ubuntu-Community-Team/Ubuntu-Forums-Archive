---
title: "systemd-networkd with wrong default route"
date: 2020-05-28
forum: Networking &amp; Wireless
---

### Post by petzler on 2020-05-28
Hi,

I'm working with VLANs here:

```

$ ip -d link show dmz
4: dmz@enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default qlen 1000
    link/ether d0:50:99:a3:b0:84 brd ff:ff:ff:ff:ff:ff promiscuity 0 minmtu 0 maxmtu 65535 
    vlan protocol 802.1Q id 90 <REORDER_HDR> addrgenmode eui64 numtxqueues 1 numrxqueues 1 gso_max_size 64000 gso_max_segs 64 
$ ip -d link show mgmt
3: mgmt@enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default qlen 1000
    link/ether d0:50:99:a3:b0:84 brd ff:ff:ff:ff:ff:ff promiscuity 0 minmtu 0 maxmtu 65535 
    vlan protocol 802.1Q id 10 <REORDER_HDR> addrgenmode eui64 numtxqueues 1 numrxqueues 1 gso_max_size 64000 gso_max_segs 64 

```

and want to add a default route for the two networks to *dmz* network:

**dmz.network **
```

[Match]
Name=dmz

[Network]
DNS=192.168.10.1
DNS=1.1.1.1
DNS=8.8.8.8

[Address]
Address=192.168.90.11/24

[Route]
Destination=0.0.0.0/0
Gateway=192.168.90.1
Table=90

[RoutingPolicyRule]
From=192.168.90.0/24
Table=90

```

and **mgmt.network**
```

[Match]
Name=mgmt

[Network]
Gateway=192.168.10.1
DNS=192.168.10.1
NTP=192.168.10.1

[Address]
Address=192.168.10.11/24

[Route]
Destination=192.168.10.0/24
Gateway=192.168.10.1
Table=10

[RoutingPolicyRule]
From=192.168.10.0/24
Table=10

```

wich results into:
```

$ip r
default via 192.168.10.1 dev mgmt proto static 
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown 
172.18.0.0/16 dev br-5a1d1b57b040 proto kernel scope link src 172.18.0.1 
172.19.0.0/16 dev br-72ec11bd3bd8 proto kernel scope link src 172.19.0.1 linkdown 
172.21.0.0/16 dev br-7c5fe20dbe79 proto kernel scope link src 172.21.0.1 linkdown 
172.23.0.0/16 dev br-ba2d4fbb272e proto kernel scope link src 172.23.0.1 linkdown 
192.168.10.0/24 dev mgmt proto kernel scope link src 192.168.10.11 
192.168.90.0/24 dev dmz proto kernel scope link src 192.168.90.11 

```

For some reasons, the default *Destination=0.0.0.0/0* from dmz.network isn't taken. Intended is the default gateway *192.168.90.1/24*. So, why happens this and how to fix? This is based on [archlinux VLAN Wiki]("https://wiki.archlinux.org/index.php/VLAN").

---


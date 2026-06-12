---
title: "Multiple gateways? Using shorewall and will install squid later"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by jlounds on 2008-09-22
Hello! I have been trying to search around for a similar question, but am having a hard time knowing *what* to type in! (e.g., redirect, route, multiple gateways, etc)

Here is the deal... I have a new server I am setting up with 3 NICs. eth0 and eth1 are connected to separate T1's, and eth2 is the internal 192.168.168.x network.

I have eth0 working just fine, and eth2. And I have figured out how to use shorewall masquerade to (S?)NAT between eth0 and eth2.

But... I want it instead to use shorewall to NAT between eth1 and eth2, but it won't work.

In fact, I cannot even ping the gateway on eth1. Here is what I am getting:

(IPs changed for security)

```
$ route
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
72.54.94.60    *               255.255.255.252 U     0      0        0 eth1
43.12.11.32     *               255.255.255.224 U     0      0        0 eth0
192.168.168.0   *               255.255.255.0   U     0      0        0 eth2
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         43.12.11.33     0.0.0.0         UG    100    0        0 eth0

$ ping 72.54.94.61
PING 72.54.94.61 (72.54.94.61) 56(84) bytes of data.
From 72.54.94.62 icmp_seq=2 Destination Host Unreachable

```

72.54.94.62 is the IP of eth1 and .61 is the gateway. But I left out the "gateway" part for eth1 in /etc/network/interfaces because if I didn't, my incoming connections on eth0 were being lost.

My gut is telling to running something like this

```
$ route add gw 72.54.94.61 dev eth1
```

But what destination do I give it? If I run

```
$ route add -net 0.0.0.0 gw 72.54.94.61 dev eth1
```

I am running in to the same issue with the incoming connections on eth0

Thank you very much in advance!

Jeremy

---

### Post by jlounds on 2008-09-22
Forgot to post contents of /etc/network/interfaces...

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 43.12.11.41
        netmask 255.255.255.224
        broadcast 43.12.11.224
        gateway 43.12.11.33

auto eth1
iface eth1 inet static
        address 72.54.94.62
        netmask 255.255.255.252
# problems if uncommented!?!    gateway 72.54.94.61

auto eth2
iface eth2 inet static
        address 192.168.168.1
        netmask 255.255.255.0

```

Thanks... Jeremy

---

### Post by Domisd on 2011-04-17
I would like to know if that is possible too but i want to Nat one internal sub-net to two external nics like,

Internal nic ( eth0 )
External nic (eth1 )
External nic ( eth2 )

Example

10.0.0.5 >>> to eth1
10.0.0.7 >>> to eth2

---


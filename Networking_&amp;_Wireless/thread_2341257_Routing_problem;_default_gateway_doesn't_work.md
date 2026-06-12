---
title: "Routing problem; default gateway doesn't work?"
date: 2016-10-26
forum: Networking &amp; Wireless
---

### Post by ronni on 2016-10-26
Hi,

I've installed Ubuntu server 16.04 LTS.

I have two VLANs each with their own IP-scope and a firewall the VLANs for routing

VLAN Id - IP-scope - Gateway
VLAN 10 - 10.20.10.0/24 - 10.20.10.1
VLAN 20 - 10.20.20.0/24 - 10.20.20.1

The Ubuntu server is located in VLAN 10 (10.20.10.101), and can reach other clients in the same VLAN.
```

root@server:~# ping 10.20.10.1
PING 10.20.10.1 (10.20.10.1) 56(84) bytes of data.
64 bytes from 10.20.10.1: icmp_seq=1 ttl=64 time=0.391 ms
64 bytes from 10.20.10.1: icmp_seq=2 ttl=64 time=0.198 ms
```

But if I try to ping something in VLAN 20 eg. my laptop at 10.20.20.55, I get Destination Host Unreachable.

```
root@server:~# ping 10.20.20.55
PING 10.20.20.55 (10.20.20.55) 56(84) bytes of data.
From 10.20.10.101 icmp_seq=1 Destination Host Unreachable
From 10.20.10.101 icmp_seq=2 Destination Host Unreachable
From 10.20.10.101 icmp_seq=3 Destination Host Unreachable
```

But I can ping Google DNS (8.8.8.8):
```
root@server:~# ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=42 time=19.4 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=42 time=19.8 ms

```

The routing table:
```
root@server:~# ip r s
default via 10.20.10.1 dev enp2s0 onlink
10.0.0.0/8 dev enp2s0  proto kernel  scope link  src 10.20.10.101
10.20.10.0/24 dev enp2s0  proto kernel  scope link  src 10.20.10.101

```

Adding a route:
```
root@server:~# ip r a 10.20.20.0/24 via 10.20.10.1 dev enp2s0
```


And the routing table:
```
root@server:~# ip r s
default via 10.20.10.1 dev enp2s0 onlink
10.0.0.0/8 dev enp2s0  proto kernel  scope link  src 10.20.10.101
10.20.20.0/24 via 10.20.10.1 dev enp2s0
10.20.10.0/24 dev enp2s0  proto kernel  scope link  src 10.20.10.101
```


And ping works:

```
root@server:~# ping 10.20.20.55
PING 10.20.20.55 (10.20.20.55) 56(84) bytes of data.
64 bytes from 10.20.20.55: icmp_seq=1 ttl=63 time=37.1 ms
64 bytes from 10.20.20.55: icmp_seq=2 ttl=63 time=61.1 ms
```


I've tried to set up a third VLAN using 100.64.0.0/24 and ping works without adding a route.


Anyone knows why this is? As I know networking, the default route should send data for 10.20.20.0/24 to the firewall, which should route it, but this doesn't happen until I add this extra route for the network.

The firewall currently have an any-any between the two VLANs to test this.


Network configuration:
```
root@server:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp2s0
iface enp2s0 inet static
  address 10.20.10.101
  netmask 255.255.255.0
  gateway 10.20.10.1
```

---

### Post by ronni on 2016-10-26
Found the reason for it not working, but don't know how to fix it other than adding a route.

The reason it doesn't work is that, it have route 10.0.0.0/8 as a link scope (connected) routed; in other words, it thinks that 10.20.20.55 is in the same VLAN and broadcast domain.

I found this by tcpdumping while making a ping; and the server makes an ARP request for the 10.20.20.55 IP-address and not sending it for the default gateway.

```
17:16:39.714199 aa:bb:cc:dd:ee:ff > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Ethernet (len 6), IPv4 (len 4), Request who-has 10.20.20.55 tell 10.20.10.101, length 28
```


This should not happen as far as I can see, because the subnet mask is /24 (255.255.255.0) and not /8 (255.0.0.0), so as I see it, this is a bug or have I made some configuration mistake somewhere?

---

### Post by ronni on 2016-10-26
Apparently Ubuntu doesn't care about my netmask 255.255.255.0

In *ifconfig* and* ip a s* it sees the IP-address as a 255.0.0.0 eg. /8, but the broadcast address is correct.


```
root@server:/etc/network# ip address show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether aa:bb:cc:dd:ee:ff brd ff:ff:ff:ff:ff:ff
    inet 10.20.10.101/8 brd 10.20.10.255 scope global enp2s0
       valid_lft forever preferred_lft forever
    inet 10.20.10.101/24 brd 10.20.10.255 scope global enp2s0
       valid_lft forever preferred_lft forever
    inet6 fe80::ffaa:aaff:aacc:aabb/64 scope link
       valid_lft forever preferred_lft forever

       root@server:/etc/network# ifconfig
       enp2s0    Link encap:Ethernet  HWaddr aa:bb:cc:dd:ee:ff
                 inet addr:10.20.10.101  Bcast:10.20.10.255  Mask:255.0.0.0
                 inet6 addr: fe80::aacc:ddff:fedd:aavbb/64 Scope:Link
                 UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
                 RX packets:5089 errors:0 dropped:0 overruns:0 frame:0
                 TX packets:4845 errors:0 dropped:0 overruns:0 carrier:0
                 collisions:0 txqueuelen:1000
                 RX bytes:423165 (423.1 KB)  TX bytes:1980201 (1.9 MB)
       
       lo        Link encap:Local Loopback
                 inet addr:127.0.0.1  Mask:255.0.0.0
                 inet6 addr: ::1/128 Scope:Host
                 UP LOOPBACK RUNNING  MTU:65536  Metric:1
                 RX packets:236 errors:0 dropped:0 overruns:0 frame:0
                 TX packets:236 errors:0 dropped:0 overruns:0 carrier:0
                 collisions:0 txqueuelen:1
                 RX bytes:17712 (17.7 KB)  TX bytes:17712 (17.7 KB)

```

---


---
title: "Setting 2 IPs on Ubuntu 12.04 with two network adaptor card"
date: 2013-11-29
forum: Networking &amp; Wireless
---

### Post by roo4.id on 2013-11-29
There is a VPS runing ubuntu 12.04.3 server on vmware esxi 5. 
It has 2 valid static IPs and two network cards eth0 and eth1. but only one of the assigned ips is pingable from outside. *(both ips ang gateway is pigable from inside).*
it seems that I receive packets on dead IP, but don't reply them.
 ifconfig will returns:

```
eth0      Link encap:Ethernet  HWaddr 00:50:56:03:43:2b  
          inet addr:91.121.247.155  Bcast:91.121.247.155  Mask:255.255.255.255
          inet6 addr: fe80::250:56ff:fe03:432b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20976 (20.9 KB)  TX bytes:7246 (7.2 KB)

eth1      Link encap:Ethernet  HWaddr 00:50:56:05:11:46  
          inet addr:91.121.247.148  Bcast:91.121.247.148  Mask:255.255.255.255
          inet6 addr: fe80::250:56ff:fe05:1146/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20181 (20.1 KB)  TX bytes:8317 (8.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5884 (5.8 KB)  TX bytes:5884 (5.8 KB)

```

and ip route: 
```
default via 188.165.247.254 dev eth1 
188.165.247.254 dev eth1  scope link 
188.165.247.254 dev eth0  scope link 
```
also ip nei :
```
fe80::12bd:18ff:fee4:5040 dev eth0 lladdr 10:bd:18:e4:50:40 router REACHABLE
fe80::ee30:91ff:fee0:dfc0 dev eth0 lladdr ec:30:91:e0:df:c0 router REACHABLE
fe80::12bd:18ff:fee4:5040 dev eth1 lladdr 10:bd:18:e4:50:40 router REACHABLE
fe80::ee30:91ff:fee0:dfc0 dev eth1 lladdr ec:30:91:e0:df:c0 router REACHABLE

```

but arp -a returns **NO OUTPUT** at all.

this is my **/etc/network/interfaces**

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 91.121.247.155
    netmask 255.255.255.255
    broadcast 91.121.247.155
    post-up route add 188.165.247.254 dev eth0
    post-up route add default gw 188.165.247.254
    post-down route del 188.165.247.254 dev eth0
    post-down route del default gw 188.165.247.254



auto eth1
iface eth1 inet static
    address 91.121.247.148
    netmask 255.255.255.255
    broadcast 91.121.247.148
    post-up route add 188.165.247.254 dev eth1
    post-up route add default gw 188.165.247.254
    post-down route del 188.165.247.254 dev eth1
    post-down route del default gw 188.165.247.254
    dns-nameservers 213.186.33.99

```

the problem is 91.121.247.155 is not pingable from outside. and i don't know why.

I only have two IPS 91.121.247.148 91.121.247.155 ; gateway 188.165.247.254; submask 255.255.255.255; DNS 213.186.33.99 with 2 NICs eth0 and eth1.  How set them to be bingable both from the outside?

**OR HOW TO DO IP ALIASING **on eth0**?**

---


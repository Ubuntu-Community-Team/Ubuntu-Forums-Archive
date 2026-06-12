---
title: "multihome routing issue (not router)"
date: 2016-02-04
forum: Networking &amp; Wireless
---

### Post by dave219 on 2016-02-04
hi all:

i am newbie to linux. i have issues with multihome routing environment (ubuntu 14.x)

the system has two physical interfaces and one tagged sub-interface under eth1: eth0 eth1 and eth1.10:

root@host:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:56:a9:7d:cf  
          inet addr:10.0.0.10  Bcast:10.0.0.127  Mask:255.255.255.128
<snip>

eth1      Link encap:Ethernet  HWaddr 00:50:56:b8:53:22  
          inet6 addr: fe80::250:56ff:fca9:5323/64 Scope:Link
<snip>

eth1.10   Link encap:Ethernet  HWaddr 00:50:56:a9:74:12  
             inet addr:10.128.0.10  Bcast:10.128.0.255  Mask:255.255.255.0
<snip>

my default route pointed to eth0 but i have a static route (10.128.0.0/16) point to eth1.10:

root@host:~# netstat -rna
Kernel IP routing table
Destination    Gateway       Genmask              Flags   MSS Window  irtt  Iface
0.0.0.0         10.0.0.1        0.0.0.0                UG      0 0                 0  eth0
10.0.0.0        0.0.0.0         255.255.255.128   U        0 0                 0  eth0
10.128.0.0    10.128.0.1     255.255.0.0         UG      0 0                  0  eth1.10
10.128.0.0    0.0.0.0          255.255.255.0     U        0 0                 0   eth1.10


now my ping packets to nexthop (in the same subnet) get "Host Unreachable" unless i ping those addresses by specifying interface address:

root@host:~# ping 10.128.0.1
PING 10.128.0.1 (10.128.0.1) 56(84) bytes of data.
From 10.128.0.10 icmp_seq=1 Destination Host Unreachable
From 10.128.0.10 icmp_seq=2 Destination Host Unreachable
From 10.128.0.10 icmp_seq=3 Destination Host Unreachable
From 10.128.0.10 icmp_seq=4 Destination Host Unreachable
From 10.128.0.10 icmp_seq=5 Destination Host Unreachable
^C
--- 10.128.0.1 ping statistics ---
10 packets transmitted, 0 received, +9 errors, 100% packet loss, time 9046ms

root@host:~# ping -l 10.128.0.1 10.128.0.10
PING 10.128.0.10 (10.128.0.10) 56(84) bytes of data.
64 bytes from 10.128.0.10: icmp_seq=1 ttl=64 time=0.067 ms
64 bytes from 10.128.0.10: icmp_seq=2 ttl=64 time=0.007 ms
64 bytes from 10.128.0.10: icmp_seq=3 ttl=64 time=0.005 ms

why is that? how could i fix this?

thanks.

_dave

---


---
title: "EtherVPN routing issues"
date: 2017-09-21
forum: Networking &amp; Wireless
---

### Post by toster132 on 2017-09-21
Hi ubuntu people, I have one problem that drives me nuts. 
I have VPS with Ubuntu Server 16.04 and EtherVPN server on it. Plus I have ASUS router with padavan firware and EtherVPN client. They connected and I can ping the server side from the client but not back. And secondly, I cannot transfer properly all of my traffic through it. 
What iptables rules should I use on both sides to make all this work?
192.168.7.x EtherVPN subnetwork
192.168.1.x my home subnet
xxx.xxx.xxx.xxx - VPS net
yyy.yyy.yyy.yyy - home wan

here is the server side
```
toster@vps436696:~$ ifconfig -aens3      Link encap:Ethernet  HWaddr fa:16:3e:3e:13:08
          inet addr:xxx.xxx.92.115  Bcast:xxx.xxx.92.115  Mask:255.255.255.255
          inet6 addr: fe80::f816:3eff:fe3e:1308/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:3677160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3537856 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:719413905 (719.4 MB)  TX bytes:438805376 (438.8 MB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:12441 (12.4 KB)  TX bytes:12441 (12.4 KB)


tap_soft  Link encap:Ethernet  HWaddr 00:ac:12:cb:3c:1b
          inet addr:192.168.7.1  Bcast:192.168.7.255  Mask:255.255.255.0
          inet6 addr: fe80::2ac:12ff:fecb:3c1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:847777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2118010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:72907878 (72.9 MB)  TX bytes:175370932 (175.3 MB)

toster@vps436696:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         xxx.xxx.64.1     0.0.0.0         UG    0      0        0 ens3
xxx.xxx.64.1     0.0.0.0         255.255.255.255 UH    0      0        0 ens3
192.168.7.0     0.0.0.0         255.255.255.0   U     0      0        0 tap_soft


```

client's side

```

/opt/home/admin # ifconfig
br0       Link encap:Ethernet  HWaddr 10:BF:48:3D:C9:4C
          inet addr:192.168.111.1  Bcast:192.168.111.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9122720 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12662658 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2366806158 (2.2 GiB)  TX bytes:13496981787 (12.5 GiB)


eth2      Link encap:Ethernet  HWaddr 10:BF:48:3D:C9:4C
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:280577842 errors:0 dropped:754 overruns:0 frame:0
          TX packets:225202937 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:354671729374 (330.3 GiB)  TX bytes:183178469651 (170.5 GiB)
          Interrupt:3


eth3      Link encap:Ethernet  HWaddr 10:BF:48:3D:C9:4B
          inet addr:yyy.yyy.224.77  Bcast:yyy.yyy.239.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:234696669 errors:0 dropped:87250 overruns:0 frame:0
          TX packets:260715168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:201863472882 (188.0 GiB)  TX bytes:316530740422 (294.7 GiB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:176088 (171.9 KiB)  TX bytes:176088 (171.9 KiB)


ra0       Link encap:Ethernet  HWaddr 10:BF:48:3D:C9:4C
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6334255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27939105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:736273103 (702.1 MiB)  TX bytes:40716675986 (37.9 GiB)
          Interrupt:4


rai0      Link encap:Ethernet  HWaddr 10:BF:48:3D:C9:48
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7232808 errors:54 dropped:0 overruns:0 frame:0
          TX packets:14222296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1530413623 (1.4 GiB)  TX bytes:18678331200 (17.3 GiB)
          Interrupt:2


rai1      Link encap:Ethernet  HWaddr 10:BF:48:3D:C9:49
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1190410 errors:1 dropped:0 overruns:0 frame:0
          TX packets:979824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:198083200 (188.9 MiB)  TX bytes:853387144 (813.8 MiB)


tun1      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.1  P-t-P:10.8.0.1  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7830 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:1080157 (1.0 MiB)  TX bytes:4175742 (3.9 MiB)


vpn_vpn   Link encap:Ethernet  HWaddr 00:AC:9F:51:44:27
          inet addr:192.168.7.125  Bcast:192.168.7.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:454 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:11002 (10.7 KiB)  TX bytes:43764 (42.7 KiB)



```

if you need additional info please let me know.

---


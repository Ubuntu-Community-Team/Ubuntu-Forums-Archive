---
title: "Card 8187B wireless disconnect"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by lovefreesoftware on 2008-11-09
I have a Realtek 8187B card with the following ID:
> 
Bus 007 Device 003: ID 0bda:8198 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem/QUOTE]

I have installed the Compat wireless drivers, and the driver seems to work. I can connect to the wireless network and it will ping the router but only for the first few seconds of connection:
[QUOTE]
john@john-laptop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=11 ttl=64 time=12.9 ms
64 bytes from 192.168.0.1: icmp_seq=12 ttl=64 time=577 ms
64 bytes from 192.168.0.1: icmp_seq=13 ttl=64 time=6.47 ms
64 bytes from 192.168.0.1: icmp_seq=14 ttl=64 time=5.02 ms
64 bytes from 192.168.0.1: icmp_seq=15 ttl=64 time=10.2 ms
64 bytes from 192.168.0.1: icmp_seq=48 ttl=64 time=5.46 ms
From 192.168.0.12 icmp_seq=64 Destination Host Unreachable
From 192.168.0.12 icmp_seq=65 Destination Host Unreachable
From 192.168.0.12 icmp_seq=66 Destination Host Unreachable

However, Network manager shows me as still connected, but I receive no more packets after this point. 

I have tried WCID, but have the same problem as with network manager.

> john@john-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:44:ff:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3592616288 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25756 (25.7 KB)  TX bytes:25756 (25.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:92.40.78.200  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1440  Metric:1
          RX packets:1330 errors:18 dropped:0 overruns:0 frame:0
          TX packets:1409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1491001 (1.4 MB)  TX bytes:149848 (149.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:ff:f8:f0  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:9eff:feff:f8f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26618 (26.6 KB)  TX bytes:27269 (27.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-9E-FF-F8-F0-38-66-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Can anyone suggest what the problem is?

---

### Post by lovefreesoftware on 2008-11-09
Managed to solve with good advice from Tom-D in this post:

[http://ubuntuforums.org/showthread.php?t=792092&highlight=8187B]("http://ubuntuforums.org/showthread.php?t=792092&highlight=8187B")

---


---
title: "Ubunutu 13.10 Internet stopped working - LAN works fine."
date: 2014-04-07
forum: Networking &amp; Wireless
---

### Post by jamesbf on 2014-04-07
Hi Everyone,

I've searched quite a bit for a solution to this problem but nothing I've found seems to work.  I'm a complete noob with Linux, so any assistance would be much appreciated.

**My Situation:** 
I've recently installed Ubuntu 13.10 on a PC (Dual boot with Windows 7). The PC is connected to my router via an ethernet cable. When running on Windows 7, I can access other PCs on the LAN, and the internet. When running Ubuntu, I can access other PCs on the LAN, but not the internet.

[B]Further Details:
[/B]- Initially the internet was working from Ubuntu, but it stopped quite suddenly (I haven't changed anything intentionally). I've tried reboots, enabling/disabling the network adapter, nothing seems to work.
- My router ip is 192.168.0.1. I have the PC in question set to use DHCP, and it is usually assigned 192.168.0.13.
- If I try to ping google.com, it seems to be able to resolve the domain name to an ip addr, but I get "Destinatin Port Unreachable"
```

PING google.com (62.254.36.187) 56(84) bytes of data.
From 192.168.0.13 icmp_seq=1 Destination Port Unreachable
From 192.168.0.13 icmp_seq=2 Destination Port Unreachable
From 192.168.0.13 icmp_seq=3 Destination Port Unreachable
From 192.168.0.13 icmp_seq=4 Destination Port Unreachable

```

- In other posts with similar problems, people ask for the output of "ifconfig", and "route -n", so here's mine:
```
eth0      Link encap:Ethernet  HWaddr bc:5f:f4:67:21:be  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::be5f:f4ff:fe67:21be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214041 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8772112 (8.7 MB)  TX bytes:252118482 (252.1 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:201469 (201.4 KB)  TX bytes:201469 (201.4 KB)



```

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

Thanks for reading this far!  If you have any suggestions I'd love to hear them.

---

### Post by varunendra on 2014-04-10
Welcome to the forums James!

What are the outputs of -
```
nm-tool
ping -c4 192.168.0.1
ping -c4 8.8.8.8
sudo lshw -C network
```??

---


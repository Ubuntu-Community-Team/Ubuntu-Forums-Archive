---
title: "[SOLVED] [Hardy] RT61 problem (pinging)"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by webit on 2008-05-15
Recently I've upgraded to 8.04 LTS desktop edition from 7.10. I use self compiled RT61 drivers for my wireless card (guide from ubuntu.com docs: [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61))

Now I have strange problem. When I connect to my desktop remotely  
I have often about 2 seconds freezes. I checked by pinging my router (192.168.1.1 address) and this is what I saw:

```
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=1343 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=343 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=0.787 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=0.790 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=0.797 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=0.817 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=0.791 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=0.819 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=1355 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=64 time=356 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=0.788 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=64 time=0.810 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=64 time=0.807 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=0.805 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=64 time=1.79 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=64 time=0.782 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=64 time=1367 ms

```

As you can see, each 8th ping response comes after about 1.3 second. I can't find out what's the reason too long pings each 8th packet.

Also I saw many errors in TX packets :(

```
~$ ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:0e:e8:e6:7e:22
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15749 errors:125 dropped:125 overruns:0 carrier:0
          collisions:56 txqueuelen:1000
          RX bytes:7389673 (7.0 MB)  TX bytes:309013 (301.7 KB)
          Interrupt:21

```

Can anyone help me with that :confused:

---

### Post by webit on 2008-05-15
Problem resolved by instaling new driver from [Ralink website]("http://web.ralinktech.com/ralink/Home/Support/Linux.html"). The driver in version 1.1.2.1 supports kernel 2.6.24 :)

One important thing, there is bug in source code. File Module/rtmp_main.c line 348 is:
```
device = dev_get_by_name(net, slot_name);
```
should be:
```
device = dev_get_by_name(slot_name);
```

That wrong line cause error while compiling module ;-)

---


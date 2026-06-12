---
title: "Wired connection keeps loosing internet connection on Ubuntu 18.04.2 LTS"
date: 2019-04-09
forum: Networking &amp; Wireless
---

### Post by cookiemonster2019 on 2019-04-09
I am running Unbuntu 18.04.2 LTS.

Running a ping shows that I keep loosing packets
```
ping google.com -D -O
```

```
[1554813201.789920] 64 bytes from lhr35s05-in-f14.1e100.net (216.58.212.78): icmp_seq=1515 ttl=54 time=9.15 ms[1554813202.790238] 64 bytes from lhr35s05-in-f14.1e100.net (216.58.212.78): icmp_seq=1516 ttl=54 time=9.17 ms
[1554813203.792015] 64 bytes from lhr35s05-in-f14.1e100.net (216.58.212.78): icmp_seq=1517 ttl=54 time=9.67 ms
[1554813204.793209] 64 bytes from lhr35s05-in-f14.1e100.net (216.58.212.78): icmp_seq=1518 ttl=54 time=9.10 ms
[1554813205.794539] 64 bytes from lhr35s05-in-f14.1e100.net (216.58.212.78): icmp_seq=1519 ttl=54 time=9.23 ms
[1554813206.795682] 64 bytes from lhr35s05-in-f14.1e100.net (216.58.212.78): icmp_seq=1520 ttl=54 time=9.07 ms
[1554813208.793010] no answer yet for icmp_seq=1521
[1554813208.802225] 64 bytes from lhr35s05-in-f14.1e100.net (216.58.212.78): icmp_seq=1522 ttl=54 time=9.13 ms
[1554813210.809027] no answer yet for icmp_seq=1523
[1554813210.818212] 64 bytes from lhr35s05-in-f14.1e100.net (216.58.212.78): icmp_seq=1524 ttl=54 time=9.12 ms
[1554813212.825006] no answer yet for icmp_seq=1525
[1554813213.849020] no answer yet for icmp_seq=1526
[1554813214.873033] no answer yet for icmp_seq=1527
[1554813215.897025] no answer yet for icmp_seq=1528
[1554813216.921026] no answer yet for icmp_seq=1529
[1554813217.945047] no answer yet for icmp_seq=1530
[1554813218.969034] no answer yet for icmp_seq=1531
[1554813219.993022] no answer yet for icmp_seq=1532
[1554813221.017070] no answer yet for icmp_seq=1533
[1554813222.041048] no answer yet for icmp_seq=1534
[1554813223.065043] no answer yet for icmp_seq=1535
[1554813224.089020] no answer yet for icmp_seq=1536
[1554813225.113039] no answer yet for icmp_seq=1537
[1554813226.137056] no answer yet for icmp_seq=1538
[1554813227.161056] no answer yet for icmp_seq=1539
[1554813228.185024] no answer yet for icmp_seq=1540
[1554813229.209004] no answer yet for icmp_seq=1541
[1554813230.233020] no answer yet for icmp_seq=1542
[1554813231.257036] no answer yet for icmp_seq=1543
[1554813231.266532] 64 bytes from lhr35s05-in-f14.1e100.net (216.58.212.78): icmp_seq=1544 ttl=54 time=9.44 ms
[1554813232.267725] 64 bytes from lhr35s05-in-f14.1e100.net (216.58.212.78): icmp_seq=1545 ttl=54 time=9.12 ms
[1554813233.268997] 64 bytes from lhr35s05-in-f14.1e100.net (216.58.212.78): icmp_seq=1546 ttl=54 time=9.17 ms
[1554813234.270495] 64 bytes from lhr35s05-in-f14.1e100.net (216.58.212.78): icmp_seq=1547 ttl=54 time=9.42 ms
[1554813235.272539] 64 bytes from lhr35s05-in-f14.1e100.net (216.58.212.78): icmp_seq=1548 ttl=54 time=9.97 ms
[1554813236.272766] 64 bytes from lhr35s05-in-f14.1e100.net (216.58.212.78): icmp_seq=1549 ttl=54 time=9.44
```

ifconfig results:
```
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500        inet 192.168.50.92  netmask 255.255.255.0  broadcast 192.168.50.255
        inet6 fe80::d267:e5ff:fee8:6ae1  prefixlen 64  scopeid 0x20<link>
        ether d0:67:e5:e8:6a:e1  txqueuelen 1000  (Ethernet)
        RX packets 787572  bytes 65134999 (65.1 MB)
        RX errors 65744  dropped 1939  overruns 0  frame 7156
        TX packets 1032248  bytes 173826137 (173.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 15101
        device interrupt 16  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 755199  bytes 91690755 (91.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 755199  bytes 91690755 (91.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

The fact that eno1 shows RX errors and dropped im guessing is a bad thing?

I'm quite new to Ubuntu, and have been trying to dig around on this for some time now, but feel a bit blind in doing so, so hoping someone can give me some guidance on investigation and rectifying this issue.

---

### Post by TheFu on 2019-04-10
Need to figure out where the issue lies.
a) NIC on the computer
b) cable to the switch/router
c) switch/router port
d) upstream - internet.

So, if you can ping the router by IP using the LAN IP it has and there aren't any dropped packets, it is either the router/modem or upstream. Call the ISP for help.

There shouldn't be any dropped packets, unless the service is down.  Inside your LAN, there should never be dropped packets, unless you use wifi.

One of my servers that doesn't do much internet traffic:```

$ ifconfig br0
br0       Link encap:Ethernet  HWaddr 00:04:e2:ee:ee:ee
          inet addr:172.22.22.20  Bcast:172.22.22.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40645660 **errors:0 ****dropped:0 **overruns:0 frame:0
          TX packets:19426561 **errors:0 dropped:0 **overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47966789605 (47.9 GB)  TX bytes:58408941430 (58.4 GB)
```
I disable IPv6, that is why that data is missing.

---


---
title: "Issue with adding static route"
date: 2014-12-26
forum: Networking &amp; Wireless
---

### Post by brianatlarge on 2014-12-26
I've got a VPN tunnel established with Private Internet Access VPN. I don't mind if all the internet traffic goes through that tunnel, but there is still some traffic I'd like to pass through my regular eth0 interface.

**Current traceroute**
```
traceroute to 69.16.179.26 (69.16.179.26), 30 hops max, 60 byte packets
 1  10.113.1.1 (10.113.1.1)  32.193 ms  32.948 ms  33.391 ms
 2  * * *
 3  162.253.128.161 (162.253.128.161)  54.270 ms  52.773 ms  53.530 ms
 4  te0-7-0-9.221.ccr22.yyz02.atlas.cogentco.com (38.122.69.121)  55.012 ms xe-9-2-1-31.tor10.ip4.gtt.net (199.229.229.153)  51.876 ms te0-7-0-9.221.ccr22.yyz02.atlas.cogentco.com (38.122.69.121)  53.529 ms

```


**Current routing table**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.113.1.5      128.0.0.0       UG    0      0        0 tun0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
10.113.1.1      10.113.1.5      255.255.255.255 UGH   0      0        0 tun0
10.113.1.5      *               255.255.255.255 UH    0      0        0 tun0
128.0.0.0       10.113.1.5      128.0.0.0       UG    0      0        0 tun0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
209.222.15.237. 192.168.1.1     255.255.255.255 UGH   0      0        0 eth0

```

Now I add in my static route:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.113.1.5      128.0.0.0       UG    0      0        0 tun0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
10.113.1.1      10.113.1.5      255.255.255.255 UGH   0      0        0 tun0
10.113.1.5      *               255.255.255.255 UH    0      0        0 tun0
69.16.179.26    192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
128.0.0.0       10.113.1.5      128.0.0.0       UG    0      0        0 tun0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
209.222.15.237. 192.168.1.1     255.255.255.255 UGH   0      0        0 eth0

```

**Traceroute:**
```
traceroute to 69.16.179.26 (69.16.179.26), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  1.167 ms  1.853 ms  1.827 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *

```

Why wouldn't this static route send traffic correctly?

---


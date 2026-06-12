---
title: "Static Host Route Not Working"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by schnarff on 2007-11-09
I've got a host that I need to get to that is configured to only allow access from a given network (my work). Since I'm not physically on that network today, but only on it through a VPN, I had figured that I'd need to add a route for that host that uses the VPN gateway. I did so with:

route add -host 1.2.3.4 gw 5.6.7.8

My routing tables then had an entry for this host on the very top line:

```
alex@home: ~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
1.2.3.4         5.6.7.8         255.255.255.255 UGH   0      0      0 cipsec0
...
0.0.0.0         192.168.2.68    0.0.0.0         UG    0      0      0 eth0

```

I figured that would do the trick. However, I wasn't able to get to the host...and when I tried a traceroute, I was shocked to see it using my default gateway to get to the host:

```
alex@home: ~$ traceroute 1.2.3.4
traceroute to 1.2.3.4 (1.2.3.4), 30 hops max, 46 byte packets
 1  gateway (192.168.2.68)  17.179 ms  10.007 ms  10.005 ms
...
```

It's as if it's just not honoring my routing table. Can anyone help me figure out why this his happening?

---


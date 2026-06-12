---
title: "Have ipv6 Address But Cannot Reach ipv6 Website"
date: 2015-10-23
forum: Networking &amp; Wireless
---

### Post by phoenix-seek on 2015-10-23
Hi:

I have ipv6 address and default gateway , but I cannot reach ipv6 website.

Here is the situation:

[COLOR=#000000]* v6 works from  windows when wired[/COLOR]
[COLOR=#000000]* v6 works from Linux over wireless[/COLOR]
[COLOR=#000000]* v6 fails from Linux when wired[/COLOR]


```

ifconfigeth1      Link encap:Ethernet  HWaddr 00:4c:00:00:24:88  
          inet addr:166.111.81.179  Bcast:166.111.81.255  Mask:255.255.255.128
          inet6 addr: 2402:f000:1:5404:1931:5a11:bdfb:88e6/64 Scope:Global
          inet6 addr: 2402:f000:1:5004:1931:5a11:bdfb:88e6/64 Scope:Global
          inet6 addr: 2402:f000:1:5004::52/128 Scope:Global
          inet6 addr: fe80::24c:ff:fe00:2488/64 Scope:Link
          inet6 addr: 2402:f000:1:5404:24c:ff:fe00:2488/64 Scope:Global
          inet6 addr: 2402:f000:1:5004:24c:ff:fe00:2488/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:215137 (215.1 KB)  TX bytes:53894 (53.8 KB)

```


```

ip -6 route2402:f000:1:5004::52 dev eth1  proto kernel  metric 256  expires 2591808sec
2402:f000:1:5004::/64 dev eth1  proto kernel  metric 256  expires 604609sec
2402:f000:1:5404::/64 dev eth1  proto kernel  metric 256  expires 604609sec
fe80::/64 dev eth1  proto kernel  metric 256 
default via fe80::203:fff:fe11:cc4c dev eth1  proto static  metric 100
 
```


```

traceroute6 ipv6.google.com
traceroute to ipv6.google.com (2607:f8b0:4007:805::100e) from 2402:f000:1:5404:1931:5a11:bdfb:88e6, 30 hops max, 24 byte packets
 1  2402:f000:1:5404::1 (2402:f000:1:5404::1)  4.277 ms  3.158 ms  2.918 ms
 2  * * *
 3  * * *


```


Is there something wrong with my configuration? How can I fix it? Thanks!

---

### Post by SeijiSensei on 2015-10-24
Is this computer acting as the router and connected directly to the Internet?  Or is there a router upstream from this?  Is that router configured to handle IPv6?

---

### Post by phoenix-seek on 2015-10-25
It's just my laptop, I have two operating system , I can reach IPv6 website on win10, but I cannot reach IPv6 website on ubuntu with the same wire.

---


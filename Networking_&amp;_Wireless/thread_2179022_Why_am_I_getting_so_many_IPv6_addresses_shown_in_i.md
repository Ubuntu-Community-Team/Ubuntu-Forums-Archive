---
title: "Why am I getting so many IPv6 addresses shown in ifconfig (Ubuntu 13.04)"
date: 2013-10-06
forum: Networking &amp; Wireless
---

### Post by tlotr2 on 2013-10-06
Hi,

Can someone please help me in understanding why there are so many IPv6 addresses shown under ifconfig. I have really no clue about it. And also how can I get rid of all those IPv6 addresses.

```
eth0     Link encap:Ethernet  HWaddr fc:75:16:e1:1d:1b  
          inet addr:192.168.10.135  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::fe75:16ff:fee1:1d1b/64 Scope:Link
          inet6 addr: 2002:b6ed:b0b2:b:7488:2566:e6d0:1c05/64 Scope:Global
          inet6 addr: 2002:b6ed:b0b2:b:fe75:16ff:fee1:1d1b/64 Scope:Global
          inet6 addr: fec0::b:7488:2566:e6d0:1c05/64 Scope:Site
          inet6 addr: fec0::b:fe75:16ff:fee1:1d1b/64 Scope:Site
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:132946 errors:0 dropped:1233 overruns:0 frame:0
          TX packets:55826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43976145 (43.9 MB)  TX bytes:16146372 (16.1 MB)
```

---

### Post by The Cog on 2013-10-06
My guess is that you have an IPv6 router on the LAN, and IPv6 has been autoconfigured from it.
This command to print your IPv6 routes might show something interesting:
route -6

---

### Post by sanderj on 2013-10-06
The fe80: is your local, private IPv6 address. No use outside your LAN

the 2002: addresses are (or: should be) publicly routable. You should be able to reacht [http://ipv6.google.com/](http://ipv6.google.com/) . Also check out [http://test-ipv6.com](http://test-ipv6.com). You have two addresses: one is based on your MAC address (check the trailing e1:1d:1b in both your MAC address and in your 2002: IPv6 address) and thus traceable, the other is more random and thus not traceable.

The fec0: is your site local IPv6 address, which is depreciated.

---

### Post by PaulBx on 2013-10-06
This is normal with ipv6, you can read up about it in wikipedia and the like. It bugged me too until I read about it.

---


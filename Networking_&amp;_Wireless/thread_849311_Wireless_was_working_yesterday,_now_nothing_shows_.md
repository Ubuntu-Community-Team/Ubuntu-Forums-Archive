---
title: "Wireless was working yesterday, now nothing shows up"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by Golevel on 2008-07-04
Yesterday my wireless was working just fine. Today, I started my laptop and now there is no list of wireless connections or anything.

Any ideas?

(I can connect to my wireless connection using other laptops)

---

### Post by alfredska on 2008-07-04
What version of Ubuntu are you running?
Can you report a few command outputs please?

```
ifconfig
iwconfig
```

and if you are using an intel wireless adapter,
```
lsmod | grep iwl
```

if not intel, what wireless adapter are you using?

---

### Post by Golevel on 2008-07-04
(I'm currently using the web via wired connection, but I need to get the wireless working)

ifconfig

> eth0      Link encap:Ethernet  HWaddr 00:1d:09:bd:7d:0d  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:febd:7d0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18710630 (17.8 MB)  TX bytes:1555877 (1.4 MB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:107200 (104.6 KB)  TX bytes:107200 (104.6 KB)


iwconfig

> lo        no wireless extensions.

eth0      no wireless extensions.


lsmod | grep iwl

(nothing comes up)

---

### Post by alfredska on 2008-07-04
> **Golevel said:**
> iwconfig

lo no wireless extensions.

eth0 no wireless extensions. 

Wireless drivers are not loading for you adapter.  What is the make/model of your wireless card?

If you do not know, try
```
lspci | grep Atheros
```

---

### Post by Tony Flury on 2008-07-04
This might be the problem :

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930)

it seems the recent update on the restricted modules breaks wireless for some adapters.

Some people are reporting success dropping back to 2.6.24-18 - if you have that available.

---


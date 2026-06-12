---
title: "No Internet connection after upgrade in VMWare"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by tennesseebrewer on 2010-05-05
I have Ubuntu 10.04 running in VMWare Player. Unfortunately, Windows is the base operating system (cause my wife will not let me make the full switch yet), and when I play it, it cannot connect to the internet. Now, in Karmic, it had no problem connecting, but since the upgrade, it will not connect. Someone, please help! I really want to use this new version, but I can't without the internet. Thanks!

---

### Post by Peter09 on 2010-05-06
Can you provide the following information from the command line
 
```
lshw -C network
```
 
and
 
```
ifconfig
```

---

### Post by tennesseebrewer on 2010-05-06
> **Peter09 said:**
> Can you provide the following information from the command line
 
```
lshw -C network
```
 
and
 
```
ifconfig
```

Here is what I got:
for lshw -C network;
```
 *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0c:29:e5:94:e2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical logical
       configuration: broadcast=yes driver=vmxnet driverversion=2.0.4.0 firmware=N/A latency=64 maxlatency=255 mingnt=6 multicast=yes
       resources: irq:19 ioport:2000(size=128) memory:dc400000-dc40ffff(prefetchable)

```

and for if config;
```

eth0      Link encap:Ethernet  HWaddr 00:0c:29:e5:94:e2  
          inet6 addr: fe80::20c:29ff:fee5:94e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1910 (1.9 KB)  TX bytes:2520 (2.5 KB)
          Interrupt:19 Base address:0x2024 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8800 (8.8 KB)  TX bytes:8800 (8.8 KB)

```

---

### Post by tennesseebrewer on 2010-05-06
I solved the problem... it was not Ubuntu's settings, rather it was VMWare's settings. I needed to click "Enable Bridge" under network options. Thanks!

---


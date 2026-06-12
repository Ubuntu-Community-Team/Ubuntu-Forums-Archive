---
title: "Wired connection not working some times."
date: 2017-10-16
forum: Networking &amp; Wireless
---

### Post by leunam12 on 2017-10-16
My wired connection sometimes stops working, then it comes back by itself. If I use a USB ethernet adapter when it's down I can get a connection; if I boot the live USB I can get a connection, but for some reason my 2 PCI network adapters stop working sometimes.

```
rivasdom@RivasPC-2:~$ ifconfig 
enp3s0    Link encap:Ethernet  HWaddr d8:cb:8a:97:c6:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp5s0    Link encap:Ethernet  HWaddr 00:04:5a:8f:bf:9e  
          inet addr:192.168.1.132  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::b171:8016:12d6:1f72/64 Scope:Link
          inet6 addr: 2602:30a:2ef6:5b80:38fe:e416:e3d4:e62b/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106612561 (106.6 MB)  TX bytes:19581295 (19.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1944 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:186734 (186.7 KB)  TX bytes:186734 (186.7 KB)


```
sudo lshw -c network
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: d8:cb:8a:97:c6:bb
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:27 ioport:d000(size=256) memory:f7d00000-f7d00fff memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 11
       serial: 00:04:5a:8f:bf:9e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.132 latency=32 maxlatency=128 mingnt=64 multicast=yes
       resources: irq:18 ioport:c000(size=256) memory:f7c20000-f7c203ff memory:f7c00000-f7c1ffff


```

Thanks

---

### Post by jeremy31 on 2017-10-16
See if this post helps your issue [https://ubuntuforums.org/showthread.php?t=2374421&p=13698647#post13698647](https://ubuntuforums.org/showthread.php?t=2374421&p=13698647#post13698647)

---

### Post by leunam12 on 2017-10-17
Ok, I tried that and it is working and I haven't had any issues so far

---


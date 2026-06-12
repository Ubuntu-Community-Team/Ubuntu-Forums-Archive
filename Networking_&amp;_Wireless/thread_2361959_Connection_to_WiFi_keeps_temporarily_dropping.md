---
title: "Connection to WiFi keeps temporarily dropping"
date: 2017-05-22
forum: Networking &amp; Wireless
---

### Post by laurastockton on 2017-05-22
Hey, 

I'm a bit of a noob so bear with me if I'm not doing everything correctly. I have recently installed Ubuntu Version 16.04. While online, the connection keeps dropping for a minute or so before coming back online.

The result of the command ifconfig is:

```

enp1s0    Link encap:Ethernet  HWaddr 68:f7:28:8e:b6:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:28818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:2317759 (2.3 MB)  TX bytes:2317759 (2.3 MB)

wlp2s0    Link encap:Ethernet  HWaddr ac:d1:b8:11:03:4f  
          inet addr:192.168.1.219  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2a00:23c4:c700:800:1dc2:e01a:503e:6f94/64 Scope:Global
          inet6 addr: fe80::105b:344c:6e34:5089/64 Scope:Link
          inet6 addr: fdaa:bbcc:ddee:0:1dc2:e01a:503e:6f94/64 Scope:Global
          inet6 addr: fdaa:bbcc:ddee:0:e0e3:7a6d:857b:80b0/64 Scope:Global
          inet6 addr: 2a00:23c4:c700:800:b6e4:343e:1819:4e4f/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:153497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:118297298 (118.2 MB)  TX bytes:25811807 (25.8 MB)

```

and the result of the command route is 

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         bthub           0.0.0.0         UG    600    0        0 wlp2s0
link-local      *               255.255.0.0     U     1000   0        0 wlp2s0
192.168.1.0     *               255.255.255.0   U     600    0        0 wlp2s0


```

Thanks in advance, I appreciate any help someone can give.

---

### Post by Bucky Ball on 2017-05-22
Welcome. Please run the Wirelessinfo Script linked in my signature at the bottom of this post (first line, second red link) and post back the output between code tags, thanks. ;)

In the meantime, before you figure out how to do that, quickly post the output of this command:

```
sudo lshw -C network
```

That will give us some quick and vital info and there may be a known, quick and easy fix for your particular wireless card.

Have you installed any drivers for the card or it just worked 'out-of-the-box'?

---

### Post by laurastockton on 2017-05-26
Thank you for your reply. The result of the command you sent is:

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 10
       serial: 68:f7:28:8e:b6:f0
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:4000(size=256) memory:c0504000-c0504fff memory:c0500000-c0503fff
  *-network
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: ac:d1:b8:11:03:4f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=4.8.0-52-generic firmware=N/A ip=192.168.1.219 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:19 ioport:3000(size=256) memory:c0400000-c0403fff

```

My wireless card did just work as soon as I installed Ubuntu.

---

### Post by laurastockton on 2017-05-26
I've also run the code in your signature; the result is at [https://paste.ubuntu.com/24665926/](https://paste.ubuntu.com/24665926/)

---

### Post by wildmanne39 on 2017-05-26
Do you have access to router?

---


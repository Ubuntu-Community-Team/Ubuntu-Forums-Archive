---
title: "Wireless is not an option for my Network"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by mickbw on 2007-05-22
I had a problem a few days ago with my wireless connection on my laptop. The WIFI light shows but  for some reason  the option to choose a wireless connection no longer exists in my Feisty install.  I can connect to my wired network without a problem.  

Is there a way to uninstall and then reinstall wireless networking?  

A previous reply asked to see /etc/network : > 
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iwconfig:

> lo no wireless extensions.

eth0 no wireless extensions.

ifconnfig
> eth0 Link encap:Ethernet HWaddr 00:19:B9:67:9C:3F
inet addr:192.168.1.101 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::219:b9ff:fe67:9c3f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1239 errors:0 dropped:0 overruns:0 frame:0
TX packets:1199 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1101957 (1.0 MiB) TX bytes:169347 (165.3 KiB)
Interrupt:21

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:103 errors:0 dropped:0 overruns:0 frame:0
TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:10376 (10.1 KiB) TX bytes:10376 (10.1 KiB)



---

### Post by Kobalt on 2007-05-23
Can you please give us additionaly the output of : ```
sudo lshw -C network
```
I assume your wireless interface is ath0. Can you see your card in the list when you run lspci ?

---

### Post by mickbw on 2007-05-23
When I run lshm I get command not found in the terminal.  The sam for lspci.

I am not sure if my card is on ATH0

---

### Post by Kobalt on 2007-05-23
oOops... typo mistake. It's corrected, sorry.

---

### Post by mickbw on 2007-05-23
Hi,  

I would have replied back sooner but for some reason I couldn't access the page at work.  

My lshw settings when I am not connected:
> 
  *-network UNCLAIMED     
       description: Network controller
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:c0200000-c0203fff irq:11
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:67:9c:3f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:c0300000-c0301fff irq:20

I don't know if it will make a difference but this is the same output when I am connected through a wired connection:
>   *-network UNCLAIMED     
       description: Network controller
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:c0200000-c0203fff irq:11
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:67:9c:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.1.101 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:c0300000-c0301fff irq:20


If it has any bearing I am using a Dell Inspiron 1501 laptop with a Dual Core t-50 AMD processor, 1GB Ram.  I got rid of the Windows virus and did a fresh install of Ubuntu Feisty approximately 2 weeks ago.  

Thanks for your assistance,

Michael

---


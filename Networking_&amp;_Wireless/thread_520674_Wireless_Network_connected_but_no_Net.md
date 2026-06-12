---
title: "Wireless Network connected but no Net"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by yashoda on 2007-08-08
Hi, trying to connect to my wireless network.  Network Manager says I'm connected, but there's no Internet access.

Please help.  else it's back to microsoft.

thanks.





lshw -C network shows:

*-network
desecription:  Ethernet interface
product:RTL-8139/8139C/8139C+
VENDOR:  Realtek Semiconductor Co., Ltd.
physical id: 12
bus info: pci@00:12.0
logical name: eth0
version:10
serial: 08.00:46:c0:cf:9d
width:  32 bits
clock:33MHz
capabilities:  bus_master cap_list ethernet physical
configuration:  broadcast=yes driver=8139too driverversion=0.9.28 latency=64 max latency=64 mingnt=32 multicast=yes
resources; ioport: 9c00-9cff iomemory:e0404dff irq:11


*-network
description:  Wireless interface
product: RT2500 802.11g Cardbus/mini-PCI
vendor: RaLink
physical id: 0
bus info: pci@02:00.0
logical name: ra0
version: 01
serial: 00:11:50:66:a8:52
width: 32bits
clock:  33MHz
capabilities bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=RT2500 DRIVERVERSION=1.1.0 beta4 LATENCY=64 MULTICAST=YES WIRELESS=rt2500 Wireless
resources:iomemory: 24000000-24001fff irq:11


iwlist scan shows:

lo Interface doesn't support scanning.

eth0  Interface doesn't support scanning.

ra0  Scan completed

(then lists various cells til it comes to my network)

Cell 06  Address 00:11:50:42:5F:1E
Mode: Managed
ESSID:"belkin54g"
Encryption key: on
Channel: 11
Quality: 68/100 Signal level-53dBm  Noise level: 193dBm



/etc/network/interfaces: Permission denied.

---

### Post by kevdog on 2007-08-08
Can you post ifconfig?

---

### Post by yashoda on 2007-08-08
thanks.

here's the ifconfig

eth0 
Link encap: ethernet HWaddr 08:00:46:c0:cf:9d
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX PACKETS, ERRROS, DROPPED, OVERRUNS, FRAME, TXPACKETS, ERRORS, DROPPED, OVER RUNS, CARRIER, COLLISIONS ALL zero
TXQUEUELEN:1000
RX bytes: 0 TX bytes: 0
Interrupt:11 base address 0xec00

eth0:avah Link encap: Ethernet HWaddr 08:00:46:c0:CF:9D
INET ADDR:169.254.9.26 bCAST:169.254.255.255 mASK:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interupt:11 Base address: 0xec00


lo
link encap:local loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric: 1
RX PACKETS:112 errors:0 dropped:0 overruns:0 frame:0
TX packets:112 ERROS:0 DROPPED:0 OVERRUNS:0 CARRIER:0
COLLISIONS:0 TXQUEUELEN:0
RX bytes:8488 (8.2 KiB) TX bytes: 8488 (8.2 kib)

ra0
Link encap: Ethernet HWaddr 00:11:50:66:A8:52
inet6 addr: fe80: :211:50ff:fe66:a852/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:569 erors:0 dropped: 0 overruns:0 frame:0
TX packets:123754 errors:0 dropped:0 overruns:0 carrier:0
collisions:6 txqueuelen:1000
RX bytes:67241 (65.6 KiB) TX bytes: 5613782 (5.3 MiB)
Interrupt:11  Base address:0xc000

---


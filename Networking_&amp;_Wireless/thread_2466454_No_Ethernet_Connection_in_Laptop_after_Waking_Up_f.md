---
title: "No Ethernet Connection in Laptop after Waking Up from Sleep"
date: 2021-08-28
forum: Networking &amp; Wireless
---

### Post by burner2k2 on 2021-08-28
I have posted this in 2 different forums dedicated for KDE but got no replies even after a couple of weeks. Last resort posting here since this forum seems to be active and helpful. 

I am having issues with my ethernet connection since last week. Noticed that on my laptop, ethernet connection is not recognized after waking up my laptop from sleep. However, the ethernet connection is recognized and connected once I restart my system. IIRC, all I did a software update (can't remember what it was)...

I am using KDE Neon Plasma 5.22.4 and Neon is the only OS on my laptop. My laptop specs

```
Operating System: KDE neon 5.22
KDE Plasma Version: 5.22.4
KDE Frameworks Version: 5.84.0
Qt Version: 5.15.3
Kernel Version: 5.11.0-25-generic (64-bit)
Graphics Platform: X11
Processors: 4 ? Intel? Core? i5-3230M CPU @ 2.60GHz
Memory: 11.6 GiB of RAM
Graphics Processor: Mesa DRI Intel? HD Graphics 4000

```


```
lspci | egrep -i --color 'network|ethernet'
01:00.0 Ethernet controller: Qualcomm Atheros AR8162 Fast Ethernet (rev 10)
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)

```

So after some more research I found out that Ethernet connection is being disabled after waking up. I tried restarting Network manager using

```
sudo service networking restart

```

I get the following error:

```
[FONT=monospace][COLOR=#000000]Failed to restart networking.service: Unit networking.service not found.[/COLOR][/FONT]
```

Here are the output of sudo lshw -C network **after system restart**


```

sudo lshw -C network
[sudo] password for <xxx>:
  *-network                 
       description: Ethernet interface
       product: AR8162 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 10
       serial: 20:89:84:41:97:d5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx driverversion=5.11.0-27-generic duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:e0500000-e053ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 01
       serial: 2c:d0:5a:34:42:66
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=5.11.0-27-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:e0400000-e047ffff memory:e0480000-e048ffff



```output of sudo lshw -C network after **waking up from sleep**


```
sudo lshw -C network
  *-network DISABLED       
       description: Ethernet interface
       product: AR8162 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 10
       serial: 20:89:84:41:97:d5
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=alx latency=0 multicast=yes
       resources: irq:16 memory:e0500000-e053ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 01
       serial: 2c:d0:5a:34:42:66
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=5.11.0-27-generic firmware=N/A ip=192.168.1.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:e0400000-e047ffff memory:e0480000-e048ffff

```

And output of


```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller [8086:1e22] (rev 04)
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)

```

Any ideas on how I can proceed from here. It could be a hardware issue but then again, the issue should persist consistently and not just after waking up. 

I think my network drivers "alx" is already included in kernel and I don't want to mess up any further without guidance.

Hoping folks here would help out. 

Thanks...

---


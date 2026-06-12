---
title: "Ethernet adapter keeps dropping connection after a few minutes"
date: 2015-11-09
forum: Networking &amp; Wireless
---

### Post by marko21 on 2015-11-09
Hello!


I have a problem with the second ethernet adapter on a Ubuntu Server 14.04 machine that I intend to use as a firewall. The adapter in question is a Deltaco USB 3.0 dongle. 


Everything works fine to begin with, and the adapter gets it's address from my modem over DHCP. The connection works fine for a few minutes, but then, without exception, drops. I can't find any difference in the adapter's state, the IP address is still assigned, but no connection through the interface is anymore possible. Nothing appears in logs that I can find.


Running ifdown eth1 && ifup eth1 gets the interface going again, only so the connection can be dropped after a few minutes again. Would anyone have suggestions on how to investigate the problem?


Below some system details, please let me know if I can provide further information. Thanks!
```
~$ uname -a
Linux MyHost 3.16.0-48-generic #64~14.04.1-Ubuntu SMP Thu Aug 20 23:03:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```
```
~$ sudo lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: RT2790 Wireless 802.11n 1T/2R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: e0:b9:a5:a4:b6:7d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.16.0-48-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fe000000-fe00ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 00:01:2e:40:20:c8
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=10.0.0.111 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:43 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth1
       serial: 00:e0:4c:68:05:cb
       size: 100Mbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.06.0 (2014/03/03) duplex=full ip=192.168.0.51 link=yes multicast=yes port=MII speed=100Mbit/s
```

**Edit:** I've experimented further. Turns out the delay before dropping the connection varies from less than a minute up to roughly 10 minutes. So far no longer than that. Before noticing the irregularity, I tried configuring the USB autosuspend for the adapter to -1, and setting autosuspend_delay_ms to a very large number, but neither had any effect. 

I also went through the BIOS settings to see if anything there might affect USB behavior, but couldn't find any such settings. The machine is a Zotac Zbox.

---


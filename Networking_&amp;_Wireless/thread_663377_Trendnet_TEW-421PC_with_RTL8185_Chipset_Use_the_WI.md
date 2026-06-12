---
title: "Trendnet TEW-421PC with RTL8185 Chipset: Use the WIN2000 drivers not the WINXP!!!"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by ubunyou on 2008-01-10
This is more of an FYI that will hopefully save people much pain and suffering.
Using ndiswrapper with the XP drivers shipped with the trendnet TEW-421PC (and probably the 423PI) cards didn't work for me. As soon as I swapped them out for the Win2000 drivers everythin worked great. Save yourself time! Don't use the XP drivers!!
Here's what my `lshw -C network` looks like - i think the version info should be sufficient to distinguish between XP and Win2K driver versions ...

```

> lshw -C network

  *-network
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1d:60:56:e6:06
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.0.7 firmware=N/A latency=0 link=no module=atl1 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: wlan0
       version: 20
       serial: 00:14:d1:34:e5:53
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 **driverversion=1.45+Realtek,01/29/2007,5.1096.0** ip=192.168.1.76 latency=64 link=yes maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


```

---

### Post by ubunyou on 2008-03-04
The trendnet  TEW-421PC never worked quite right. The r8185 dirver didn't work and the ndiswrapper driver would lock up after 30-45 minutes.  I would advise against this card. I tried a linksys WMP54G and it is kicking *** so far with no setup headaches.

---


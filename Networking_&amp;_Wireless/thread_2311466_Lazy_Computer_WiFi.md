---
title: "Lazy Computer WiFi"
date: 2016-01-27
forum: Networking &amp; Wireless
---

### Post by ErmenegildoRos on 2016-01-27
Hello everybody!

Just bought a HP 250 G4, installed Ubuntu 14.04 in it, downloaded last updates during the installation process.
My problem is that I can't reach any WiFi connection if I'm not very close to the router or phone (HotSpot).
My other computer and my phone doesn't have the same problem. I also have a partition with Win10 and the WiFi works fine there. 

This is what i get from: [COLOR=#101010][FONT=Ubuntu]sudo lshw -c network [/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]```
*-network [/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]description: Wireless interface[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]product: RTL8723BE PCIe Wireless Network Adapter[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]vendor: Realtek Semiconductor Co., Ltd.[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]physical id: 0[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]bus info: pci@0000:02:00.0[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]logical name: wlan0[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]version: 00[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]serial: 60:6d:c7:8f:6e:85[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]width: 64 bits[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]clock: 33MHz[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]configuration: broadcast=yes driver=rtl8723be driverversion=3.19.0-25-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]resources: irq:18 ioport:2000(size=256) memory:91200000-91203fff[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]*-network[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]description: Ethernet interface[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]vendor: Realtek Semiconductor Co., Ltd.[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]physical id: 0[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]bus info: pci@0000:03:00.0[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]logical name: eth0[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]version: 07[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]serial: 94:57:a5:e5:e5:c4[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]size: 10Mbit/s[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]capacity: 100Mbit/s[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]width: 64 bits[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]clock: 33MHz[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]resources: irq:117 ioport:1000(size=256) memory:91100000-91100fff memory:91000000-91003fff
```

[/FONT][/COLOR]Than you all in advance!

---

### Post by chili555 on 2016-01-27
Please check here, starting at post #35. If you don't want to try the screwdriver trick, proceed to post #52.

[http://ubuntuforums.org/showthread.php?t=2304607&highlight=rtl8723be](http://ubuntuforums.org/showthread.php?t=2304607&highlight=rtl8723be)

---


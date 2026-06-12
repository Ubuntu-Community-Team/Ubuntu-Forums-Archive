---
title: "Share wired network connection through wireless"
date: 2019-12-20
forum: Networking &amp; Wireless
---

### Post by cylan2 on 2019-12-20
Ubuntu 18.04
How can I share my wired network connection (pppoe) through wifi hotspot? Tried **Turn on wifi hotspot** but **No wifi adapter is found. **No share connection option is shown under ipv4 of the wired network**.** 
Tried:[INDENT=2]**sudo rfkill list**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[/INDENT]
Tried[INDENT=2]**sudo lshw -C network**
network DISABLED
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 01
       serial: bc:85:56:44:98:fd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=5.0.0-37-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:c0500000-c057ffff memory:c0580000-c058ffff
[/INDENT]
For[INDENT=2]**sudo ifconfig wlan0 up**
wlan0: ERROR while getting interface flags: No such device
[/INDENT]

---


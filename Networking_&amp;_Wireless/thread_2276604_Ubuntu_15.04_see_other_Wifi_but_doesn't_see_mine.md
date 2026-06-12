---
title: "Ubuntu 15.04 see other Wifi but doesn't see mine"
date: 2015-05-03
forum: Networking &amp; Wireless
---

### Post by vincent29 on 2015-05-03
Hi, I have problem :) The problem is My wireless working (I guess) it see many other WiFi around me (For example my neighbor's WiFi) but it doesn't see my WiFi. I tried mint 17, elementary for all versions they have the same problem. I tried update kernal bcs in a LinuxMint forum, they said it will solve my problem. This happened while I trying to solve this problem in LinucMint but it didn't solve my problem. Then I delete everyting (Recovery files etc) and finally I install Ubuntu 15.04 but it has the same problem also. What can I do? Pls help. Thank you very much.

I did the update things (apt get update, apt-get dist-upgrade) but still problem continues..

My grammer is not perfect but I believe you understood. If it is not clear I could explain again. Sorry for it.

I am not using a hidden SSID and my password protected with WPA2
My Modem is Airties 5341

these are the outputs from "lshw -C network"

```

*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 0c
       serial: 18:67:b0:4d:31:e3
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:35 ioport:e000(size=256) memory:fea00000-fea00fff memory:d0800000-d0803fff
  *-network
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 48:d2:24:3e:c4:7b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.19.0-15-generic firmware=N/A ip=192.168.165.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:37 memory:fe900000-fe97ffff memory:fe980000-fe98ffff


```

---

### Post by wildmanne39 on 2015-05-03
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---


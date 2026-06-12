---
title: "Ubuntu Net Problem"
date: 2016-12-24
forum: Networking &amp; Wireless
---

### Post by raoufe on 2016-12-24
Hi all
i have recently installed Ubuntu but my Ethernet not worked 
in Network settings it show me cable unplugged but it's connected and i can see him in my router 
"sorry for this Bad Language" 
Thnx.

---

### Post by cariboo on 2016-12-25
A little more information would be helpful, could ytou open a terminal and type the following command?

```
sudo lshw -C network
```

the output should be similar to this:

```
sudo lshw -C network
[sudo] password for cariboo: 
  *-network                 
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 07
       serial: f8:a9:63:7a:e4:e3
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:89 ioport:e000(size=256) memory:d0804000-d0804fff memory:d0800000-d0803fff
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 01
       serial: b8:ee:65:8a:1b:f7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.9.0-11-generic firmware=N/A ip=192.168.0.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d0700000-d077ffff memory:d0780000-d078ffff
```

---

### Post by raoufe on 2016-12-26
no Thing Happened :( 
Please Help Me .

---

### Post by chili555 on 2016-12-26
Please try again and be patient. It takes the system a few moments to collect and display all that data.

---

### Post by victoriano1979 on 2016-12-29
Have you tried the ethtool [interface] command? check /sys/class/net/eth0/ in order to know if everything is fine

---


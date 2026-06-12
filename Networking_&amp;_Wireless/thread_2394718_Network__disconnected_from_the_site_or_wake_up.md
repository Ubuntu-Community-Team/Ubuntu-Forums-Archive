---
title: "Network  disconnected from the site or wake up"
date: 2018-06-20
forum: Networking &amp; Wireless
---

### Post by bedhorn on 2018-06-20
Hi, my HP Pavilion notebook with dual boot Windows and Ubuntu Budgie (18.04 LTS; 4.15.0-23-generic) angry. After disconnecting or waking from sleep, you can not find a network device (both ethernet and wifi). Only when running on battery.
```
sudo lshw -class network
```
```
  *-network                        description: Wireless interface
       product: Wireless 3165
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlo1
       version: 81
       serial: 00:db:df:a8:6b:50
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-23-generic firmware=29.1044073957.0 ip=10.0.0.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:44 memory:fe900000-fe901fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eno1
       version: 07
       serial: 70:5a:0f:28:6f:8b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits



```
I can not exactly figure out what I'm doing differently because it's not always doing that   :mad:

---


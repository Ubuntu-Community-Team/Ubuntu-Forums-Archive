---
title: "Neither WiFi nor ethernet in Ubuntu 20.04.1 LTS"
date: 2020-10-15
forum: Networking &amp; Wireless
---

### Post by alexstip21 on 2020-10-15
First time here. I completed almost 4 weeks with neither WiFi nor Ethernet; I'm using USB tethering for internet connection. I've followed several tutorials and solutions posted in forums but I've been unable to solve my problem hitherto. I'd really appreciate some guidance from scratch i.e. diagnosis, troubleshooting.


Operating System: Ubuntu 20.04.1 LTS

*-network UNCLAIMED       
   description: Ethernet controller
   product: RTL810xE PCI Express Fast Ethernet controller
   vendor: Realtek Semiconductor Co., Ltd.
   physical id: 0
   bus info: pci@0000:02:00.0
   version: 07
   width: 64 bits
   clock: 33MHz
   capabilities: bus_master cap_list
   configuration: latency=0
   resources: ioport:d000(size=256) memory:ef200000-ef200fff memory:e2100000-e2103fff
 *-generic DISABLED
   description: Wireless interface
   product: RTL8821AE 802.11ac PCIe Wireless Network Adapter
   vendor: Realtek Semiconductor Co., Ltd.
   physical id: 0
   bus info: pci@0000:03:00.0
   logical name: wlp3s0
   version: ff
   serial: f0:03:8c:ac:4a:27
   width: 32 bits
   clock: 66MHz
   capabilities: bus_master vga_palette cap_list ethernet physical wireless
   configuration: broadcast=yes driver=rtl8821ae driverversion=5.4.0-48-generic firmware=N/A latency=255 link=no maxlatency=255 mingnt=255 multicast=yes wireless=IEEE 802.11
   resources: irq:130 ioport:c000(size=256) memory:ef100000-ef103fff
  *-network
   description: Ethernet interface
   physical id: 1
   bus info: usb@1:2
   logical name: usb0
   serial: 72:de:96:42:06:a1
   capabilities: ethernet physical
   configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.241 link=yes multicast=yes
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


I [COLOR=#242729][FONT=Arial]don't know whether this initial information is enough. TIA![/FONT][/COLOR]

---


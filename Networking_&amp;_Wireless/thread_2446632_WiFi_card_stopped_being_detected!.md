---
title: "WiFi card stopped being detected!"
date: 2020-07-04
forum: Networking &amp; Wireless
---

### Post by s-viradiya on 2020-07-04
[COLOR=#242729][FONT=Arial][FONT=inherit][FONT=inherit][FONT=inherit]Yesterday, Some updated on my Ubuntu 20.04 were installed. After installation it asked me to restart. After restart, My WiFi card stopped being detected.[/FONT][/FONT][/FONT][/FONT][/COLOR][FONT=Arial][FONT=inherit]
[/FONT]
[/FONT]
[COLOR=#242729][FONT=Arial][FONT=inherit]I'm using Lenovo Ideapad 320, with Ubuntu 20.04.[/FONT]
[FONT=inherit]Here is the output of sudo lshw -C network:
[/FONT]
  [FONT=courier new]*-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: 8c:16:45:14:70:c9
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII
       resources: irq:16 ioport:3000(size=256) memory:94004000-94004fff memory:94000000-94003fff
  *-network
       description: Ethernet interface
       physical id: 3
       bus info: usb@1:3
       logical name: usb0
       serial: 0e:7c:35:4a:11:b3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.176 link=yes multicast=yes[/FONT]

[FONT=inherit]And here is the output of lspci:
[/FONT]
[FONT=courier new]00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point LPC Controller/eSPI Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 920MX] (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
[/FONT]
[FONT=inherit]Currenly I'm using mobile USB ethernet.[/FONT]
[FONT=inherit]My Laptop is in dual boot mode, with Ubuntu 20.04 and Windows 10. Wifi perfectly works with windows 10. Right now I'm using it in windows 10. Problem occurs only with Ubuntu 20.04[/FONT]

[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-07-04
Welcome.

In Windows please check the device manager and post here the full information about the WiFi device.

---


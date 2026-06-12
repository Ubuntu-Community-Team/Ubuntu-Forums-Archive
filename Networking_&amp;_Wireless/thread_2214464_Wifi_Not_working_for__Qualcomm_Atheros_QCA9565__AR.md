---
title: "Wifi Not working for  Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter"
date: 2014-04-01
forum: Networking &amp; Wireless
---

### Post by swanand_phadke on 2014-04-01
Hi,

Recently my OS got updated, since then I am having trouble using Wifi, Can anyone please help ?

**$ lspci**
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)



[HR][/HR]
** lshw -C network**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 74:86:7a:3f:7c:58
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.5 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network UNCLAIMED
       description: Network controller
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c0500000-c057ffff memory:afb00000-afb0ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by Hadaka on 2014-04-01
Hi, please see this thread...post#4

[http://ubuntuforums.org/showthread.php?t=2190930](http://ubuntuforums.org/showthread.php?t=2190930)

thanks.

---

### Post by swanand_phadke on 2014-04-05
Heyy i tried doing the backport driver installation, but it gives me an error as 

Inspiron-3521:~/Desktop/backports-3.13.2-1$ make deconfig-ath9k
Generating local configuration database from kernel ... done.
make[1]: *** No rule to make target `deconfig-ath9k'.  Stop.
make: *** [deconfig-ath9k] Error 2

---

### Post by swanand_phadke on 2014-04-05
Well it was my typo mistake , though i did manage to get it installed, although it doesnt show any effect on the wireless, its still not working :(

---


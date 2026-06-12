---
title: "8192SE wireless problem Toshiba 515"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by lpeter on 2010-03-30
30 Mar 10

Newbie. Having a very similar problem with a Toshiba L515. Has been very frustrating. Performed the procedures as you identified below, with nod to [http://ubuntuforums.org/showpost.php...55&postcount=5]("http://ubuntuforums.org/showpost.php?p=8754255&postcount=5")  but no joy.[INDENT]lpeter@lpeter-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

lpeter@lpeter-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:cd:71:b1
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.102 latency=0 link=yes multicast=yes port=MII speed=100MB/s
resources: irq:28 ioport:4000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:d4600000-d4603fff
lpeter@lpeter-laptop:~$ 

[/INDENT]Using 9.10
Assistance would be greatly appreciated.

Take good care,
Lp

---

### Post by chili555 on 2010-03-30
Are you sure the device is the same? May we see:```
lspci -nn
```Were ther any errors or warnings in the compile process?

---

### Post by lpeter on 2010-03-30
yes, thank you:

lpeter@lpeter-laptop:~$ sudo lspci -nn
[sudo] password for lpeter: 
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)
lpeter@lpeter-laptop:~$

---


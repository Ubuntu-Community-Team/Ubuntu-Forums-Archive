---
title: "Toshiba C50-A X0011 wired and wirless network not working in Ubuntu 12.04"
date: 2014-03-25
forum: Networking &amp; Wireless
---

### Post by Nitiraj_Singh_Rath on 2014-03-25
Hi,

I have recently bought Toshiba C50-A X0011 laptop and installed ubuntu on it. But the network is not working. Probably I don't have the right drivers.
Please point me to the right drivers and installation procedure. Below is the information regarding the system that might be important. Please let me know I you need more information about the system.

ubuntu@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Haswell DRAM Controller [8086:0c04] (rev 06)
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell Integrated Graphics Controller [8086:0416] (rev 06)
00:03.0 Audio device [0403]: Intel Corporation Haswell HD Audio Controller [8086:0c0c] (rev 06)
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point USB xHCI Host Controller [8086:8c31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Lynx Point MEI Controller #1 [8086:8c3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation Lynx Point USB Enhanced Host Controller #2 [8086:8c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point HD Audio Controller [8086:8c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point PCI Express Root Port 1 [8086:8c10] (rev d4)
00:1c.2 PCI bridge [0604]: Intel Corporation Lynx Point PCI Express Root Port 3 [8086:8c14] (rev d4)
00:1c.3 PCI bridge [0604]: Intel Corporation Lynx Point PCI Express Root Port 4 [8086:8c16] (rev d4)
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point USB Enhanced Host Controller #1 [8086:8c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point LPC Controller [8086:8c49] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point 6-Port SATA AHCI Controller [8086:8c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Lynx Point SMBus Controller [8086:8c22] (rev 04)
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0036] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. Device [1969:10a0] (rev 10)




ubuntu@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f7c00000-f7c3ffff ioport:e000(size=128)


ubuntu@ubuntu:~$ uname -r
3.5.0-23-generic




ubuntu@ubuntu:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---


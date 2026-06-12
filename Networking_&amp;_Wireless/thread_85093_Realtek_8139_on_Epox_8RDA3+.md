---
title: "Realtek 8139 on Epox 8RDA3+"
date: 2005-11-01
forum: Networking &amp; Wireless
---

### Post by sciurus on 2005-11-01
Hi,
When I first installed Breezy, my Realtek network card worked fine. After I installed the 686 kernel, it stopped working, even when I boot with 386. The ligt on the back of my motherboard does not light up when the cable is inserted. When I plug the same cable into my other integrated NIC, it works fine.

syslog:
localhost kernel [4294678.877000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
localhost kernel [4294678.877000] 8139cp: pci dev 0000:01:0b.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
localhost kernel [4294678.877000] 8139cp: Try the "8139too" driver instead.
localhost kernel [4294678.879000] 8139too Fast Ethernet driver 0.9.27
localhost kernel [4294678.879000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
localhost kernel [4294678.879000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 19
localhost kernel [4294678.880000] eth1: RealTek RTL8139 at 0x9000, 00:04:61:66:fa:a8, IRQ 19
localhost kernel [4294678.880000] eth1:  Identified 8139 chip type 'RTL-8101'
localhost kernel [4294702.240000] eth1: link down

lsmod:
8139too                23552  0
8139cp                 18432  0
mii                     5248  2 8139too,8139cp

lspci:
0000:01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

ifconfig:
eth1      Link encap:Ethernet  HWaddr 00:04:61:66:FA:A8
          inet6 addr: fe80::204:61ff:fe66:faa8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x9000

Similar problems are discussed at
[http://www.ubuntuforums.org/showthread.php?t=70213](http://www.ubuntuforums.org/showthread.php?t=70213)
[http://www.ubuntuforums.org/showthread.php?t=63852](http://www.ubuntuforums.org/showthread.php?t=63852)

---


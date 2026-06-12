---
title: "msi s270 + intel 2915abg"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by skatedawe on 2006-08-25
I have experienced a lot of trouble with the wlan with kubuntu. I've been compiling all the drives and firmwares 1000 times, cant get it to work. 

lspci: 

0000:02:09.0 Network controller: Intel Corporation PRO/Wireless 2915ABG MiniPCI Adapter (rev 05)

my laptop is; msi s270 @ athlon thurion 64 2.0ghz.. 


My card is; intel PRO / Wireless 2915abg


iwconfig gets me: 

eth1      unassociated  ESSID:""
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



from dmesg: i get; ipw2200: Failed to send SCAN_ABORT: Command timed out.

I got connected 3-4 times, then it disconnected, i could go from 2-4links at www. Then it died.

I've followed the howtos on this forum, still i dont get it. I hate wlan, let me feel the opposite.

plz help me step by step.

---

### Post by skatedawe on 2006-08-27
[17179593.460000] sdhci: ============== REGISTER DUMP ==============
[17179593.460000] sdhci: Sys addr: 0x00000000 | Version:  0x00002010
[17179593.460000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179593.460000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179593.460000] sdhci: Present:  0x01fa0000 | Host ctl: 0x00000000
[17179593.460000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179593.460000] sdhci: Walk up:  0x00000000 | Clock:    0x00000000
[17179593.460000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179593.460000] sdhci: Int enab: 0x01ff00cf | Sig enab: 0x01ff00cf
[17179593.460000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179593.460000] sdhci: Caps:     0x038021a1 | Max curr: 0x00ffffff
[17179593.460000] sdhci: ===========================================
[17179593.508000] mmc0: SDHCI at 0xfbfff800 irq 185 DMA
[17179593.512000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179593.512000] 8139cp: pci dev 0000:02:03.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[17179593.512000] 8139cp: Try the "8139too" driver instead.
[17179593.516000] 8139too Fast Ethernet driver 0.9.27
[17179593.516000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 18 (level, low) -> IRQ 209
[17179593.516000] eth0: RealTek RTL8139 at 0xf8ad2c00, 00:13:d3:f1:25:8a, IRQ 209
[17179593.516000] eth0:  Identified 8139 chip type 'RTL-8101'
[17179593.532000] logips2pp: Detected unknown logitech mouse model 99
[17179593.536000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[17179593.540000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[17179593.540000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179593.544000] ieee80211_crypt: registered algorithm 'NULL'
[17179593.604000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179593.604000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179593.672000] cs: IO port probe 0x100-0x3af: clean.
[17179593.672000] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[17179593.676000] cs: IO port probe 0x820-0x8ff: clean.
[17179593.676000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179593.676000] cs: IO port probe 0xa00-0xaff: clean.
[17179593.744000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179593.744000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179593.744000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[17179593.744000] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 22 (level, low) -> IRQ 217
[17179593.744000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[17179593.756000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 193
[17179593.760000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 193
[17179593.992000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[17179594.976000] ipw2200: Detected geography ZZE (13 802.11bg channels, 19 802.11a channels)
[17179595.012000] eth0: link down
[17179595.432000] lp: driver loaded but no devices found
[17179595.456000] SCSI subsystem initialized
[17179595.468000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179595.468000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179595.468000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179595.524000] Adding 2096472k swap on /dev/hda3.  Priority:-1 extents:1 across:2096472k
[17179596.064000] NET: Registered protocol family 17
[17179596.144000] eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device->is_queue_full.

I got this recently from dmesg.

---


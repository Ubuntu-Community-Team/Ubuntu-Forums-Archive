---
title: "Help getting TV and Radio Card running"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by garwal on 2009-03-01
I have been using Linux for many years now so I am determined to get my tv and radio card working. I have read much on how to do this but I have come totally confused. I know it is asking a lot to have someone to hold my hand while I figure this out but I am good at paying forward. I am posting the results of what I think is the information regarding this card. I really appreciate the help. Actually there are two tuner cards in this system one DVB Sat and the other win TV and  Radio card combo. I only want to get the Radio card running..
Gary


[   12.169754] nvidia 0000:00:0d.0: setting latency timer to 64
[   12.172066] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
[   12.196426] Linux video capture interface: v2.00
[   12.205242] cx23885 driver version 0.0.1 loaded
[   12.205640] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[   12.205651] cx23885 0000:03:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
[   12.205711] CORE cx23885[0]: subsystem: 0070:7801, board: Hauppauge WinTV-HVR1800 [card=2,autodetected]
[   12.364953] cx23885[0]: i2c bus 0 registered
[   12.364975] cx23885[0]: i2c bus 1 registered
[   12.365012] cx23885[0]: i2c bus 2 registered
[   12.391133] tveeprom 2-0050: Hauppauge model 78521, rev C1E9, serial# 2798189
[   12.391135] tveeprom 2-0050: MAC address is 00-0D-FE-2A-B2-6D
[   12.391138] tveeprom 2-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[   12.391140] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   12.391142] tveeprom 2-0050: audio processor is CX23887 (idx 42)
[   12.391144] tveeprom 2-0050: decoder processor is CX23887 (idx 37)
[   12.391145] tveeprom 2-0050: has radio
[   12.391147] cx23885[0]: hauppauge eeprom: model=78521
[   12.408929] cx25840' 4-0044: cx25  0-21 found @ 0x88 (cx23885[0])
[   12.409474] cx23885[0]/0: registered device video0 [v4l2]
[   12.412919] firmware: requesting v4l-cx23885-avcore-01.fw
[   12.492503] cx25840' 4-0044: unable to open firmware v4l-cx23885-avcore-01.fw
[   12.505414] cx23885[0]: registered device video1 [mpeg]
[   12.505416] cx23885[0]: cx23885 based dvb card
[   12.584899] MT2131: successfully identified at address 0x61
[   12.584905] DVB: registering new adapter (cx23885[0])
[   12.584907] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   12.585270] cx23885_dev_checkrevision() Hardware revision = 0xb1
[   12.585276] cx23885[0]/0: found at 0000:03:00.0, rev: 15, irq: 16, latency: 0, mmio: 0xfd600000
[   12.585281] cx23885 0000:03:00.0: setting latency timer to 64
[   12.628631] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   13.176292] lp: driver loaded but no devices found
[   13.270752] Adding 8924068k swap on /dev/sda5.  Priority:-1 extents:1 across:8924068k
[   13.806710] EXT3 FS on sda1, internal journal
[   14.797437] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.172062] ACPI: WMI: Mapper loaded
[   15.358524] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ processors (2 cpu cores) (version 2.20.00)
[   15.358994] powernow-k8:    0 : fid 0x16 (3000 MHz), vid 0xa
[   15.358997] powernow-k8:    1 : fid 0x14 (2800 MHz), vid 0xc
[   15.358999] powernow-k8:    2 : fid 0x12 (2600 MHz), vid 0xe
[   15.359001] powernow-k8:    3 : fid 0x10 (2400 MHz), vid 0x10
[   15.359002] powernow-k8:    4 : fid 0xe (2200 MHz), vid 0x10
[   15.359004] powernow-k8:    5 : fid 0xc (2000 MHz), vid 0x10
[   15.359006] powernow-k8:    6 : fid 0xa (1800 MHz), vid 0x10
[   15.359007] powernow-k8:    7 : fid 0x2 (1000 MHz), vid 0x12
[   15.951123] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   15.999732] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   15.999740] apm: disabled - APM is not SMP safe.
[   16.133460] ppdev: user-space parallel port driver
[   17.500023] Clocksource tsc unstable (delta = -282929765 ns)
[   19.038239] Bluetooth: Core ver 2.13
[   19.038691] NET: Registered protocol family 31
[   19.038696] Bluetooth: HCI device and connection manager initialized
[   19.038704] Bluetooth: HCI socket layer initialized
[   19.074179] Bluetooth: L2CAP ver 2.11
[   19.074194] Bluetooth: L2CAP socket layer initialized
[   19.094738] Bluetooth: RFCOMM socket layer initialized
[   19.095212] Bluetooth: RFCOMM TTY layer initialized
[   19.095223] Bluetooth: RFCOMM ver 1.10
[   19.126126] Bluetooth: SCO (Voice Link) ver 0.6
[   19.126140] Bluetooth: SCO socket layer initialized
[   19.173097] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.173114] Bluetooth: BNEP filters: protocol multicast
[   19.215273] Bridge firewalling registered
[   19.215982] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   23.532589] NET: Registered protocol family 17

---


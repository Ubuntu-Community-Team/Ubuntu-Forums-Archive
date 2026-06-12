---
title: "No Netmork Devices Available"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by Kchymet on 2010-12-05
So I installed Ubuntu as a dual-boot with Windows and I'm having trouble making a wired connection. I have tried lspci and ifconfig eth0 (0-5 actually) and get the following results:
```

kchymet@kchymet-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RD890 Northbridge only single slot PCI-e GFX Hydra part (rev 02)
00:02.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port D)
00:05.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port E)
00:06.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port F)
00:07.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port G)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
02:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4381 (rev 11)
04:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
05:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
05:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
06:00.0 VGA compatible controller: ATI Technologies Inc Device 68b8
06:00.1 Audio device: ATI Technologies Inc Device aa58
kchymet@kchymet-desktop:~$ ifconfig eth0
eth0: error fetching interface information: Device not found

```
Anyone know how I can connect to my network?

---

### Post by theozzlives on 2010-12-05
Looks like your controller has a Marvel Technology chipset. You could go to their website and see if they have a Linux Driver.

---


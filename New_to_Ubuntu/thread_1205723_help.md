---
title: "help"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by ukaoha ugo on 2009-07-06
my system crashes, either in d middle of movie, when im playin music files or when im copying files from a disk. just started using ubuntu 9.04 on my hp6735s.pls help.tanx

---

### Post by s.fox on 2009-07-06
Hi,

Do you get any error messages?  Also what are your computer specifications?

-Silver Fox

---

### Post by Don1500 on 2009-07-06
A little more information please.
error codes
system specs
program your using when you have the problem.
output of (in terminal type) lspci

---

### Post by ukaoha ugo on 2009-07-07
my system crashes when
1.copying files from an ext harddisk
2. watchin a movie
3.playing music wit music box

```

manolo@manolo-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4357 (rev 10)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
manolo@manolo-laptop:~$ 

```
thanks

---

### Post by Don1500 on 2009-07-07
Are you running 9.04?
If yes, than you have an ATI card that is not supported fully. Suggest you reinstall with 8.10 or 8.04.

---


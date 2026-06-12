---
title: "just installed 9.04 not sound"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by nnamdi on 2009-07-01
i just finished making a clean installation but my sound seems not to be working

lspci

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

lspci -n
```

manolo@manolo-laptop:~$ lspci -n
00:00.0 0600: 1022:9600
00:01.0 0604: 1022:9602
00:04.0 0604: 1022:9604
00:07.0 0604: 1022:9607
00:09.0 0604: 1022:9608
00:11.0 0106: 1002:4391
00:12.0 0c03: 1002:4397
00:12.1 0c03: 1002:4398
00:12.2 0c03: 1002:4396
00:13.0 0c03: 1002:4397
00:13.1 0c03: 1002:4398
00:13.2 0c03: 1002:4396
00:14.0 0c05: 1002:4385 (rev 3a)
00:14.2 0403: 1002:4383
00:14.3 0601: 1002:439d
00:14.4 0604: 1002:4384
00:14.5 0c03: 1002:4399
00:18.0 0600: 1022:1300 (rev 40)
00:18.1 0600: 1022:1301
00:18.2 0600: 1022:1302
00:18.3 0600: 1022:1303
00:18.4 0600: 1022:1304
01:05.0 0300: 1002:9612
02:00.0 0200: 11ab:4357 (rev 10)
06:00.0 0280: 14e4:4315 (rev 01)
manolo@manolo-laptop:~$ 

```

---

### Post by Sardonism on 2009-07-01
It looks like you're on a  HP Pavillion dv4-1225dx or something similar.

Try this:
[URL="http://georgia.ubuntuforums.org/showthread.php?t=1073090"]
http://georgia.ubuntuforums.org/showthread.php?t=1073090[/URL]

---

### Post by nnamdi on 2009-07-01
it is not in the dv series
it is hp 6735s

---

### Post by insanity99 on 2009-07-01
i also have no sound after upgrading, i was about to make a thread but saw this one. anything i can do?

EDIT i'm not on a laptop, i am on a computer i built.

---


---
title: "RTL-8169 + SiI 3512 PCI not recognized on 7.04"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by matt1980 on 2007-06-15
Ok, I'm pretty good with Linux, but not so much the hardware side. I've got a combo GigE+SATA card (why? because this SFF system has only two PCI slots) that won't work at all. Mostly concerned with the RTL-8169 GigE at the moment, wanted the SATA for future updates.

The system has an onboard BCM4401 that works just fine, but the new card is not seen at all. Well, sort of. Here's the output from lspci:

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 14)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:0e.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 15)
00:0f.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
00:10.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
00:10.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
00:13.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:13.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
```

...and its missing. However scanpci shows this:

```

[snip]...

pci bus 0x0001 cardnum 0x00 function 0x00: vendor 0x1039 device 0x6325
 Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

pci bus 0x0002 cardnum 0x00 function 0x00: vendor 0x10ec device 0x8169
 Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet

pci bus 0x0002 cardnum 0x01 function 0x00: vendor 0x1095 device 0x3512
 Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller
```

At boot, pcimodules doesn't show r8169 loaded, nor lsmod. I tried modprobe r8169, and then it shows up in lsmod, but nothing new in dmesg or ifconfig. So I'm just kindof poking around in the dark here. Since scanpci sees it (and knows what it is), is there something simple I have to do that I just don't know about?

TIA...

---


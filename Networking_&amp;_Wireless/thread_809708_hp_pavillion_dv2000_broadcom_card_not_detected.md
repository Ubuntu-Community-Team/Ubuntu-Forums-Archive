---
title: "hp pavillion dv2000: broadcom card not detected"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by tk03759 on 2008-05-27
Hello my name's tyler. I just got a new laptop a few days ago. It's an HP Pavilion dv2000, with an AMD Turion64 and a Broadcom BCM4310 wireless card. I've been trying to get the wireless working in ubuntu x32 and/or ubuntu x64 for a few days now with ***no luck at all***.

These are the steps I've tried to get it running through ndiswrapper, unsuccessfully:

> You can download the windows drivers here (these are for a Broadcom BCM 4328 but should work for all the series) then extract the archive in a folder you call broadcom in your home directory.

Install ndiswrapper and follow the procedure:

sudo apt-get install ndiswrapper-utils*

sudo ndiswrapper -i /home/tyler/.broadcom/bcmwl5.inf

sudo ndiswrapper -l

sudo modprobe ndiswrapper

To make ndiswrapper automatically run at each startup:

sudo ndiswrapper -m

modified from this tutorial: [Tutorial for installing Ubuntu on HP Pavillion Laptops]("http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#installing")

Can anyone help me out?

---

### Post by tk03759 on 2008-05-28
Grr... okay so this is night four of being up until 5 trying to get this to work.

I can't really understand what the problem is. I'm using ndiswrapper and I'm using the right driver I think, according to a lot of different websites and the ndiswrapper website.

I installed the bcmwl5.ini file using eithor the terminal or the gui for ndiswrapper, but it tells me that the driver is loaded but the **hardware isn't present**?

lspci gives me this:

```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
04:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

```

any help? i'm so lost. i've done a lot of searching to no affect.

---

### Post by tk03759 on 2008-05-28
Heh well I guess it's just me, but it doesn't even matter. I just fixed it. =)

I did a

```
sudo apt-get remove ndiswrapper ndiswrapper-utils*
```

and then searched my whole computer for ndiswrapper, and used sudo to delete the one folder and file that came up.

Then, I started following a tutorial from: [http://ubuntuforums.org/archive/index.php/t-650729.html](http://ubuntuforums.org/archive/index.php/t-650729.html)

Apparently, despite all being named the same things, none of the drivers I used were correct. The one linked to in that post is the one that worked for me. I reinstalled ndiswrapper and ndiswrapper-utils* and loaded the driver and wham, it said driver loaded and hardware detected, and my wireless worked, just like that. =)

Yay! =D

---

### Post by baronhe on 2008-06-05
I don't know but I have an HP DV2000 especial edition and I tried everything to make it work and yesterday I got a Netgear WPN111 to use wifi and I install the driver for that USB wifi using ndiswrapper and the OS recognize my broadcom wifi, does not turn blue the signal but it work with this driver netwpn11.inf, just follow the instruction to this link [http://www.linuxquestions.org/questi...u-6.06-515914/](http://www.linuxquestions.org/questi...u-6.06-515914/) and I hope this help you I'm not an expert in ubuntu it was just causality and works perfect    :confused::confused::confused::)

---


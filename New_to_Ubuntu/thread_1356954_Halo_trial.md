---
title: "Halo trial"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by The3irikr on 2009-12-16
Hi, i downloaded Halo trial for windows and the installation was perfect, nothing wrong, but when i play it i hear the sound but no screen, like, the screen is all black. I can even move my mouse around and hear the mouse going over the buttons, and i've played the campaign thing but the screen is still black.. HELP!!!
i have a hp pavilion notebook, dv1000. wine version is 1.1.33

---

### Post by n0glu3 on 2009-12-16
Intel graphics?

---

### Post by The3irikr on 2009-12-16
like, i have no idea, but this was a vista before i put UBUNTU on it...so i'm sure the graphics r up to date, but how do i know wat graphics i have?? or turn them on or somehting....idklol

---

### Post by n0glu3 on 2009-12-16
Goto Applications >> Accessories >> Terminal.

Type lspci and press enter.

It will give you a list.

Paste that list back here.

---

### Post by The3irikr on 2009-12-16
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller


yea, i didn't think it would be this big..lol:lolflag:

---

### Post by n0glu3 on 2009-12-16
Sorry you do have an Intel IGP. The Intel drivers for Linux have problems as certain things are not included because they are open source.

---

### Post by The3irikr on 2009-12-16
isn't there SOME way to fix or get this!!! i'm in serious need of killing sprees!

---

### Post by n0glu3 on 2009-12-16
Buy an old Xbox :P

But seriously it depends. There may be a way, but I don't know for certain that it will work.

Feeling lucky? lol

---

### Post by northern lights on 2009-12-16
A. [wine appdb entry]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6978")

B. Does your current setup support direct rendering?
Run ```
glxinfo | grep rendering
```to find out.

---

### Post by The3irikr on 2009-12-17
yes, it said i do have direct rendering.

---

### Post by n0glu3 on 2009-12-17
There may be a way if you use something called driconf.

---

### Post by The3irikr on 2010-02-19
so srry for the really late replay,


yea. What is driconf???

---

### Post by The3irikr on 2010-02-19
ok, so i downloaded driconf from my synaptic.
I open this new thing that appeared called 3d acceleration.. i assume that's it. when i open it. i have no idea what to change.

---

### Post by MC_Sketch on 2010-05-24
hey, im having the same problem! i do have direct rendering, and im not sure if i have the Intel graphics, but i did the test thing you told the other poster, and the results were this
> 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
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
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)if you can, please help me out, i'd really like to play some Halo :D

---

### Post by MC_Sketch on 2010-05-24
forgot to mention im using an Acer Aspire 55536 notebook :)

---


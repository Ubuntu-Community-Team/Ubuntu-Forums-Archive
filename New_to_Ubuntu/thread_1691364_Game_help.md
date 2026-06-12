---
title: "Game help"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by AnnAni1234 on 2011-02-19
I wanted to start playing elderscrolls on my ubuntu machine 
Specs
Intel celeron processer  2.0Ghz
2 GB of ddr1 ram
don't know what graphics card i am running
Dell inspiron 1525

is there a way to check if i can play on my machines virtual box and how would i be able to check wat graphics card i have in linux

---

### Post by uRock on 2011-02-19
Looks like it should play well in Wine. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506)

---

### Post by AnnAni1234 on 2011-02-19
how would i use wine and how would i check what graphics card i am running in my machine

---

### Post by lightningfox on 2011-02-19
I'm not sure how to see what graphic card there is, but to install WINE go to Applications>Ubuntu Software Center and install it from there.

---

### Post by uRock on 2011-02-19
> **AnnAni1234 said:**
> how would i use wine and how would i check what graphics card i am running in my machine

You can install Wine via the Ubuntu Software Center and to find your graphics card enter the following command in a terminal(Applications> Accessories> Terminal) ```
lspci
```

If you can't find which line is the listing for your card, then feel free to copy and paste here using the # sign in the reply ribbon.

---

### Post by AnnAni1234 on 2011-02-19
Here is the out put i cant make heads or tails of it and will it be good enough to play elder scrolls 3 and 4


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by uRock on 2011-02-20
> **AnnAni1234 said:**
> Here is the out put i cant make heads or tails of it and will it be good enough to play elder scrolls 3 and 4


[COLOR=Silver][/COLOR][COLOR=Black]00:02.0 VGA compatible controller: **[COLOR=Red]Intel Corporation Mobile GM965/GL960[/COLOR]** Integrated Graphics Controller (rev 0c)[/COLOR]
[COLOR=Silver][/COLOR]
There it is. As for gaiming quality, i have no systems with Intel chipsets, so I am not sure of the quality for gaming. I did find an Intel manual on the chipset here, [http://www.intel.com/Assets/PDF/datasheet/316273.pdf](http://www.intel.com/Assets/PDF/datasheet/316273.pdf)

---


---
title: "TV Tuner Card"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by augie2051 on 2010-02-14
Greetings I have an "AverMedia" TV card and was wondering if I can set it up in Ubuntu?  I've done a Google search and cant seem to find anything to help me out.  Any advice would be greatly appreciated.

---

### Post by lyall on 2010-02-14
> **augie2051 said:**
> Greetings I have an "AverMedia" TV card and was wondering if I can set it up in Ubuntu?  I've done a Google search and cant seem to find anything to help me out.  Any advice would be greatly appreciated.

see the following link about TV Tuner
[http://manpages.ubuntu.com/manpages/hardy/man4/brooktree.4.html#toptoc3]("http://manpages.ubuntu.com/manpages/hardy/man4/brooktree.4.html#toptoc3")

it is a place to start

good luck and have fun learning

---

### Post by oldos2er on 2010-02-14
Is your card PCI or USB? Accordingly, could you please post the output of either **lspci** or **lsusb** run in a terminal?

---

### Post by lidex on 2010-02-14
This should get you started:
[http://www.mythtv.org/wiki/Category:Video_capture_cards]("http://www.mythtv.org/wiki/Category:Video_capture_cards")

You will, of course, need to know the model, make, etc.

---

### Post by augie2051 on 2010-02-14
> **oldos2er said:**
> Is your card PCI or USB? Accordingly, could you please post the output of either **lspci** or **lsusb** run in a terminal?
PCI

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
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
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
0c:00.0 Multimedia controller: Philips Semiconductors Device 7160 (rev 03)

---

### Post by oldos2er on 2010-02-14
Assuming this is the card (Multimedia controller: Philips Semiconductors Device 7160 (rev 03)), have you tried running an app e.g. Tvtime, or xawtv?

---


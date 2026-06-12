---
title: "My graphics card doesn't work!"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by sweetmiracle on 2009-01-29
Greetings from the ice and snow that is Ohio!

I have a Gateway laptop that is running Intrepid rather well..

until I decided to install World of Warcraft. That's when I found out that my graphics card isn't even on the hardware list:



00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE  Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


There IS a graphics card in there. It's an Intel GMA 950 (with 945 chipset.)

So that's why WoW won't play correctly!

My question is, of course, how do I fix this? I've downloaded a tar.gz driver from Intel for Linux, but it's specific for SUSE, so I'm not sure if it will work. 

Could it be helpful to do a reinstall?

Thanks,

Patti

---

### Post by neurostu on 2009-01-29
So my first question is if Ubuntu isn't recognizing your graphics card then how are you getting a display?

---

### Post by sweetmiracle on 2009-01-29
No clue...

Does it make any difference that it doesn't show up in the list (dumb question, I know.

---

### Post by sweetmiracle on 2009-01-29
It's working on the basic, generic drivers, which don't do much for acceleration...or so I'm told. The drivers that are specific for my card, which usually load automatically on install, didn't load in my case.

---


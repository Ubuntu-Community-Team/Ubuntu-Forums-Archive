---
title: "Output of lspci , I can't see a wireless card here, can anyone else?"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by Siph0n on 2007-09-07
I cant see my wireless card in lspci, but ubuntu definitely finds it because i am online now with it. Any help would be amaing, thanks.

lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

Shawn

---

### Post by revford on 2007-09-07
No, not exactly, I see the Marvell ethernet, but no Wifi.

From a little googling it seems the Marvell 88E8038 PCI-E is often found alongside the Atheros wifi chips, there is a dirver for such a thing here:

[http://madwifi.org/](http://madwifi.org/)

It could help, or it could be a complete dead end.

Hope it helps.

---

### Post by Siph0n on 2007-09-07
Thanks..... the wireless is working fine (without any additional drivers), i was just curious. Also I wanted to look into the Aircrack-PTW program, and I think i need the madwifi drivers (patched) to use it....

---

### Post by noob12 on 2007-09-07
It might sit on an onboard usb.  Does it show up in **lsusb**?

---


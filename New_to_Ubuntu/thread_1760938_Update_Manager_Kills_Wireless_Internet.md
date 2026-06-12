---
title: "Update Manager Kills Wireless Internet"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2011-05-17
I just re-installed Ubuntu 11.04 and had some problems detecting wireless networks to connect to the Internet with.

Here is my hardware:
```
kalayaan001@Kalayaan-MM061:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

So, followed this user's sagely advice:
> **computerandu said:**
> Hi,
Here is what you need to do. Use other Broadcom drivers. Download these drivers (from Windows or through wired network or a friend’s computer or from wherever you are reading this article  ). Install these instead of the one provided by Ubuntu 11.04.

For 32 bit: [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)

For 64 bit: [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb)

Now remove the previous drivers using: sudo apt-get remove bcmwl-kernel-source

Now install the appropriate driver. Restart your computer. If restarting doesn’t work try shut down and then start it (strange…but works). Enjoy 

Source: [http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

Good news is that it worked. After installing his suggested bcmwl-kernel-source (version 5.60.48.36). I can now connect to the Internet wirelessly.
The bad news is that Update Manager keeps pushing me to replace it with version 5.100.82.38, which kills my Internet.

I remember that in Microsoft Windows Update, you can hide specific updates. How can I do this with Ubuntu's Update Manager?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by TeoBigusGeekus on 2011-05-17
Find the package in Synaptic, right click it and select "Lock". Apt won't try to upgrade it anymore.

---

### Post by RedStarYellowSun on 2011-05-17
It worked!

THANKS!!!!!


Take care,
RedStarYellowSun

---


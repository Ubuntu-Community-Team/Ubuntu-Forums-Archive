---
title: "Wireless Not Recognised"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by pixels on 2010-10-02
I've just installed 10.04 on a formatted HP laptop.  It used to run Vista, and wireless was working just fine.

Here's the output from lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```
When previously booted with Vista, the little wireless button lit up.  Now it no longer does this, so I'm assuming ubuntu doesn't recognise the wireless card.

I don't have access to a wired connection right now.  (I do have a usb stick for transferring files between laptops.)

Help?  Thanks in advance.

---

### Post by canthus13 on 2010-10-02
The 4312 should work fine. You'll need to plug in via ethernet and run updates first, and then you should be able to enable the STA driver.  there's more information in [this]("http://ubuntuforums.org/showthread.php?t=1586366") thread.

--Me

---

### Post by pixels on 2010-10-02
> **canthus13 said:**
> The 4312 should work fine. You'll need to plug in via ethernet and run updates first, and then you should be able to enable the STA driver.  there's more information in [this]("http://ubuntuforums.org/showthread.php?t=1586366") thread.

--Me

Thanks.

---


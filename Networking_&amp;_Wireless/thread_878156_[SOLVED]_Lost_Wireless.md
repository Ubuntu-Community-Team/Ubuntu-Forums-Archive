---
title: "[SOLVED] Lost Wireless"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by fballem on 2008-08-02
I had wireless network working on my laptop up until the most recent updates from ubuntu (running 8.04 32-bit). I have a network icon on my panel that used to allow for either wired or wireless network connection. After the latest rounds of updates, I still have the wired connection, but no longer have the wireless connection - I do have a manual connection option that I can't seem to make work.

Any ideas?

---

### Post by Kevbert on 2008-08-02
What's your wireless card chipset ?  If it's Broadcom you may need to update the firmware.  Please post the output of
```
lspci
```

---

### Post by fballem on 2008-08-02
> **Kevbert said:**
> What's your wireless card chipset ?  If it's Broadcom you may need to update the firmware.  Please post the output of
```
lspci
```

output from lspci:

fballem@ballemco-01:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by fballem on 2008-08-02
Somewhere on the forum, I found a reference to an alternate network manager called wicd.

When I installed this, it seems to have corrected the problem. I am assuming that Network Manager was included in the last batch of updates and that seems to have introduced a bug in the wireless network connectivity.

FYI the options that I had available after the last update were wired connection, connect to 802.1 network (which I don't have) or manual configuration. Prior to the last update, I had wired and wireless options.

Hope this helps.

Should I continue with wicd, or is there something else that I should try to get Network Manager working again?

---

### Post by Kevbert on 2008-08-03
I'd stay with what is working.  Congratulations.

---

### Post by fballem on 2008-08-03
Still curious to know what went wrong, but I guess that will be one of life's small mysteries. I'm going to mark this solved, but if someone wants to add to this in the future, that would be helpful.

The link to the wicd that I mentioned is here: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I don't know if I prefer this or not, and I don't know if this will work in all cases, but it did solve my specific problem.

---


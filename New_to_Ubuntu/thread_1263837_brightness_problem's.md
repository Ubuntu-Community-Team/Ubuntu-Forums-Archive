---
title: "brightness problem's"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Uglamugla on 2009-09-11
hello, i'm using ubuntu 8.10 but my brightness is miserable, it's hard to see !

i have a asus m51vr and my graphic is a amd  hd 3470


can anyone help me ?

---

### Post by r.osmanov on 2009-09-11
Did you actually install graphics card driver? 
What does the system output when you go System->Preferences->Display?

---

### Post by r.osmanov on 2009-09-11
To see drivers installed on PCI bus(es) issue the following command:
```
sudo lspci -k
```
And it would be a good idea, if you copy and paste the command output here.

---

### Post by Uglamugla on 2009-11-28
the output it's here, 

jf@jf-laptop:~$ sudo lspci -k
[sudo] password for jf: 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Kernel modules: intel-agp
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Kernel driver in use: uhci_hcd
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Kernel driver in use: uhci_hcd
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Kernel driver in use: uhci_hcd
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
    Kernel driver in use: ahci
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
06:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn
08:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394
08:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
08:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

when i go to system, preferences display it says unknow (in the part of the monitor)
can anyone help me ? i'm sorry for outrageous delay

---

### Post by PRC09 on 2009-11-29
You can try the brightness control keys I believe are FN+F5 and see if that makes a difference,also try System>Preferences>Power Management and check in display. I am using 9.10 but I think the settings are the same...

---

### Post by r.osmanov on 2009-11-29
The issue should be in conflicting drivers, close-source fglrx and open-source radeon

---

### Post by r.osmanov on 2009-11-29
Okay, I see, you have two conflicting drivers close-source **fglrx** and open-source **radeon**:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
Kernel driver in use: fglrx_pci
Kernel modules: fglrx, radeon
```I think the solution is here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Good luck.

---


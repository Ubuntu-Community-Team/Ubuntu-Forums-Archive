---
title: "Identifying hardware?"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by Mercredi on 2009-08-25
Is it possible to find out what video cards, etc, my machine has through Ubuntu? At work I was given a machine with no information as to its specs, and I didn't think to check what Windows Vista thought it had before installing Ubuntu and wiping the old OS.

---

### Post by halitech on 2009-08-25
open a terminal and type
```
lshw
```and it will list everything

---

### Post by x33a on 2009-08-25
try 
```
lspci
lshw -C video
```

---

### Post by scorp123 on 2009-08-25
> **Mercredi said:**
> Is it possible to find out what video cards, etc, my machine has through Ubuntu?  

Shell method:
```
sudo apt-get install hwinfo
```

Once the program is installed, type:
```
sudo hwinfo --all
```

This should spit out a ton of information. If you want to have the output in a text file you can re-direct the output, e.g.
```
sudo hwinfo --all > /tmp/hwinfo_output.txt
```

Other useful tools are lsusb and lspci ... You get them by installing their packages (unfortunately they are not there by default):
```
sudo apt-get install pciutils usbutils
```

To get a nice output of all PCI devices in your system, you'd type:
```
sudo lspci
```

To list all known USB devices (on some laptops the built-in webcam will be listed here too):
```
sudo lsusb
```


Example outputs from my system (a laptop):

```
> sudo lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
**[COLOR="Red"]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)[/COLOR]**
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
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
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 01)
08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 0a)
```


```
> sudo lsusb

Bus 001 Device 004: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 008: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by Mercredi on 2009-08-25
Thank you!

---

### Post by drs305 on 2009-08-25
There is a nice little app called *hardinfo* that gives a nice gui display of hardware and systems.

To install:
```
sudo apt-get install hardinfo
```

To run:
```
hardinfo
```

---


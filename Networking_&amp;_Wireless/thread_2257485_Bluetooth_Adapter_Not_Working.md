---
title: "Bluetooth Adapter Not Working"
date: 2014-12-20
forum: Networking &amp; Wireless
---

### Post by greg0ry on 2014-12-20
I'm trying to get my Bluetooth adapter working. Formerly, when running Windows on this machine, I used a driver from Broadcom's website.

For hardware, there is a single button on the chassis for enabling/disabling wireless. It is in the 'on' state.
The BIOS has no options for enabling/disabling devices.

I'm using a HP Pavilion dm3t with Xubuntu 14.04.1 x86-64, fully updated.
uname -a
```

Linux HP-Pavilion-dm3t-1000 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

When starting Blueman Device Manager 1.23, I receive the following alert:
Bluetooth Turned Off
Bluetooth needs to be turned on for the device manager to function

I then choose the 'Enable Bluetooth' option. The program starts, however, both the 'adapter' and 'device' menus are greyed-out. This process repeats upon exiting and restarting Blueman.

dmesg | grep -i bluetooth
```

[   39.380383] Bluetooth: Core ver 2.17
[   39.380413] Bluetooth: HCI device and connection manager initialized
[   39.380426] Bluetooth: HCI socket layer initialized
[   39.380431] Bluetooth: L2CAP socket layer initialized
[   39.380438] Bluetooth: SCO socket layer initialized
[   39.405275] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   39.405277] Bluetooth: BNEP filters: protocol multicast
[   39.405289] Bluetooth: BNEP socket layer initialized
[   39.445269] Bluetooth: RFCOMM TTY layer initialized
[   39.445290] Bluetooth: RFCOMM socket layer initialized
[   39.445312] Bluetooth: RFCOMM ver 1.11
```

lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218M [GeForce G 105M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

lsusb
```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b182 Chicony Electronics Co., Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

hciconfig returns nothing.

rfkill list
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Along with Blueman, the Ubuntu Software Center lists the following as installed when searching for 'bluetooth':
bluez
bluez-alsa
bluez-cups
libbluetooth3
libgnome-bluetooth11
obex-data-server
rfkilll

Any and all help is appreciated.

---

### Post by greg0ry on 2014-12-31
I finally solved my problem. Marking as such.

---


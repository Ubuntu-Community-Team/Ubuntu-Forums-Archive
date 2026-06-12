---
title: "Intel Centrino Advanced N-6235 Wifi Weirdness"
date: 2014-07-21
forum: Networking &amp; Wireless
---

### Post by WinEunuchs2Unix on 2014-07-21
When the N-6235 (Revision = blank NOT 24) is plugged in to the Mnin PCI-E slot dmesg reports a phantom device every 14.3 seconds:

~$ dmesg -d


```

[28818.060095 <   14.303955>] usb 7-2: new full-speed USB device number 126 using uhci_hcd
[28832.360095 <   14.300000>] usb 7-2: new full-speed USB device number 127 using uhci_hcd
[28846.660122 <   14.300027>] usb 7-2: new full-speed USB device number 2 using uhci_hcd
[28860.960159 <   14.300037>] usb 7-2: new full-speed USB device number 3 using uhci_hcd
[28875.260129 <   14.299970>] usb 7-2: new full-speed USB device number 4 using uhci_hcd
[28889.564131 <   14.304002>] usb 7-2: new full-speed USB device number 5 using uhci_hcd
[28903.868310 <   14.304179>] usb 7-2: new full-speed USB device number 6 using uhci_hcd
[28918.168121 <   14.299811>] usb 7-2: new full-speed USB device number 7 using uhci_hcd
[28932.468094 <   14.299973>] usb 7-2: new full-speed USB device number 8 using uhci_hcd
[28946.768215 <   14.300121>] usb 7-2: new full-speed USB device number 9 using uhci_hcd
[28961.068104 <   14.299889>] usb 7-2: new full-speed USB device number 10 using uhci_hcd
[28975.576240 <   14.508136>] usb 7-2: new full-speed USB device number 11 using uhci_hcd
[28989.672082 <   14.095842>] usb 7-2: new full-speed USB device number 12 using uhci_hcd
[29003.972079 <   14.299997>] usb 7-2: new full-speed USB device number 13 using uhci_hcd



```

Another weird thing is the lsusb command is usually instantaneous but when the N-6235 is plugged in it takes anywhere from 5 seconds to 20 seconds with an average of 15 seconds to generate output.

Speaking of lsusb:
```

~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 007: ID 174c:5136 ASMedia Technology Inc. 
Bus 009 Device 006: ID 0951:1666 Kingston Technology 
Bus 009 Device 005: ID 2109:0812  
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 004: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 008 Device 003: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 008 Device 002: ID 2109:2812  
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I've tested various Kernel versions and with all USB devices / hubs / Expresscard USB 3.0 host controller unplugged.  Same symptoms.

I searched for udev device 7-2 directories but they don't exist, just the normal:

```

/sys/bus/usb/devices/usb7$ ls
7-0:1.0              bDeviceClass     bNumConfigurations  devnum     ltm_capable   removable  urbnum
authorized           bDeviceProtocol  bNumInterfaces      devpath    manufacturer  remove     version
authorized_default   bDeviceSubClass  busnum              driver     maxchild      serial
avoid_reset_quirk    bmAttributes     configuration       ep_00      power         speed
bcdDevice            bMaxPacketSize0  descriptors         idProduct  product       subsystem
bConfigurationValue  bMaxPower        dev                 idVendor   quirks        uevent

```

Finally lspci output, note the N-6235 appears to be original version and not (Rev 24) like most posters have:

```

/sys/bus/usb/devices/usb7$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235
08:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller

```


I'm not sure if the card's n11 is disabled and I have disabled and re-enabled the card's bluetooth to no avail.

Coincidentally the mobo has an Intel Core 2 Duo Centrino T5250 @ 2Ghz.  GME965 Express chipset.

I'm going to order an Atheros AR9287 (Qualcomm put the driver's code right into the Kernel) but would still like to figure out what is going on for educational purposes.  The laptop came with an Intel Wireless 3945 b/g/n (Golan) which works great.

The two dongles I've experimented with RA-Link b/g/n (single stream 802.11N @ 150Mbps) and Net Gear A6200 ac (have to use ndiswrapper around 802.11n windows xp driver) work great in Windows but only ok in Linux.

My long term goal is to find the best Mini PCI-e wifi card for Linux.  Intel might get their microcode/firmware cleaned up and the N-6235 will be the winner but, today it is not.

---

### Post by jeremy31 on 2014-07-22
Does the bluetooth on the card work?  I am used to seeing an intel device in lsusb with the intel wifi/bt cards

---

### Post by WinEunuchs2Unix on 2014-07-22
I assume the bluetooth works because no error messages are reported in dmesg or Kernel log that I've noticed.  I've never had any bluetooth devices.  2 Weeks ago I picked up a MS Wireless 2000 Keyboard & Mouse which uses it's own bluetooth built into a USB transceiver dongle so it doesn't access the onboard bluetooth.

I'd like to order a bluetooth device though.  Any suggestions?

---

### Post by WinEunuchs2Unix on 2014-08-02
I've taken this problem off the table by removing the Intel Centrino Advavanced-N 6235 Half-Mini PCIe Wifi Adapter 802.11 b/g/n and putting back the original Intel 3945 (Golan) Full-Mini PCIe Wifi Adapter 802.11 a/b/g.

Life is good again :D

---


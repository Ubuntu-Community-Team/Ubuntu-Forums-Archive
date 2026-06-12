---
title: "Help with wireless"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by SixStringSoldier on 2010-12-24
I recently installed Ubuntu on a new lap top I received. I've installed ubuntu on two other lap tops and it has worked fine with the wifi, however on this one the wifi doesn't seem to be detected or work. I entered iwconfig in the terminal and this is what it output


alex@alex-Vostro-1520:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

---

### Post by wep940 on 2010-12-24
Please also post the output of the following:
 
lspci
 
lsusb
 
 
These will list all known pci devices and USB devices (even if they aren't working).
 
From there we'll hopefully know what adapter/chipset your laptop has and help you with a driver.

---

### Post by SixStringSoldier on 2010-12-24
> **wep940 said:**
> Please also post the output of the following:
 
lspci
 
lsusb
 
 
These will list all known pci devices and USB devices (even if they aren't working).
 
From there we'll hopefully know what adapter/chipset your laptop has and help you with a driver.

lspci: 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)

lsusb: Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by wep940 on 2010-12-24
Okay, you have a Broadcom 4312 wireless adapter.  The absolute easiest (and best) way to get it working is to do the following:
 
- hard-wire a connection from your laptop to the router so you can get on the internet
 
- open a terminal window and type:
 
sudo apt-get update
 
- then go to System/Administration/Additional Drivers and see if a driver is available for your device - if so, be sure it is enabled.  This may download some things from the net so it may take a little while
 
- physically disconnect the hardwire cable
 
- wait a few seconds
 
- right-click on the network manager icon and be sure "Enable Wireless" is checked and enabled - if not, enable it
 
- left-click on the network manager icon and see if wireless networks show now
 
If you can't do the hard-wire thing, check in System/Administration/Additional Drivers and see if a driver is there - if so be sure it is enabled (it might say something that includes STA in the name or description).
 
If none of the above work, post back and we'll go from there.

---

### Post by SixStringSoldier on 2010-12-25
> **wep940 said:**
> Okay, you have a Broadcom 4312 wireless adapter.  The absolute easiest (and best) way to get it working is to do the following:
 
- hard-wire a connection from your laptop to the router so you can get on the internet
 
- open a terminal window and type:
 
sudo apt-get update
 
- then go to System/Administration/Additional Drivers and see if a driver is available for your device - if so, be sure it is enabled.  This may download some things from the net so it may take a little while
 
- physically disconnect the hardwire cable
 
- wait a few seconds
 
- right-click on the network manager icon and be sure "Enable Wireless" is checked and enabled - if not, enable it
 
- left-click on the network manager icon and see if wireless networks show now
 
If you can't do the hard-wire thing, check in System/Administration/Additional Drivers and see if a driver is there - if so be sure it is enabled (it might say something that includes STA in the name or description).
 
If none of the above work, post back and we'll go from there.

When i entered the command in the terminal a new driver appeared. 
it's called Broadcom B43 wireless driver. however I already had an STA driver. I activated the b43 and still no wireless.

---

### Post by wep940 on 2010-12-26
Try activating the STA driver.  Also, right-click on the network manager icon and be sure "Enable Wireless" shows and is enabled.

---

### Post by SixStringSoldier on 2010-12-26
> **wep940 said:**
> Try activating the STA driver.  Also, right-click on the network manager icon and be sure "Enable Wireless" shows and is enabled.
when I right click to enable the wireless, it's grayed out and i can't click enable.

---


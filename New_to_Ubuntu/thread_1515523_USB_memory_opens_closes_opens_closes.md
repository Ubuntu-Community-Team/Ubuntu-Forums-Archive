---
title: "USB memory opens closes opens closes"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-06-22
I have a 256 meg Dane Elec "flash" or "jump" drive. It has consistently caused minor problems, such as calling Picasa opens the drive for no reason (Picasa is not looking at the drive). I got a new 4-port USB 2.0 hub yesterday. I plugged the hub into the 'puter and then the 256meg drive. It Gnome-Nautilus opened the device properly, at first. Then 30 seconds or so later, it re-opened another Nautilus file manager window. Another 30 seconds go by and another Nautilus file manager window opens.

Before getting the new USB hub, I had the device plugged into a USB 1.1 hub and did not have this problem. Except for Picasa, which, is a nuisance, not a problem.

Output of lsusb is:


Bus 002 Device 002: ID 0a05:7211  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 3538:0054 Power Quotient International Co., Ltd Flash Drive (2GB)
Bus 001 Device 009: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 008: ID 04f9:0028 Brother Industries, Ltd Printer
Bus 001 Device 007: ID 0471:204d Philips 
Bus 001 Device 006: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 001 Device 004: ID 2001:f103 D-Link Corp. [hex] 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 046d:0807 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and a week ago, trying to get Picasa to not open the USB drive, I reformatted it as FAT 32 under Win7 and put the files and directories back in it. I've also done that with GParted, using ext3. No change in the device and Picasa. No other programs seem to care about it (Gourmet Recipe Manager, Adobe Reader, Audacity, Cheese Webcam ... all other USB devices are working without problem: logitech webcam, brother mfc-240c printer, 1gig usb memory stick, bluetooth dongle, IR receiver.

---


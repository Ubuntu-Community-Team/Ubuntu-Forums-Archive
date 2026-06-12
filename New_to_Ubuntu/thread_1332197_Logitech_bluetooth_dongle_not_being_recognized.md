---
title: "Logitech bluetooth dongle not being recognized"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by Automat2 on 2009-11-20
Hi all, 

I am quite new to Ubuntu. I have a Logitech MX5000 keyboard and a MX1000, linked to my PC with the Logitech bluetooth dongle. Strangely enough, both the keybodard and the mouse work as when I used XP, although Bluetooth Manager on Ubuntu tells me that there is no Bluetooth adapter connected to my PC.

I have tried several solutions from this forum but I haven't found any that actually turns Bluetooth on the system.

This is what I get on lsusb, if it's for anybody's help

[PHP]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 059b:0370 Iomega Corp. 
Bus 001 Device 009: ID 046d:c70a Logitech, Inc. MX5000 Cordless Desktop
Bus 001 Device 008: ID 046d:c70e Logitech, Inc. MX1000 Bluetooth Laser Mouse
Bus 001 Device 006: ID 0c45:8000 Microdia DC31VC
Bus 001 Device 005: ID 08bb:2900 Texas Instruments Japan PCM2900 Audio Codec
Bus 001 Device 004: ID 04a9:220e Canon, Inc. CanoScan N1240U/LiDE 30
Bus 001 Device 003: ID 046d:0b02 Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 001 Device 002: ID 050d:0307 Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/PHP]

---

### Post by Automat2 on 2009-11-21
I finally found the solution to my BT problem.

Just look at post #7.
[http://forums.logitech.com/t5/Keyboards-Bluetooth/How-to-use-a-Logitech-BT-Mini-Receiver-as-a-BT-dongle/m-p/768](http://forums.logitech.com/t5/Keyboards-Bluetooth/How-to-use-a-Logitech-BT-Mini-Receiver-as-a-BT-dongle/m-p/768)

Simple, really.

---

### Post by dlodge on 2011-04-14
A synopsis of the solution:

There are two modes the dongle works in, Embedded and HCI. By default the embedded is active, which emulates a USB device so it seems to your PC that your using a normal USB mouse/keyoard.
 
If you hold the little red Button on the USB BT mini-receiver it will enable the other mode. Hold the red button on the BT dongle and plug it into the computer, and after 3-5 seconds of holding the button, the Bluetooth icon will appear in the system tray.

You can then use the adapter as a BT receiver. The adapter continues to work in BT mode after reboots, but I think the occasional BT failure (usually after an update) is caused by the mode changing. I have tried this fix on 10.10 & 11.04.

---

### Post by Blengineer on 2012-03-22
If this wasn't already absolutely clear, (It took me a few tries to get it right) you need to HOLD the red button AS YOU INSERT the dongle and keep holding it until you get a response from your system.

---


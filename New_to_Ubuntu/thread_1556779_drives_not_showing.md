---
title: "drives not showing"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by berdar on 2010-08-19
over the past couple days, i've noticed that my ubuntu isn't showing up my DVD drive, my second internal hard drive or any usb flash or external drives when they're plugged in.   They all show up in the bios boot menu and I can boot from a usb drive.   

When i boot from usb, all my drives show up just fine.  

Is there anything short of a reinstall that will bring my drives back?

---

### Post by lombaardcj on 2010-08-20
Hi,

A few option you can try to identify the root of your problem.

1) Try to look in /media for your external devices after you connected them.

2) Else you can try to run **lsusb** in terminal window and see if any of your USB devices are at least detected.

My output I got after connecting my BlackBerry, and Iomega external HDD through USB port

...$ lsusb
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0fca:8004 **Research In Motion, Ltd. **
Bus 002 Device 003: ID 059b:0277 **Iomega Corp. **
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

3) You can also try to open you Log File Viewer under System -> Administration

When you connect / disconnect any device from your computer, you should be seeing something here.  If not, it means there is something major wrong.

Let me know what happened please.

---


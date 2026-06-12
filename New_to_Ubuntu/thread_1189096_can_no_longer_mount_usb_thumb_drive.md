---
title: "can no longer mount usb thumb drive"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by karasuman on 2009-06-16
One of these last updates broke my ability to mount a usb thumb drive.  I've tested this with different devices, and they all work with other computers (running ubuntu), but nothing I do gets my thumb drive to show up on my netbook.  I googled a bit, and tried something:

```
beth@cheerbear-netbook:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
beth@cheerbear-netbook:~$ sudo modprobe -r ehci-hcd
FATAL: Module ehci_hcd not found.

```

Any suggestions?

---

### Post by LowSky on 2009-06-16
this is with the usb flash drive plugged in?

Are you still using 8.04, something tells me you did a linux kernel upgrade, or tried to use the PC out of hibernate or suspend?

Have you tried rebooting?

---

### Post by karasuman on 2009-06-16
Yes, the thumb drive I'm trying to use is plugged in.  I've tried restarting and cold booting, both with and without the drive plugged in.  I'm using the netbook remix 9.04 with kernel 2.6.28-11-generic.  The only updating I've done is via update manager, and only when prompted.  I have tried this out of suspend, but the problem persists with a reboot, etc.

---


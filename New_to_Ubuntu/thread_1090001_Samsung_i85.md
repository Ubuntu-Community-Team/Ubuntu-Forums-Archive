---
title: "Samsung i85"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by Daemmerung on 2009-03-07
Hi!

I just bought a Samsung i85 and it is not being recognized as anything. I have looked through the other digital camera issue posts and found that I should put my dmesg | tail, which is:
[12393.831692] usb-storage: waiting for device to settle before scanning
[12399.829704] usb-storage: device scan complete
[12405.325137] usb 2-1: USB disconnect, address 6
[12432.228075] usb 1-1: new full speed USB device using uhci_hcd and address 4
[12432.386044] usb 1-1: configuration #1 chosen from 1 choice
[12432.388783] scsi17 : SCSI emulation for USB Mass Storage devices
[12432.429714] usb-storage: device found at 4
[12432.429729] usb-storage: waiting for device to settle before scanning
[12438.430405] usb-storage: device scan complete
[12443.924126] usb 1-1: USB disconnect, address 4

and my lsusb:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I have tried to use f-spot and gtkam, neither could find/import my camera. I also tried different usb ports. I am not using a removable SD card, just the internal memory. If there is anything else I need to do or can do, just let me know.

Thanks in advance!
Daemmerung

---


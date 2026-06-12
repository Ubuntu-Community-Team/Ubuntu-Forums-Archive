---
title: "Webcam trouble"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by IronPirat3 on 2009-09-09
I have a Philips USB webcam and am having trouble getting it to work.
When I type dmesg in terminal, this happens:

[  166.304696] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47pre49
[  166.305337] usb 5-2: SN9C105 PC Camera Controller detected (vid:pid 0x0471:0x0328)
[  166.438260] usb 5-2: No supported image sensor detected for this bridge
[  166.438325] usbcore: registered new interface driver sn9c102
[  270.472067] usb 5-2: USB disconnect, address 2
[  274.096024] usb 5-2: new full speed USB device using uhci_hcd and address 3
[  274.255216] usb 5-2: configuration #1 chosen from 1 choice
[  274.263091] usb 5-2: SN9C105 PC Camera Controller detected (vid:pid 0x0471:0x0328)
[  274.391725] usb 5-2: No supported image sensor detected for this bridge
[  998.368069] usb 5-2: USB disconnect, address 3
[ 1042.296022] usb 5-2: new full speed USB device using uhci_hcd and address 4
[ 1042.459105] usb 5-2: configuration #1 chosen from 1 choice
[ 1042.468530] usb 5-2: SN9C105 PC Camera Controller detected (vid:pid 0x0471:0x0328)
[ 1042.598988] usb 5-2: No supported image sensor detected for this bridge


I have looked around several threads, none of which were really any help.
I tried installing easycam2, but that failed as well.
Any ideas/help on installing the drivers would be greatly appreciated :)

---

### Post by cariboo on 2009-09-09
Could you post the output of lsusb?

---

### Post by karthick87 on 2009-09-09
Try these,

    sudo modprobe -r gspca

    sudo modprobe -r zc0301

    sudo modprobe gspca

---


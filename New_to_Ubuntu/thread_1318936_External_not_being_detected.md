---
title: "External not being detected"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by lanceps on 2009-11-08
I am getting these error from a log file.... my external which used be detected properly is not being detected by my system..... pls help


Nov  8 06:27:06 ubuntu kernel: [ 2464.784051] usb 6-2: new full speed USB device using uhci_hcd and address 7
Nov  8 06:27:06 ubuntu kernel: [ 2464.904030] usb 6-2: device descriptor read/64, error -71
Nov  8 06:27:06 ubuntu kernel: [ 2465.129052] usb 6-2: device descriptor read/64, error -71
Nov  8 06:27:06 ubuntu kernel: [ 2465.345053] usb 6-2: new full speed USB device using uhci_hcd and address 8
Nov  8 06:27:06 ubuntu kernel: [ 2465.465054] usb 6-2: device descriptor read/64, error -71
Nov  8 06:27:07 ubuntu kernel: [ 2465.693057] usb 6-2: device descriptor read/64, error -71
Nov  8 06:27:07 ubuntu kernel: [ 2465.909054] usb 6-2: new full speed USB device using uhci_hcd and address 9
Nov  8 06:27:07 ubuntu kernel: [ 2466.325045] usb 6-2: device not accepting address 9, error -71
Nov  8 06:27:07 ubuntu kernel: [ 2466.437054] usb 6-2: new full speed USB device using uhci_hcd and address 10
Nov  8 06:27:08 ubuntu kernel: [ 2466.853053] usb 6-2: device not accepting address 10, error -71
Nov  8 06:27:08 ubuntu kernel: [ 2466.853074] hub 6-0:1.0: unable to enumerate USB device on port 2

---

### Post by SunnyRabbiera on 2009-11-08
Whats the make and model of your external?
Do you know its format?

---

### Post by lanceps on 2009-11-08
Its a WD and the file system is fat32

its 250 GB

---

### Post by lanceps on 2009-11-08
help

---

### Post by SunnyRabbiera on 2009-11-08
Hmm, odd.
Still on personal advise you may wish to reformat your external to something other then FAT, NTFS if you need windows compatibility or ext3 if you are just using this on linux.

---


---
title: "Please help with usb mouse"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by ddixonr on 2009-05-27
Laptop running intrepid. Touchpad is working fine, but I'd like to install this swiss army, tiny usb mouse. When I plug it in, I can see by the optical light that it gets power, but nothing else. Here might be some helpful outputs:

```
ryan@ryan-laptop:~$ dmesg | tail
[  950.496065] usb 3-1: device descriptor read/64, error -71
[  950.720069] usb 3-1: device descriptor read/64, error -71
[  950.936060] usb 3-1: new low speed USB device using uhci_hcd and address 15
[  951.056080] usb 3-1: device descriptor read/64, error -71
[  951.280075] usb 3-1: device descriptor read/64, error -71
[  951.496055] usb 3-1: new low speed USB device using uhci_hcd and address 16
[  951.904058] usb 3-1: device not accepting address 16, error -71
[  952.016075] usb 3-1: new low speed USB device using uhci_hcd and address 17
[  952.424064] usb 3-1: device not accepting address 17, error -71
[  952.424086] hub 3-0:1.0: unable to enumerate USB device on port 1
ryan@ryan-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ryan@ryan-laptop:~$ 

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

```

Thanks.

---

### Post by ddixonr on 2009-05-27
Don't know how, but it just started working all of a sudden. I'd still like an explanation if someone has one.

---


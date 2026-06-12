---
title: "Bluetooth ressetting randomly on Dell D600 laptop"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by sflinter on 2006-11-29
Hi,

I have installed Kubuntu 6.10 recently on my Dell D600 laptop (which has an integrated Bluetooth receiver).  Occasionally, the bluetooth service appears to start switching off and on again.  This behaviour starts randomly - it doesn't happen all the time.

The messages from /var/log/kern.log look like the following:

```
Nov 29 13:58:01 sflaptop kernel: [17240806.952000] usb 1-2: device descriptor read/64, error -71
Nov 29 13:58:02 sflaptop kernel: [17240807.176000] usb 1-2: device descriptor read/64, error -71
Nov 29 13:58:02 sflaptop kernel: [17240807.392000] usb 1-2: new full speed USB device using uhci_hcd and address 25
Nov 29 13:58:02 sflaptop kernel: [17240807.512000] usb 1-2: device descriptor read/64, error -71
Nov 29 13:58:02 sflaptop kernel: [17240807.828000] usb 1-2: configuration #1 chosen from 1 choice
Nov 29 13:58:03 sflaptop kernel: [17240808.164000] usb 1-2: USB disconnect, address 25
Nov 29 13:58:03 sflaptop kernel: [17240808.660000] usb 1-2: new full speed USB device using uhci_hcd and address 26
Nov 29 13:58:03 sflaptop kernel: [17240808.780000] usb 1-2: device descriptor read/64, error -71
Nov 29 13:58:04 sflaptop kernel: [17240809.004000] usb 1-2: device descriptor read/64, error -71
Nov 29 13:58:04 sflaptop kernel: [17240809.220000] usb 1-2: new full speed USB device using uhci_hcd and address 27
```

There are pages and pages of this stuff.  I've tried restarting the bluetooth service, scanning for devices to no avail.  The lsusb command seems to show that the internal USB bluetooth adapter is not recognised (which matches with the messages above):

```
$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 034: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
```

Any thoughts?

Steve

---


---
title: "pilot-link doesn't work with libusb"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by jtniehof on 2008-08-20
(This is under 8.04.1, ThinkPad R60, Clie PEG-SJ30/U)

I can't seem to get my Clie syncing with libusb:
```
~$ pilot-xfer -p usb: -l

   Listening for incoming connection on usb:... 
~$ 
```
(times out and returns to prompt)

syslog:
```
Aug 20 10:03:34 kernel: [  445.251637] usb 3-1: new full speed USB device using uhci_hcd and address 4
Aug 20 10:03:35 kernel: [  445.417401] usb 3-1: configuration #1 chosen from 1 choice
Aug 20 10:04:35 kernel: [  505.502256] usb 3-1: USB disconnect, address 4
```

(The connect is when I press the hotsync button; the disconnect is when the Clie times out. And yes, this is at the same time I'm running pilot-link...whether I start pilot-link first or press the button first makes no difference.) I also tried uncommenting the /proc/bus/usb lines in mountdevsubfs.sh, then rerunning it to mount /proc/bus/usb...didn't make a difference.

Manually modprobing visor and mknod'ing /dev/ttyUSB[0,1] makes it work using -p /dev/ttyUSB1, but I'd rather be using libusb instead of hacking apart my udev configuration to make it work automatically.

---


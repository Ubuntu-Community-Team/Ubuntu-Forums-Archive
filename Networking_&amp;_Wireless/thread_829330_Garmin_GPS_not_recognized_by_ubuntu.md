---
title: "Garmin GPS not recognized by ubuntu"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by DarkAngel88 on 2008-06-14
Hi everyone,

I have a problem with my Garmin GPS.  When plugging my GPS using the USB port, the system doesn't see it and I'm unable to use it.  Upon further research, I found that it needed to be attached to /dev/ttyUSB0 for gpsd to work.  Running dmesg after plugging my GPS, this is what I see : 

```
[ 9224.609526] usb 2-1: new full speed USB device using uhci_hcd and address 6
[ 9224.764625] usb 2-1: configuration #1 chosen from 1 choice
```

It used to work under 7.10 but now it doesn't work under 8.04.  My kernel is 2.6.24-18-generic.  I'm wondering if there is a way to "force" the mount to /dev/ttyUSB0...  

Thank you !

---

### Post by DarkAngel88 on 2008-06-16
Anyone ?

---


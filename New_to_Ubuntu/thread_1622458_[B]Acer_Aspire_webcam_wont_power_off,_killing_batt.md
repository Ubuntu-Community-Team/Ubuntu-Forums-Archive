---
title: "[B]Acer Aspire webcam wont power off, killing battery time![/B]"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by Darkhorse85 on 2010-11-15
I have been trying for hours to get the webcam to switch off because it uses so much power on battery. I have tried disabling the driver using
```
sudo modprobe -r uvcvideo
```

It just stays on! I have tried blacklisting it as well and this doesn't work either.

Using powertop I can see it is still using power. Here is the relevant part of the output.

> Recent USB suspend statistics
Active  Device name
100.0%	USB device 2-1.5 : 1.3M WebCam (Suyin)
100.0%	/sys/bus/usb/devices/2-1
  0.0%	/sys/bus/usb/devices/1-1
100.0%	USB device usb2 : EHCI Host Controller (Linux 2.6.35-22-generic ehci_hcd)
  0.0%	USB device usb1 : EHCI Host Controller (Linux 2.6.35-22-generic ehci_hcd)


Any help short off cutting the wires??

---

### Post by Darkhorse85 on 2010-11-16
anyone? :-k

---

### Post by ironic.demise on 2010-11-16
Go into System>Preferences see if you can shut it down in there?

---


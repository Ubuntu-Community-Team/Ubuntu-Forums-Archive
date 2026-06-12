---
title: "Ho to check a symlink for a usb medium"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by 151kg on 2011-04-29
Hi there,

I folowed the instructions on [http://wiki.ubuntuusers.de/UDEV](http://wiki.ubuntuusers.de/UDEV) to react to the event of connecting a usb stick.
The udev should create a symlink named "usbmedium2". But I have no clue how to check if it happens or not.

The udev line reads like this:

```
BUS=="usb", ACTION=="add", KERNEL=="sde", SYSFS{idProduct}=="0165", SYMLINK+="usbmedium2"
```The file is named ```
usb-medien.rules
```.

---


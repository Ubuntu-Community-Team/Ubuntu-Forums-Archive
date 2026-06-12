---
title: "Cant write to usb drives"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by tropicaljuce on 2011-05-18
Hi, i have some important files that need to come off the computer so i can upgrade the system. I cant write anything to a USB drive it says:  Error opening file '/media/usb0/BackToOnenessReport.pdf': Permission denied  grateful of anyway of some how saving these files will do, ready for a new install. i dont have my CD drive installed as when i put ubuntu on my comptuer the CD drive was not plugged in. could i install the cd drive or create a new partition on the hard drive? or upload them somewhere? please help

---

### Post by Sidewinder1 on 2011-05-18
Open a terminal and type:
```
sudo chown -R tropicaljuice:tropicaljuice /media/usb0 
```

When asked, input the password that you use to start your system.
The above assumes that your username on the system is tropicaljuice.

HTH, Side

---

### Post by coffeecat on 2011-05-18
> **tropicaljuce said:**
> I cant write anything to a USB drive it says:  Error opening file '/media/usb0/BackToOnenessReport.pdf': Permission denied

The mountpoint /media/usb0 suggest that you installed the package usbmount. If you have, uninstall it and the usb drive automounting built in to the Ubuntu desktop will work properly. The package usbmount is not for use on GUIs - it interferes with the desktop automouting function.

---

### Post by tropicaljuce on 2011-05-18
Thank you both i corrected the problem by uninstalling the package usbmount

---


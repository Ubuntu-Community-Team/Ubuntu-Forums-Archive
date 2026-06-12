---
title: "install to lusb?"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by beelzebufo on 2010-07-27
how would I install to a usb? I have a sandisc 8 gb usb and I am pretty sure it is possible to install to this and just run ubuntu on any of my computers with this, but I am not sure how to do it... apparently I have to reformat, anyway, I am rambling, could someone let me know how to do this?

---

### Post by Paqman on 2010-07-27
You'll need to have a copy of the LiveCD, just like you would if you were going to install to a hard drive. Boot up into it and just choose the USB stick as the target of the install. At the end there will be a screen summarising all the changes it's going to make, with an "advanced" button. Click that and make sure it's going to install the Grub bootloader onto the USB stick, not the machine's hard drive.

---

### Post by wojox on 2010-07-27
You could also boot into BIOS and change the boot order.

---

### Post by 3rdalbum on 2010-07-27
I think you want to use the System > Administration > Startup Disk Creator program; this creates a LiveUSB of the Ubuntu ISO, optionally with some "persistance" space that stores your changes. Then you can run the USB on any computer.

If you just want to use the flash drive on ONE computer, then do a normal install but to the USB drive, and make sure you redirect the bootloader's installation to the USB drive as mentioned above.

---


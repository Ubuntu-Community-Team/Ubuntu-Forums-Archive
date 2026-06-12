---
title: "Change name of USB drives"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by bexpert on 2009-10-06
Could someone tell me how to change the name of a USB drive?

Also, I've plugged a camera card into my laptop, but I'd like to use it as a drive. How do I convince Ubuntu to stop reminding me that it's a camera card? It always wants to launch F Spot.

Thanks.

---

### Post by lavinog on 2009-10-06
Hopefully there will be an easier way to do this in the future.
One way to rename a usb drive is to use gparted.  It isn't installed by default, but you can install it by clicking here: [apt:gparted](apt:gparted)

Launch gparted by going to System > Administration > Partition editor
There will be a dropdown on the right to select the drive.
It will then display the partition map. You can right click on it. If it is mounted you need to unmount it first, then you should be able to select label and change the label.

EDIT: here is guide that says pretty much the same thing: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---


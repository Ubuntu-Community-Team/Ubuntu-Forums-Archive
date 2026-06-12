---
title: "Webcam How-To IBM C-It webcam Xirlink"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-02-13
I have a used IBM C-It WebCam, model: ksx-x9903.  I only want it for Skype.

What, other than Ekiga can be used to test this device? I tried my Skype but it says no device found.

mark@Lexington-19:~$ lsusb
Bus 004 Device 002: ID 0545:8080 Xirlink, Inc. IBM C-It WebCam

and

mark@Lexington-19:~$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory

so I see the usb bus has found it. Maybe /dev/ has no driver for it installed?

I tried the ubuntu community doc for webcams to no avail. ([https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam))

I also read

Model 3 KSX-X9902   

Vendor ID is 0x0545
Product ID is  0x8080
USB Revision   3.01

above from: [http://www.linux-usb.org/ibmcam/](http://www.linux-usb.org/ibmcam/) which says that the driver is in-built in the kernel.

I see 2005/06 posts about this model with bugs, but figure those are "out of date" so, can you give me a url to a how-to for ubuntu & webcams?

---

### Post by newacct on 2009-03-19
try running "sudo modprobe ibmcam"

---


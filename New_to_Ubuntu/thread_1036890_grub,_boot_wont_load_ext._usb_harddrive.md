---
title: "grub, boot wont load ext. usb harddrive"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by jerzydirtracer on 2009-01-11
Hello, I am trying to use an external hard drive, 3.5 reg desktop, with a generic usb case,  it won't recognize or load in gnome, I tried a couple of other hard drives, same thing, but gnome will mount a usb flash drive, so I try to load it when the computer starts, I get an error 

"usb 1-1.4 device description read 64 error-110" with a usb hub,
 and 
"usb 2.0 device description read 64 error-110" directly plugged into usb port

 after the Ubuntu boot screen starts. Could the enclosures be linux incompatle? I set the jumpers on the hard drives as slaves, and as master, the same thing. But funny thing is, Gnome will recognize my 2.5 drive with windows as a usb drive, but will not recognize a drive with linux suse 10.1, even when playing around with jumpers. I am using all separate drives.

Also, if I put the Suse drive in, it boots and loads fine.

---

### Post by taseedorf on 2009-01-12
I have a question.  can you mount the drives manually?

---

### Post by jerzydirtracer on 2009-01-13
I am trying to find out how, and just get gnome to even recognize it so I can either format it or use it.

---

### Post by newbee70 on 2009-01-14
> **jerzydirtracer said:**
> I am trying to find out how, and just get gnome to even recognize it so I can either format it or use it.

have you tried to use gparted check on the drive?

make sure its turned on start gparted, If it finds the drive select it in the device menu, highlight the partition; select partition on the top of gparted, near the bottom is check, click it and then apply on the menu.

---


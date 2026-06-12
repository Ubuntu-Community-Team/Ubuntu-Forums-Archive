---
title: "Can I install ubuntu from the .iso file downloaded on a usb drive?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by newbie1000 on 2008-12-03
My CD writer is broken.

---

### Post by perlluver on 2008-12-03
I would recommend reading this: [http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive](http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive) , and this [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick).  That tells you how to install from a Drive and a Usb Stick.

---

### Post by sportscrazed2 on 2008-12-03
if your boot options gives you usb key as an option i don't see the problem

---

### Post by newbie1000 on 2008-12-03
This is an new 8.1 installation on a windows machine.

Thanks for the help, but I just found out my usb drive isn't big enough.

---

### Post by Shwefty on 2008-12-03
Well, if it's 1 GB or more, you should be alright.  There's the standard USB startup disk option under System -> Administration -> Create a USB Startup Disk.  That creates a USB disk that is kinda like a mobile OS and will take about 4.5 GB, but it's read and writeable.

If you're just looking to make a USB equivalent of the Live CD, I had somebody refer me to Unetbootin.  To install, go to System -> Administration -> Synaptic Package Manager, search for unetbootin, and select it for install.  Select Apply.

Then go Applications -> Accessories -> Terminal.  For the command, type in ```
unetbootin
``` and hit enter.  It'll prompt you for your password.

Find the .iso image you downloaded, and don't forget to check the md5sum as showed on [this page.]("https://help.ubuntu.com/community/HowToMD5SUM")

In Unetbootin, select "Diskimage" - "ISO", and browse to the .iso image save file.  Select the right USB drive under "Drive" at the bottom, hit okay, and wait!  It'll probably format your drive first, I don't remember.

Oh, and I have done this myself.  I have a flash drive (8 GB Kingston) with 8.10 Live CD on there this way...and its install to a computer before (and run w/o install for the trial).

---

### Post by anjilslaire on 2008-12-04
Interesting. I don't see unetbootin in the repos. I have universe & multiverse enabled, too...

---

### Post by Shwefty on 2008-12-04
It's not in Add/Remove, but only under Synaptic Package Manager, check out the attached picture on the post above.

---

### Post by anjilslaire on 2008-12-04
Yeah, its not in th repo's until I added the unetbootin repository:

deb [http://ppa.launchpad.net/gezakovacs/ubuntu](http://ppa.launchpad.net/gezakovacs/ubuntu) intrepid main

---

### Post by Shwefty on 2008-12-04
Touche kind sir!  That's golden info for newbie1000.

---


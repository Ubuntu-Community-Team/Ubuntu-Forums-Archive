---
title: "usb installations"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by beelzebufo on 2010-07-28
I want to check out some other operating systems, but my little laptop cant use dvd+rs I would like to know how to boot things like opensuse and ubuntu studio from my usb... I have a sandisk 8 gb usb, I can't find any way to copy an iso as an image or anything like that

thanks

---

### Post by hhh on 2010-07-28
Unetbootin is the easiest way, you can install via Synaptic.

[http://packages.ubuntu.com/lucid/unetbootin](http://packages.ubuntu.com/lucid/unetbootin)

---

### Post by marshmallow1304 on 2010-07-28
There's also usb-creator, available under System->Administration->USB Startup Disk Creator.  It seems to be a bit less flexible than unetbootin, but it does support creating persistence space to save installed programs, files, and settings from the live session.

---

### Post by beelzebufo on 2010-07-28
well, I tried the unetbootin thing and when I boot from the usb, I get a screen that says boot: then if I type anything, it says invalid kernal file, or something to that effect.  what needs to happen for this to work?

thanks

---

### Post by beelzebufo on 2010-07-28
anybody? please?  I can create a startup usb for any ubuntu based os, but nothing else, and whenever I use unetbootin I get that boot: command line with the kernel error message, any ideas would be greatly appreciated

thanks guys

---

### Post by Jazzy_Jeff on 2010-07-28
I usually download the image file of the distro I want to try out and then run UNetbootin. Tell it where the image file is and it should set it up for you. I use it all the time.

---

### Post by beelzebufo on 2010-07-29
hmmm, I do that and then boot from the usb and just get to the command screen saying boot: do I need to type something in there?

---

### Post by marshmallow1304 on 2010-07-29
Hit Enter at the boot: prompt.

---

### Post by hhh on 2010-07-29
Some ISOs don't boot for me using Unetbootin, even the ones it has in it's download list. You can also try using dd to write the image, though this doesn't work for me all the time either. Sometimes I just have to burn the image to CD, and even then it can fail to boot depending on the hardware you run.

dd is dangerous as it will write to your hard drive if you tell it to. Here are some links...
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles) (see Command Line Interface)
[http://kmandla.wordpress.com/2010/05/02/ubuntu-10-04-desktop-i386-bootable-usb-image/](http://kmandla.wordpress.com/2010/05/02/ubuntu-10-04-desktop-i386-bootable-usb-image/)
[http://en.opensuse.org/SDB:Live_USB_stick](http://en.opensuse.org/SDB:Live_USB_stick)

When using dd, the command is going to be of=/dev/sdX where X is the drive, NOT sdX1 !!!

BTW, I didn't register the part where you said you were trying openSUSE. I just tried writing the openSUSE KDE ISO to USB yesterday via Unetbootin, and it failed to boot. I'm going to try the dd instructions from the last link I gave now, I'll post back...

-edit- That worked for me (except that my hardware fails during boot, the monitor goes to standby, then on, then standby, and never comes back on. Same thing happened when I tried Kubuntu 10.04)

---


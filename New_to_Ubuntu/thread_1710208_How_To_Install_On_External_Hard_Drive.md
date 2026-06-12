---
title: "How To Install On External Hard Drive"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by burnnoticefan on 2011-03-19
Hi, I am newbie to Linux. I have a Win 7 x64 machine.  I would like to install Ubuntu on an external hard drive. I setup a 35gb partition for install. I do not want to install on my C drive. Do not want dual boot system, want to boot Ubuntu from external drive. I would like a simple ABC's of how to do this. Want to make certain it does not install on my C drive. Any help much appreciated!! Thanks

---

### Post by PPPilot on 2011-03-19
HI,

Welcome. I have not tried this but I plan to. This site may be of help:

[HTML]http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/#more-4080[/HTML]

---

### Post by burnnoticefan on 2011-03-19
Hi, Thanks for reply, this thread is to boot from USB flash drive. I want to do a full installation on external 2.0 hard drive. Wonder if Windows Installation in Ubuntu allows to configure where to install.

---

### Post by PPPilot on 2011-03-19
I do not believe Ubuntu will see your USB external drive any differently than a USB Flash Drive. On my system, my USB external drive, USB flash drive, and even my camera with SD card are seen as external drives. Worth a shot anyway.

---

### Post by Naggobot on 2011-03-19
I have not tried hard drive but I did an USB persistent install a week ago.  This is done from system-> administration -> create start up disk. 

You do not want to do this since the maximum persistent file size seemed to be 4 GB.

I also would have liked to make a full install but I did not have time to find out how. 

There seems to be a tutorial for 7.04

[http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/)

Basically the tutorial just advises to install from live CD which seems reasonable and might work with never Ubuntu. There are few extra details worth noting. 

> Point 1: **[COLOR=#FF0000]IMPORTANT[/COLOR]:** Ensure that all internal hard drives are disconnected from your computer during the install (pull your SATA or IDE cables)


and point three which I suspect is done so that the drive is not mounted when inserted. 

Be careful! I guess that point 1 is especially important to make sure that you do not accidentally install over existing installation.

Good luck with any method you may choose to try.

---


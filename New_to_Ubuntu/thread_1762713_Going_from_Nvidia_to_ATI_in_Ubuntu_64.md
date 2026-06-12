---
title: "Going from Nvidia to ATI in Ubuntu 64"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by witofcricket on 2011-05-19
Hi there, this is my first post.

I have installed a ATI Radeon HD5770. I upgraded from an old NVIDIA GEFORCE 8400. 

My machine is running 10.10

When i load up Ubuntu it goes to a text login. It will log in successfully but text only.

I have tried to install in Safe graphics mode but this doesn't load the system at all. 

I upgraded to Natty but the new kernel doesn't load at all! 

Any ideas would be greatly appreciated!!

---

### Post by hhh on 2011-05-19
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English) ?

I got that link from this thread...
[http://ubuntuforums.org/showthread.php?t=1341891](http://ubuntuforums.org/showthread.php?t=1341891)

---

### Post by coffeecat on 2011-05-19
@witofcricket, you need to uninstall the proprietary nvidia driver (if you installed the proprietary nvidia driver) before the ATI card will work at all. The proprietary driver has set up a custom xorg.conf file which is confusing things. You can do this with terminal commands from a console but the easiest way is to put the nvidia card back in, boot up and go to System > Administration > Additional Drivers and disable the nvidia driver. Now shut down and refit the ATI card and boot up again when the system  will now use  the default open source driver. 

Don't install the ATI proprietary driver as hhh suggests just yet. The ATI open source driver is more capable than the open source nouveau driver for nvidia cards, so try the ATI card with the OS driver and see how you get on. It may prove to be adequate for your needs. If you do need to install the ATI proprietary driver, follow hhh's links or simply use the Additional Drivers utility again.

---

### Post by witofcricket on 2011-05-24
[LEFT]Thanks for your help, I did replace my old graphics card and disabled the nvidia drivers. Worked a treat! 
[/LEFT]

---


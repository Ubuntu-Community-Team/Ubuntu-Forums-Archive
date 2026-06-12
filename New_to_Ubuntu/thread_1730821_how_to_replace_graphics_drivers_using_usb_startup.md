---
title: "how to replace graphics drivers using usb startup"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by mkc73 on 2011-04-16
I have just loaded beta version of natty narwhal. System complained that graphics card would not support unity. System came up in "classic mode". I tried activating a different nvidia accelerated graphics driver from
system/additional drivers. On restart gnome no longer comes up i.e hangs in a boot screen.

I can boot up from a usb drive instead. How do I remove the drivers I just loaded on sda1 and go back to the default driver ?

Any pointers appreciated.

---

### Post by mkc73 on 2011-04-16
Oh well. Reinstall it is then.
Many thanks for viewing.

---

### Post by mkc73 on 2011-04-19
I think

sudo rm /etc/X11/xorg.conf 

would have allowed the system to come up with the default graphics drivers.

Interestingly, before removing the accelerated graphics drivers I tried :
 
xinit 

to start up the xserver from command screen and it told me that the external power cable to my graphics board was unplugged and wouldnt allow the accelerated graphics system to start up. I opened the case and the cable was actually unplugged and all worked when plugged in. 

Unbelievable. It must be the first time in 30 years that an error message has told me something that was useful !

---

### Post by mikewhatever on 2011-04-19
Sometimes, running **nvidia-xconfig** is required to make the proprietary driver work properly. You probably can boot and run it from the recovery mode. To remove the driver, use the recovery mode as well. You can check which nvidia packages are installed with **dpkg -l | grep nvidia**, and then remove the ones you don't need.

---


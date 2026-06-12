---
title: "Black Screen"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by harddixk on 2009-01-18
I installed ubuntu 8.10 and it asked me to install graphics drivers. When I did and rebooted i have a black screen. Nothing. Can't even log in. Others say to ron from recovery console. How ??  Cheers

---

### Post by stoogiebuncho on 2009-01-18
What kind of graphics card do you have?  I had the same problem with a Nvidia card, and this is what I had to do to fix it:

> Screen Blanks/Monitor Turns Off

Using a laptop with a GeForce Go card, or connecting the sole display via DVI on a dual-head system sometimes results in the screen not receiving a picture. This is caused by the driver outputting video to the VGA port on the graphics card, instead of DVI.

The usual hint that you have this problem is when you hear the startup sound but nothing appears on the screen. If you do not hear any sound, you are more than likely experiencing unrelated problems.

This is a launchpad bug about displays on digital outputs being blank when using NVIDIA binary driver, and can be resolved by editing your /etc/X11/xorg.conf file:

*

Switch to the console (Try using ctrl+alt+F1, or reboot and select recovery mode from the GRUB menu.)
*

Use your text editor to open /etc/X11/xorg.conf. (try sudo nano /etc/X11/xorg.conf)
*

Find the line that says Section "Screen"
*

Insert a new line that says Option "UseDisplayDevice" "DFP".
*

Save the file. If you had to restart into recovery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart.

If nothing else works and you want to go back to the original settings, you can boot into recovery mode (as described above) and enter

```
dpkg reconfigure xserver-xorg
```

It will ask you a lot of questions about your keyboard, display, and other things.  If you don't know the answer to any of the questions, just use the default answer and Ubuntu provides for you.

---

### Post by harddixk on 2009-01-18
Thanks very much for the quick reply. I will try that, as it seems to be the most logical answer. Cheers

---

### Post by minsf on 2009-01-18
great post. 
just a little typo: i think to recover the xorg.conf file you use "sudo dpkg-reconfigure xserver-xorg" (with a dash)- hopefully you are not going to need it. this method worked for me too by the way.

---


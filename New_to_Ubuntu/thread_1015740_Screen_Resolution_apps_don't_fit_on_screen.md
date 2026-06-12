---
title: "Screen Resolution apps don't fit on screen"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by mazola on 2008-12-19
Hi , am new to Linux. Good experience of Windows / (novell before that) I have installed latest Ubuntu to disk, up and working fine and on wireless etc, problem is the screen res says 800x600 but the apps do not fit on the screen (mozilla etc) H/w and scree res works fine when I boot the mandriva live CD? but wnat to use Ubuntu. 

The PC is a compaq deskpro P3 800mz , the monitor is an LG TV that takes PC input (has been working fine on Windows for years)

(also have a test PC with ubuntu on and all works fine (older PC and Monitor?)

Can anyone advise what I can do to troubleshoot this. 

Apologoes if I have posted in wrong forum or detail is pants. This is my first post, (will learn !)

Thanks

---

### Post by Kobalt on 2008-12-19
Hello,

Try this : open up a Terminal, and enter the following command line : ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This will promt you with the resolutions you want available, make your selection using the spacebar and validate with Enter.
After a reboot, your resolution should be higher.

---

### Post by mazola on 2008-12-19
Thanks for the advice. I tried that  and got the following
***********

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.200812191328

***********

---

### Post by Kobalt on 2008-12-19
Did it work ?
Sorry there was a mistake in my command line (sudo was kept out of the CODE tag), now the code is correct.

---

### Post by mazola on 2008-12-19
Hi, i get the same. the command line i am using is " sudo dpkg-reconfigure -phigh xserver-xorg"  Am I missing something here.

thanks

---

### Post by linux_tech on 2008-12-19
If you type ```
 xrandr
```
         you can see if a better resolution is available or not.

---

### Post by mazola on 2008-12-19
hi,  xrandr output is as follows. 
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0 

800X600 is current setting but all app windows are to big . 

thanks

---


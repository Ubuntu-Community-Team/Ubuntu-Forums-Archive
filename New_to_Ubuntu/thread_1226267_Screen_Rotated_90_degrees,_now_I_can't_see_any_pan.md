---
title: "Screen Rotated 90 degrees, now I can't see any panels"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by hitekwaiter on 2009-07-29
I was playing around with Configure Display settings with my newly install Ubuntu 9.04 machine. I have to monitors and the ATI card has an analog and digital output. But I can only get it to display to the digital output. I resigned myself to this and only had my digital montor hooked up. I played about with Config display settings & the screen rotated 90 degrees but I cannot get to any control panels or icons to change back. 
silly, really.

Please help if you can.

---

### Post by Mark Phelps on 2009-07-29
If you can open a terminal, you can enter the command "xrandr --rotate left" to rotate your desktop 90 degrees to the left (presuming you rotated it to the right in the first place).

---

### Post by pedro3005 on 2009-07-30
If you can't seem to open a panel, reboot your PC. While on the GRUB menu screen, select safe mode, then select Get a Root Terminal (or something like that). Then, run ```
 cd .. 
``` twice until you are on the base of the file system. Run ```
 cd etc/init.d 
```Now run ```
 echo xrandr --rotate left > anythinglol 
```Now, the command indicated by *Mark Phelps* will be executed on bootup, if I'm correct :)

---


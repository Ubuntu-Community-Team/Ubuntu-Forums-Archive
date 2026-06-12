---
title: "Change autoboot"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by Yuchiras on 2011-08-03
[SIZE=3][FONT=Arial]Hi, 

I am using Ubuntu 11.04 and I want to **change my boot order** (put win 7 first). I checked other posts and I have tried
 
gksudo gedit /boot/grub/menu.lst 

but all I can see is a blank page. I don't know if it is normal. I apologise if someone already posted this and I am new to Ubuntu. 

Thank you in advance for helping.[/FONT]:D
[/SIZE]

---

### Post by cbennett926 on 2011-08-03
When you start up your pc strike whatever key sends you to the boot menu and I am pretty sure you can edit the boot order from there.

---

### Post by EkuquoL on 2011-08-03
Most computers have a "F" key to show the bootloader. I think it is F8 or F6 ... You can press that at computer statup too display all available boot routines.  You can also press Pause Break and it will halt system load so you can read the screen.

Also.. Tht isn't where the header is at....

It would be in the
etc/grub/ folder.

---


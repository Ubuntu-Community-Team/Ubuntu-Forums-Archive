---
title: "Black screen"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by Shadow99 on 2010-07-07
I just got a new toshiba laptop that had windows 7 but I wanted to replace that with Ubuntu 10.04 64 bit instead and I then encountered many problems. Well first I got the video card problem where whenever I booted to the Ubuntu disc, picked my language and clicked any option. I'd get the black screen of death and have to restart! So then I tried to run the disc in noapic, nolapic, and nomodeset. Which then let me install and it said the install was successful but then it black screened again! So now I can't run windows 7 or ubuntu since my computer didn't come with a windows 7 disc and now the ubuntu disc won't work anymore either since now a I/O error box pops up if you click on any of the disc options. PLEASE SOMEONE HELP ME!!! D':

tech specs
------------
intel core i-7 processor
nvida Gforce vid card
4G of DDR3 RAM
500G HD

---

### Post by overdrank on 2010-07-07
> **Shadow99 said:**
> 
------------
intel core i-7 processor
nvida Gforce vid card
4G of DDR3 RAM
500G HD

Hi and welcome. Are you able to boot into recovery mode at the grub?
When you see the grub loading press esc key and you should see the grub list. Then you can choose recovery mode which is usually the second on the list.

 I believe you can choose fail safe graphics or reconfigure the graphics. Hopefully this will get you to the desktop where you can install the drivers for the graphics.

Moved to Absolute Beginner Talk

---

### Post by Shadow99 on 2010-07-07
sorry i am unfamiliar with grub, does that pop up before the installer menu?

---

### Post by davidmohammed on 2010-07-07
when booting - just after th bios message - press and hold shift.  This will display a list of kernels - this is your grub.  Now press e and find the line with quiet splash

add your boot options before quiet splash

i.e.

... nomodeset noapic nolapic quiet splash --

then press ctrl + x to boot.

---

### Post by overdrank on 2010-07-07
> **Shadow99 said:**
> sorry i am unfamiliar with grub, does that pop up before the installer menu?

I am sorry, I thought Ubuntu was able to install according to your first post.
Are you still using the live cd?

---

### Post by Shadow99 on 2010-07-07
all that seems to do is ask "load boot graphics(y/n)?"

---


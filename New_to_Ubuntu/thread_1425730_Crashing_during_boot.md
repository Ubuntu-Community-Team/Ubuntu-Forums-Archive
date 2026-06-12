---
title: "Crashing during boot"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by browny254 on 2010-03-09
Hi i have a real big problem in that when i try to boot up into ubuntu or kubuntu it seems to stall and not do anything. Usually when i power up it boots automatically but now it loads grub where i have tried every option (linux 2.6.31-20(19, 17, 16, 15, 14)-generic) in both regular and recovery mode. In regular mode it freezes on the kubuntu loading splash screen with my caps lock light flashing. In recovery it freezes at /sbin/init: relocation error: /sbin/init:symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
Then it has 13 lines of numbers and other stuff. The caps lock light is also flashing.

Any help in what i can do? I seem to have lost my install disk so i cant do a fresh install but i have the iso on a usb hard drive so if it is possible to burn another disk somehow i can do that.

I dont have any other computers except my phone which im using now so any help will be really appreciated. Cheers.

---

### Post by ikt on 2010-03-09
Heya,

You're up early for perth ^^

> iso on a usb hard drive so if it is possible to burn another disk somehow i can do that.

Do you have a spare empty usb drive? 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you do pretty much plug it in then head the system menu > administration > usb startup disk creator > and just chose the iso and your usb drive and then you have yourself a boot drive.

Just need to choose to boot off the usb when booting up and you can reinstall, this is pretty much how I do all my installations these days.

The blinking caps lock like is a sign of a kernel panic, which is.. not good..

Hope you are able to solve your issues :) (btw check out the link in my signature ;) )

---

### Post by browny254 on 2010-03-09
Not up early, still up late :)

Thanks for the advice for the usb live disk, will do that in the future but i cant get ubuntu to load at all so i was hoping there was someway else of doing it

---

### Post by undecim on 2010-03-09
Do you have other kernel options from grub? (i.e. more than one normal and more than one recovery mode option)

If so, try one of those.

---

### Post by browny254 on 2010-03-09
Yeah i have 6 kernels and each freezes at the exact same spot

---

### Post by browny254 on 2010-03-09
Ive attached a photo (i hope) of where it crashes incase that helps. I only have access via my phone atm so im not sure if i can include much more.

---

### Post by ikt on 2010-03-11
[http://www.linuxquestions.org/questions/linux-kernel-70/kernel-panic-not-syncing-attempted-to-kill-init-313273/](http://www.linuxquestions.org/questions/linux-kernel-70/kernel-panic-not-syncing-attempted-to-kill-init-313273/)

Might want to run a memory test.

---

### Post by browny254 on 2010-03-12
Thanks for the reply again, I ended up getting a friend to burn me new instal disk anddid a fresh install so no longer have the problem, and dont know how to fix it either...

---


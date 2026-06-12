---
title: "via unichorme driver"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by paulthomas07 on 2010-06-06
I recently installed Ubuntu 10.04 on my old desktop machine, the machine specifications are given below


[LIST=1]
[*]processor AMD ATHLONL XP
[*]motherboard A7V8X-MX SE
[*]Chipset VIA KM400
[*]Memory 256
[*]integrated VIA UniChrome Graphics
[/LIST]
i am having problem with the display as i am not able to get the right driver for ubuntu 10.04
pls help me in getting the VIA unichrome driver and installing it as i am new to ubuntu and i am not a computer geek

---

### Post by roger_1960 on 2010-06-06
Hi

If your problem is that you cannot enable desktop effects, then I think you are out of luck.  There is no 3d driver for that chipset which works in linux (afaik).  I have a laptop with the same and have given up looking now.

If its a resolution problem, we need more info

---

### Post by cascade9 on 2010-06-06
AFAIK, the right driver is xserver-xorg-video-openchrome- 

[http://packages.ubuntu.com/lucid/xserver-xorg-video-openchrome](http://packages.ubuntu.com/lucid/xserver-xorg-video-openchrome)

It should be working out of the box. ;)

---

### Post by roger_1960 on 2010-06-06
Hi again

Bizarre that I've not found that before!  I'll try it too...

---

### Post by paulthomas07 on 2010-06-07
xserver-xorg-video-openchrome- this package is already installed and the  graphics are not getting

---

### Post by roger_1960 on 2010-06-07
Hi again

I have also got this installed, and have specified it in xorg.conf as the device driver and I still cant enable any desktop effects.  I think my first view in posr #2 was correct.....

---

### Post by cascade9 on 2010-06-08
> **roger_1960 said:**
>   I think my first view in posr #2 was correct.....

+1. I really doubt that desktop effects are going to be possible from VIA Unichrome.

---

### Post by anewguy on 2010-06-08
I used to have a cheap Gateway laptop with a Via Unichrome Pro in it.  I went through a lot of work then getting the openchrome drivers working, and there was a patch you had to manually make to one of the files for the 3D driver to even try to work.  Alas, the Via Unichrome cannot run desktop effects.  To see exactly why, try "compiz --replace" in the command line - you'll see it doesn't support some of the things needed by compiz.

Dave ;)

---


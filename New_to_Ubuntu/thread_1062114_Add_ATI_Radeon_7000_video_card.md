---
title: "Add ATI Radeon 7000 video card"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by tk05 on 2009-02-06
Please put in plain English, how do I install an ATI Radeon video card in my Ubuntu system. I am already the system with the on board and love the OS. I am not good at using Ubuntu yet, I am at the playing with it stage. 
I do not have a driver disk. I have tried looking for linux versions of the drivers, but no luck, just windows versions. I tried inserting the card and booting, but it comes up with it is running in low resolution mode and then I end up with brown bars across the screen. I was using the built in video, but I need DVI for the new monitor. If it helps at all I am currently using a 17 inch CRT monitor.

---

### Post by overdrank on 2009-02-06
> **tk05 said:**
> Please put in plain English, how do I install an ATI Radeon video card in my Ubuntu system. I am already the system with the on board and love the OS. I am not good at using Ubuntu yet, I am at the playing with it stage. 
I do not have a driver disk. I have tried looking for linux versions of the drivers, but no luck, just windows versions. I tried inserting the card and booting, but it comes up with it is running in low resolution mode and then I end up with brown bars across the screen. I was using the built in video, but I need DVI for the new monitor. If it helps at all I am currently using a 17 inch CRT monitor.

Hi and welcome, when you install the graphics card you will need to boot into recovery mode which is usually the second choice from the grub. 
You will be given 4 choices and you need to choose the xfix option. This will hopefully configure your graphics.
Then you should be give the option to boot normally after the xfix. Hope this helps good luck. :)

---

### Post by tk05 on 2009-02-06
Thanks, that solved my problem!

---

### Post by Ross_and_Eye on 2009-12-27
> **overdrank said:**
> Hi and welcome, when you install the graphics card you will need to boot into recovery mode which is usually the second choice from the grub. 
You will be given 4 choices and you need to choose the xfix option. This will hopefully configure your graphics.
Then you should be give the option to boot normally after the xfix. Hope this helps good luck. :)

How do U Restart in Recovery mode?  And what is a "grub" Please?

---

### Post by Miljet on 2009-12-27
You really should have started a new thread. This one is almost a year old.

GRUB stands for GRand Unified Boot loader. It is what gives you the menu that allows you to boot into Ubuntu or Windows.

When the GRUB menu displays, the second option from the top will take you into recovery mode.

---

### Post by Ross_and_Eye on 2009-12-28
Thanks Miljet, how do I make that menu appear during boot?

---

### Post by ovid9 on 2009-12-28
After your BIOS screen pops up, it will say GRUB is loading and a countdown of 3....2....1... and say hit escape to enter GRUB menu.
 
At that point, hit escape and into the menu you go.

---


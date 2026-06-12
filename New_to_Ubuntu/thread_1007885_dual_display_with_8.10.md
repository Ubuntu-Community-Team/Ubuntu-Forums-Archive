---
title: "dual display with 8.10"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by moose12 on 2008-12-10
i was using 8.04 and plugging my laptop into a docking station that i keep a projector plugged into. with 8.04 it auto mirrored the screens and didn't screw up my picture on the actual laptop. but after upgrading to 8.10 the mirrored screen feature messes up the size of everything on my laptop. the projector has 800x600 display. ideally id really like to make it a side by side style dual display, but i would settle for mirror screens if i can get the size to stay normal on my laptop screen. when i tried to do the dual display it always makes the projector the primary screen (this caused some trouble before actually turning the projector on lol). i want my laptop to have 1200x800 resolution and the projector to function like a dual display monitor. i will settle for mirror screens if thats my last resort though.

---

### Post by moose12 on 2008-12-10
im trying to extend my monitor onto a projector but it keeps making the projector the primary display(has the tabs and such). when i use mirror screen it works sort of, but it cuts off part of the screen on my laptop. mirror screen didnt do this with 8.04 but this started when i upgraded to 8.10. any ideas?

---

### Post by cdmike2k8 on 2008-12-10
Try not to double post. What type of a graphics card is it?

---

### Post by moose12 on 2008-12-10
sorry everyone seemed to be ignoring the previous post. and its an intergrated chip from intel.

nathaniel@nathaniel-laptop:~$ lspci | grep Graphics00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

i read a post about using the xrandr commands and ran this

nathaniel@nathaniel-laptop:~$ xrandr --output VGA --mode 1024x768 --right-of LVDS

though it still made the projector the primary screen

---

### Post by moose12 on 2008-12-11
still need an answer

---

### Post by overdrank on 2008-12-11
Please be patient, I have not had a chance to use the intel graphics with 8.10 and others may have not also. May I ask if Hardy 8.04 was working, why upgrade. Just curious :)

Threads merged

---

### Post by moose12 on 2008-12-11
ok i didnt mean to seem impatient i was simply trying to put it back on top with the new posts.

---

### Post by moose12 on 2008-12-15
i wiped the computer and reinstalled 8.04 so im back and in good shape!

---


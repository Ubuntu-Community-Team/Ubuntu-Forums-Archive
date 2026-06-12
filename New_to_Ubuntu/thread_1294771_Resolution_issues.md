---
title: "Resolution issues"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by Jam_tart on 2009-10-18
I have just got ubuntu and i have changed the display settings so i can see barly anything and i cant change it back because the bottom of the display options window is cut off. What should i do?

---

### Post by howefield on 2009-10-18
You might be able to press the alt key, and left mouse button and drag the window so you can see the part you need.

---

### Post by Jam_tart on 2009-10-18
Nope you can only move the window left right or down and i need to move it up but thanks anyway

---

### Post by sandyd on 2009-10-18
use the tab key.

---

### Post by GregBrannon on 2009-10-18
Can you resize it from the top (squish it flatter) and then move it up?

---

### Post by nigel_nb on 2009-10-18
u cud use tabs to go to the next button

---

### Post by user333 on 2009-10-18
I did that once, but I don't know how I fixed it. :( I might have had to re-install, but I am guessing you don't want to do that. You might be able to do this though: (if you mess somthing up, I am not responsible. I am warning you. Only do this if you can't do anything else, and you are not afraid of losing data.)

Open a terminal. You will find it in the accessories folder of the applications menu.

cd to /etc/X11

> cd /ect
cd X11Then type:

> gedit xorg.confThen figure out where the 600x400's are and try to figure out which on you should make into 800x600. Please, be **CAREFUL**!!! I an not sure what to change, because I am guessing you don't have the same video card, or if you do, probably not the drivers. I hope you are able to fix your problem ;)

---

### Post by Xatolos on 2009-10-18
Assuming you can't see anything, this is a blind way to reset your screen res.

Press Alt-F2 which will bring up the Run Application box. Then type gnome-display-properties and press the Tab button 6 times and press Enter. 
*Edit* If you have a card with its own drivers like NVidia, you'll need to press the Right button here and then Enter, otherwise ignore this step.
This will bring up the Display options. Press Tab 3 times and that will be the Screen Res option, and press the Down button a few times which will select a smaller screen size. Press Tab 3 more times and press Enter again to select Ok. Now you should have a smaller screen Res and be able to set it to a more better size.

---

### Post by user333 on 2009-10-18
**Wait!!!! **Here is how to do it, risk free!!!!

Press [ALT][A] after you select the resolution you want!!!!

NO risk involved. A command is used like this if you can't use the mouse. The button will have a underline of the thing to want to "click".

---

### Post by halitech on 2009-10-18
what video card do you have and have you installed any drivers for it?
```
lspci
``` if you don't know

---


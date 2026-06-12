---
title: "Screen Size Problem"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by yellowdog1000 on 2011-08-25
My issue is that the Ubuntu install created a screen size that is slightly larger than my physical screen size. The result is the very bottom of the main desktop is out of view. This is not a screen resolution problem, this is a display size problem. My mouse will track off screen at the bottom. I have an HP Mini. I suspect that I need to set some parameter(s) in X11 or gnome but I have no idea of the proper file or setting. Any ideas?

---

### Post by snip3r8 on 2011-08-25
Does your Screen have an autosize option?

---

### Post by yellowdog1000 on 2011-08-25
Sorry, I do not know about autosize. How does one check - where are the files or what are the commands?

---

### Post by tzily on 2011-08-25
autosize options are for tv's only as far as i know

have you tried changing the gksudo nvidia-settings ?
try an auto resolution or panning from advanced from xserver display configurations / also in DFP-0 check if you have scaling and set it to stretch or something

---

### Post by snip3r8 on 2011-08-25
> **tzily said:**
> autosize options are for tv's only as far as i know btw

have you tried changing the gksudo nvidia-settings ?
try an auto resolution or panning from advanced from xserver display configurations / also in DFP-0 check if you have scaling and set it to stretch or something

my Samsung BX2031(monitor,definately not tv) supports autosize(aka auto adjust). and practically every LCD monitor ive seen.

---

### Post by tzily on 2011-08-25
> **snip3r8 said:**
> my Samsung BX2031(monitor,definately not tv) supports autosize(aka auto adjust). and practically every LCD monitor ive seen.

oh, weird. i dunno, because i've upgraded from laptop lcd straight to lcd-tv... but then again, laptops as in this case mini, don't have buttons and settings for the screen, therefore no autosize/aspect ratio options ;)

---

### Post by realzippy on 2011-08-25
The autosize option is in your LCD-TV's menu,not in your ubuntu.

---


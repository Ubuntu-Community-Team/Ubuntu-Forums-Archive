---
title: "Howto: Geforce2 drivers"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by SomeJavaDeveloper on 2011-07-10
Hello,

i recently installed ubuntu 11.04 desktop on an older machine. The machine has got a soundblaster Live Premium audio card, and a Geforce 2 video card.

I tried to install the drivers (nvidia current) but this freezes the machine. It starts up, and then when the Ubuntu logo comes up, it stays on that screen and freezes completely.
I have to boot from the recovery disk and remove the Xconf settings file in the X11 directory.

Is there any way to activate this graphics card propertly?

---

### Post by SomeJavaDeveloper on 2011-07-11
Is there anyone else who has managed this configuration, or am i wasting my time here?
The machine itself has 512MB ram, so the ubuntu itself runs fine.
It's a pitty I have to watch this flickering screen on an old 21 inch monitor.

---

### Post by CatKiller on 2011-07-11
nvidia-current doesn't support a card that old. I think you want one of the older ones. There used to be an nvidia-legacy for older cards but I think they just list the version number these days, since their segmentation got confusing. It's probably nvidia-96 that you want.

---

### Post by wildmanne39 on 2011-07-11
Hi, so true I have an older nvidia card mine is a 6150, I have to use the 173 driver, these drivers are a little picking in natty.

---

### Post by Terl on 2011-07-11
You may want to check compatibility lists as Xorg has discontinued support for many older graphics cards.  What model card do you have?

---


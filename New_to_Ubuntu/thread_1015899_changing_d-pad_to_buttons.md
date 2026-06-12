---
title: "changing d-pad to buttons?"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by miniyak on 2008-12-19
original title: changing d-pad to buttons?

heres my situation- i play stepmania, a rhythm game that uses a dance pad for the control. The dance pad is for a PS2, however i have a PS2 to usb adapter so i can use it on my desktop.

problem- everything works fine except for one thing. In the game the d-pad needs to be recognized as buttons or else useful game play is compromised. The d-pad is recognized as an x and y axis (so left and right can't be pressed at the same time, for example) My adapter does not have the cool button code to switch into "dance pad mode" unfortunately (though i could try again to see it magically works). Any possible solutions would be great, though i dont really want to get a new dance pad, out of fear of having the same problem.

ive been looking for a good solution to this problem for a while, with very little, but some convoluted answers. keep in mind i have very little to no experience editing config files but am willing to do so. (i only edited the bootloader once via copy and paste from forums)

update: i just found a better solution to my problem at stepmania.com. This is from the site: 

" Linux Workaround without Messing with the Kernel

If you fear recompiling your kernel, for some controllers you can recompile StepMania instead to use a special hack - see [http://pasky.or.cz/~pasky/dev/stepmania/3.9/](http://pasky.or.cz/~pasky/dev/stepmania/3.9/)

This workaround works at least for the DragonPlus PS->USB converter. "

this should work for me because the input on my controller show up as 127 when left and right/ up and down are not pressed and 128 when there simultaneously pressed, this work around apparently exploits this fact by recompiling stepmania to account for that. so only one question remains, how do i recompile stepmania?

---


---
title: "broken volume dial on toshiba laptop"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by jtofu on 2008-12-17
volume control on toshiba laptop broken
hello,

i've recently made the switch to linux after about ten years of thinking about it. i really like it a lot. recently, i upgraded from hardy to intrepid. with the upgrade, i've lost control of my volume dial on the side of my toshiba u300 laptop.

when i try to turn up, or down, the volume with the dial, it seems to repeat the volume adjustment. this makes the speaker icon pop-up on the screen and flash on and off. this also makes me loose control of my mouse buttons.

i think i found a fix here: [http://lists.freedesktop.org/archive...ne/036373.html](http://lists.freedesktop.org/archive...ne/036373.html) but i don't how to implement it.

could someone help me with a walk-through? or tell me if the above will even work?

thanks,

tofu

---

### Post by Hospadar on 2008-12-17
It looks to me that you'd need to recompile something (the post is not very descriptive as to what exactly, certainly not in the context of ubuntu)

You might try asking on the mailing list that you found the solution and see if they can help you figure out what you need to apply the patch to and how to re-build whatever package it belongs to (my guess would be xserver-xorg).

[http://lists.freedesktop.org/archives/xorg/2008-June/036373.html](http://lists.freedesktop.org/archives/xorg/2008-June/036373.html)

---

### Post by jurusu on 2009-10-30
Still not working in my U300 using Karmic. :(
!Help. Thanks!

EDIT: I managed somehow to disable the volume dial and reassign the control to other keys.

[http://swiss.ubuntuforums.org/showthread.php?t=1010409](http://swiss.ubuntuforums.org/showthread.php?t=1010409)

---


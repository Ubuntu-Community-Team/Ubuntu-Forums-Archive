---
title: "Dual booting without screwing anything up"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by XKCD64 on 2009-09-20
How do I dual boot?  I have XP and want to put Ubuntu on a hidden partition that my mom wont find accidentally.  Like I have to press a certain key at start up? 

Any way, how do I do this without screwing anything up?  It needs to be risk free!  :P

---

### Post by Liolikas on 2009-09-20
Ubuntu ext3/4 is quite well hidden and impossible to see from windows XP without drivers instalations looks like C; become smaller. 

Problem may be grub menu but you can set up its time to something like 1 second and winXp default so notice hardly possible.

You can proceed with normal install just DAMN BE SURE not to delete windows!!! Shrink partition and use free space.

Also learn about /boot/grub/menu.lst file all that is possible. Forums full or info google too. You will learn how to hide menu well and default options to XP.

+++++++++++++++++
Also consider virtual box if you have powerful PC.

---

### Post by nhasian on 2009-09-20
the new Karmic Koala 9.10 comes with Grub2, and you can set it so that the grub boot menu only shows up when you press ESC.  Otherwise it will just start the default operating system.

---

### Post by Liolikas on 2009-09-20
Detailed info with screenhots;
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)
Actually very easy but better read than risk mess thigs up.
Here KEY point:
[http://www.psychocats.net/ubuntu/images/dualboot09.png](http://www.psychocats.net/ubuntu/images/dualboot09.png)

---

### Post by Liolikas on 2009-09-20
> **nhasian said:**
> the new Karmic Koala 9.10 comes with Grub2, and you can set it so that the grub boot menu only shows up when you press ESC.  Otherwise it will just start the default operating system.
Current grub can do this too!
GRUB2 actually just look much more cool (not like XX stuff) and have boot from iso and nothing else really new.

---


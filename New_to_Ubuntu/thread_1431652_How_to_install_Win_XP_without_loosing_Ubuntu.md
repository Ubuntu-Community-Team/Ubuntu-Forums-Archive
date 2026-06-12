---
title: "How to install Win XP without loosing Ubuntu?"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by Saito Chikara on 2010-03-16
Okay...

The games I want to play require XP and have no Linux support, so I want to install Windows XP on my computer now, but I'm afraid to break something.

How can I have Windows XP and Ubuntu in a dual-boot, without loosing any key bits of Ubuntu?

I am hoping ot give this a go ASAP, so a quick reply would be great.

Thanks!!

---

### Post by zvacet on 2010-03-17
With your Ubuntu live CD or with [Gparted live CD]("http://gparted.sourceforge.net/") shrink Ubuntu partition,and on that free space install XP.[Reinstall grub.]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2")

---

### Post by aeiah on 2010-03-17
yea basically all you've gotta watch out for is grub disappearing. windows will overwrite it, and you just need to write it back. during an xp installation you'll have the option to choose which partition to install the OS to. just make sure you know which one's which by making a note of the size whilst you're resizing things in gparted.

---

### Post by julio.tomaschitz on 2010-03-17
well, I dont know a way to do this without losing grub. I think the best way is install windows, then repair grub using a ubuntu live-cd, is very simple. Take a look on google, expressions like 'grub recover'. It's something like this:
grub
root (hd0,x)
setuo (hd0)
quit

where 'x' is the grub's partition number, plus 1 (always 1).

---

### Post by waynefoutz on 2010-03-17
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

That guide will get the job done on the Karmic. You'll need a 9.10 live CD. Karmic, and I think Jaunty, use grub2, which is what this guide is for.

---


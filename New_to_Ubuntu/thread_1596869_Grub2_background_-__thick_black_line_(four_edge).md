---
title: "Grub2 background -  thick black line (four edge)"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by EgoGratis on 2010-10-14
Is this normal and why is it normal. And if it is possible to correct the "issue". If i set Grub2 background image and set custom screen resolution. 

I get black edge around the image. Few pixels wide line.

Is it possible to correct this and to have Grub2 background image on all available monitor work space? Monitor native resolution, Grub2 setting and image dimensions are all the same.

Thanks for answers!

---

### Post by andrewthomas on 2010-10-14
The image is the exact same size as the screen resolution?

---

### Post by EgoGratis on 2010-10-14
Yes.

---

### Post by EgoGratis on 2010-10-14
I found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/567226](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/567226)

[http://twitpic.com/1h1d4r](http://twitpic.com/1h1d4r)

I have the same trouble as the picture from the bug report shows. Any suggestions?

---

### Post by EgoGratis on 2010-10-14
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=575252](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=575252)

> This is because grub_gfxterm_fullscreen hardcodes a 10-pixel border around the edge of the screen.  If the background is just plain black, then this is fine, but it's not very helpful with a background image which tends to be designed for the full screen size. 

Basically i can do nothing about it? Border is "hard-coded" in Grub2?

Or is here somebody smart enough to come up with a (temporary) fix? :)

---

### Post by EgoGratis on 2010-10-15
OK i solved the thing. Grub2 has this border "hard coded" in it. I don't know if it is a feature or a bug.

I installed Burg. Made a nice theme for it. And now i have 100% x 100% custom made boot loader menus. And i like it a lot. So i will mark this thread as solved. It explain everything and i listed one possible solution until (if in the future) Grub2 goes back to 100% x 100% of screen size boot loader menu.

---


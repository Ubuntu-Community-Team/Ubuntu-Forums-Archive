---
title: "Small problem with ubuntu and my monitor"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by starwarsYeah on 2009-01-25
So I decided to major in computer science because I love working with computers. I can handle hardware issues easily, I'm really good with circuitry. But software issues are not my cup of tea. Since I'm taking C programming I figured I would invest in a real operating system. I dual bot Ubuntu and XP Pro 64 bit, I'm running all this on a 32" Sanyo HDTV, with an NVIDIA GeForce 6600GT. When I first installed Ubuntu, it downloaded some NVIDIA driver on its own. MY problem is that my native resolution is 1366x768, and on XP the screen fits perfectly, but on Ubuntu the screen goes off all the edges quite a bit. I need to know how to adjust this so I can actually see everything. 
Thanks!

---

### Post by llamabr on 2009-01-25
Hi.  In my experience, the install doesn't get the resolution right the first time.  Did you try:

sudo dpkg-reconfigure -phigh xserver-xorg

sometimes just reconfiguring xorg does the trick.

---

### Post by diablo75 on 2009-01-25
This thread might help:

[http://ubuntuforums.org/showthread.php?t=96980](http://ubuntuforums.org/showthread.php?t=96980)

Found it by googleing "ubuntu 1366x768"

There are others.

---

### Post by diablo75 on 2009-01-25
> **llamabr said:**
> Hi.  In my experience, the install doesn't get the resolution right the first time.  Did you try:

sudo dpkg-reconfigure -phigh xserver-xorg

sometimes just reconfiguring xorg does the trick.

Seconded.  I'd try this first before looking at other threads.  Also be sure there's nothing in between your PC and your TV (like a KVM switch).

---


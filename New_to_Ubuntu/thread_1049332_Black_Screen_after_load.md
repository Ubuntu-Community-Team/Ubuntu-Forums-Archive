---
title: "Black Screen after load"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by showkjh on 2009-01-24
I've tried searching around and I haven't been able to find a solution so I've decided to register and get help :\

Okay so my computer is 5-6 years old, and I've been trying to install Ubuntu for 2 or 3 days (my memory is a bit horrible :P)The computer I have is hp pavilion a250n and I'm using Windows XP.

So I burned the iso onto the disk, and it works perfectly fine, I select my language, and choose the install option where I wait for it to load, after it does I get a black screen and a cursor, I can move the cursor around but do absoloutely nothing else, so I decided to try waiting, and after a good 40 minutes nothing happened so I decided to give up, and try booting it in Safe Graphics Mode and I got the same result.

oh and my specs are
2.60 GHz Intel Pentium 4 processor
512 MB RAM
120 GB Memory
NVIDIA GeForce 4 MX440

I think that should cover it(besides the can't install ubuntu part)

---

### Post by russu52 on 2009-01-24
Are you able to run it as a live cd?

as a machine, ubuntu should run. but if there's a crash, i suggest trying the little mouse (xubuntu) which is lightweight.

---

### Post by showkjh on 2009-01-24
Yes I am able to run it as a live CD, and I don't really want to use xubuntu until I've explored all my options

---

### Post by linux_tech on 2009-01-24
Try adding the vga=771 option to the end of the Boot Options line
see instructions here:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

when you can, pls post your xorg.conf

---

### Post by showkjh on 2009-01-24
I tried doing what you said but I got a black screen with a blinking line, which turned to a black screen with a cursor

---


---
title: "GRUB Problem"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by sudeepk on 2010-06-20
I currently have ubuntu 9.10 installed in my dell laptop. I Have installed windows xp in it. Now that i have lost my grub, I tried to install it from a ubuntu 8.04 live cd.But the problem is the grub is an older version and i cannot install from it. I dont have a ubuntu 9.10 cd with me.. Any solutions..?

---

### Post by wilee-nilee on 2010-06-20
It is easy, follow these directions with a karmic or lucid live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
This link should default to the #11 step. If this doesn't work post the script in my sig in code tags as described in the sig.

Really to be honest you should post the script before doing anything.;)

---

### Post by technocp on 2010-06-20
boot up with your ubuntu 8.10 live CD

go to terminal or any of the virtual consoles (ctrl+Alt F1.....F6)

issue command grub at the prompt

you will get a prompt with greater than sign

on that prompt issue commands as follows

>find /grub/stage1
(hd0,0)

>root (hd0)

>setup (hd0,0)

you may get some thing different from hd0,0 may be hd0,1 or some thing like that so work accordingly

---

### Post by wilee-nilee on 2010-06-20
> **technocp said:**
> boot up with your ubuntu 8.10 live CD

go to terminal or any of the virtual consoles (ctrl+Alt F1.....F6)

issue command grub at the prompt

you will get a prompt with greater than sign

on that prompt issue commands as follows

>find /grub/stage1
(hd0,0)

>root (hd0)

>setup (hd0,0)

you may get some thing different from hd0,0 may be hd0,1 or some thing like that so work accordingly

If he has grub2 which is quite likely with Karmic these instructions are for grub legacy and as they said already the hardy cd didn't work. 

With Boot problems we really have to see the script to know whats going on. If you get a chance run it on your own setup and get familiar with it as there are lots of boot problems and there is always a need for others to be able to recognize the scripts importance and how to fix the problems.;)

---


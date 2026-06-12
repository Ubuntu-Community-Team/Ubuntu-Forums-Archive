---
title: "Packard Bell Dot M/A - Ubuntu 10.10 - screen scrambled"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by romeogal on 2011-01-31
HI
 
I'm new to Linux/Ubuntu. couple of days ago I installed for first time Ubuntu 10.10 on Packard Bell Dot M/A. I installed Ubuntu Netbook edition first but could not see the menus at all, so I had to install the desktop version.
I used a USB stick to install.
 
All works ok, except when I use browser and scroll, the screen goes crazy and gets scrambled. I need to turn machine off (I know position of menus as you can't read any text or see images sometimes).
 
It's possible that the ATi Radeon driver cause the problem, and I tried to complete a tutorial on this forum, entering the comands in terminal but some of comands were displaying missing elements information. It's possible I did worst.
 
I dont want to switch back to windows (wich comes with netbook), and need some help beginer style, as i really like how Ubuntu looks and works (except this issue).
 
What other information I need to provide? Print screens would help?

---

### Post by grief -l on 2011-01-31
see if this page helps you:
[https://wiki.ubuntu.com/FrameBuffer](https://wiki.ubuntu.com/FrameBuffer)

---

### Post by Nickjpost on 2011-01-31
> **romeogal said:**
>  
 
It's possible that the ATi Radeon driver cause the problem, and I tried to complete a tutorial on this forum, entering the comands in terminal but some of comands were displaying missing elements information. It's possible I did worst.
 

 
 
Be mindful that you didn't select conflicting drivers. I found that when I had open and proprietary drivers installed , I had massive x server issues,  see the following link
and make sure in the Synaptic Package Manager, you haven't selected the wrong or too many drivers selected. Find the specs on your device's video card and choose approproiately.  That link is for ATI drivers, but it may point you in the right direction if you have a different video card.
 
[[COLOR=#444444]https://help.ubuntu.com/community/BinaryDriverHowto/ATI[/COLOR]]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by romeogal on 2011-01-31
thanks for hints i will check links and get back with results. thanks again

---

### Post by Lula_F on 2011-11-05
Hi, I'm afraid you may be experiencing [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/556782").

I first experienced it while testing Natty and the only thing that helped was the workaround in the bug description. Now, at least, the system is usable. :(

---


---
title: "Cannot see text when use alt-ctrl-f1"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by vysotsky on 2010-07-06
Since upgrading to Ubuntu 10.04 (64 bit version) I've encountered a problem with "text mode" displays.  (I'm sorry if I'm not using the right terminology; I'll try to be as specific as possible in my description.)  

After I boot from the grub menu, I see a blurry mess of variously colored dots on a lines at the top of the screen for a second or two, but then when the full graphical login screen appears everything is fine.  I hadn't thought much about this until I tried to stop the X server and open a terminal using alt-ctrl-f1.  When I do, I again see a messy blur of dots and lines at the top.

Is there any way to fix this?

I'm running Ubuntu 10.04 (64-bit) on an HP Pavilion dv4t-1000 laptop with an NVIDIA GeForce 9200M GS graphics card.

---

### Post by jtarin on 2010-07-06
Welcome to the world of [FBDEV]("https://wiki.ubuntu.com/FrameBuffer")

---

### Post by vysotsky on 2010-07-06
Thanks!  That gave me all the information I needed to solve the problem.

---

### Post by jtarin on 2010-07-06
Your welcome. You might share you solution with others and mark the thread solved.

---

### Post by vysotsky on 2010-07-06
Gladly.  Following the instructions on the webpage to which you linked, I discovered that I could fix the problem by using the " vga=normal nomodeset" in the grub menu line that launches Ubuntu.

---

### Post by jtarin on 2010-07-06
Excellent!!!

---


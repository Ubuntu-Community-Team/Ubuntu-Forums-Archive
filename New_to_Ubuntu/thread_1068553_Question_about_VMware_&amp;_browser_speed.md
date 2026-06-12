---
title: "Question about VMware &amp; browser speed"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by Zigon on 2009-02-13
Will apps run exactly how they would under Windows? I've got Macromedia Flash running using WINE, but I'm having to many problems and it's hela slow. Firefox and other browsers are noticeably slower on ubuntu, watching videos in flash is choppy, and when I have 3+ tabs open things start to slow down. I've looked around for a solution to this, but as far as I know it's just a bug within Ubuntu. I have no idea how to view my specs on here, I have 2BG ram, Intel duo cpu, 1.66ghz and plenty of space on the hard drive, so none of that should be a problem. If this is just a common bug, could I expect a fix or some improvement with Faunty?

Thanks!

---

### Post by x33a on 2009-02-13
virtual machines cannot provide better performance than the os they are installed on.

virtual machines cannot make use of full system resources, as a normal os would. i am running firefox, view videos and do a lot of other stuff on ubuntu and i don't feel much difference in speed or performance than windows. 

you can view your full system specs with lshw.

type sudo aptitude lshw to install it.

> If this is just a common bug, could I expect a fix or some improvement with Faunty?it's jaunty and not faunty :)

---

### Post by sonofusion82 on 2009-02-13
erm.. sorry but i have got no idea what are you talking about...
the title says VMWare...
but then you talk about Flash on WINE
later you talk about firefox on Ubuntu which i assume it is native app.

anyway, i have no problem with firefox in ubuntu.

---

### Post by freak42 on 2009-02-13
> Will apps run exactly how they would under Windows?
Basically, yes, however your virtual windows does not really have a graphics card, so applications that use OpenGL or DirectX will (or might) not run good (or at all).

Flash 10 (Dev) runs quite fine in my virtual XP on Ubuntu.

---


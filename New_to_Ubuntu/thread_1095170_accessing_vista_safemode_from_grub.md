---
title: "accessing vista safemode from grub??"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by abhigyan91 on 2009-03-13
hey i have windows vista as well as ubuntu 8.10.. can ne1 tell me how to access vista safemode from grub?

---

### Post by Mark Phelps on 2009-03-13
Safemode is generally entered in MS Windows by repeatedly pressing F8 until it comes up, and then selecting the particular mode option (e.g., command line, with or without network, etc.)

All GRUB does is point to the proper boot partition; not aware of any way to have GRUB pass MS Windows an F8-keypress to force it to start in safe mode -- if that's what you're asking.

Otherwise, you boot into windows from GRUB and start pressing F8 right away...

---

### Post by abhigyan91 on 2009-03-13
yea ur rite.. but my prob was that ive gt this other msdos program wrking jus b4 vista startup.. hence i cant use f8.. i figured out a way around that tho.. np. the soln is nt relli related to linux tho ill post thie link neway..

[http://www.bleepingcomputer.com/tutorials/tutorial61.html](http://www.bleepingcomputer.com/tutorials/tutorial61.html)

---


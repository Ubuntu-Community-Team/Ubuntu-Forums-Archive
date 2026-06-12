---
title: "The First Boot Up Doesn't Seem To Start"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by dandodge1 on 2009-01-04
I installed ubuntu from a CD that I ordered.  Everything seems to install just fine.  I get to the first boot-up, the screen comes up and the little jingle plays, then the screen goes black except for the mouse pointer and it sits there doing nothing for hours.  Anyone know what is going on?

---

### Post by handydan918 on 2009-01-04
> **dandodge1 said:**
> I installed ubuntu from a CD that I ordered.  Everything seems to install just fine.  I get to the first boot-up, the screen comes up and the little jingle plays, then the screen goes black except for the mouse pointer and it sits there doing nothing for hours.  Anyone know what is going on?

Sounds like you have an nvidia or ati video card. try ctrl+alt+f1.
 If that drops you to a black-and-white text interface, (console) Then your system is OK, you just need to install the drivers for whatever card you have.  From the console, you can run ```
lshw
``` and that will list all the hardware in your box. Then you can search the forums for a tutorial on how to handle the driver install.

---


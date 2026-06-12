---
title: "Usb to DB25 Adapter Issues"
date: 2009-01-13
forum: New to Ubuntu
---

### Post by abeisgreat on 2009-01-13
I have this special cable, called an xboo cable, it has a db25 on one end (the side that goes into the computer(duh)), and my netbook does not have that port, neither does my desktop, so I bought a usb to parallel cable. I plug everything in, it works fine, no big deal. 

Well kinda... the software i am using with the xboo, doesnt want to recognize the cable. It appears to mount the cable at /dev/usblp0, which if Im not mistaken, is for printers (I know very little about the /dev folder and its workings, I have always tried to stay away), I need it to mount like a normal parallel port would, so the program can see the cable and work correctly.

Is there a way to correct this?

Thanks,
Abe

---

### Post by da_petcu21 on 2009-08-13
Unfortunately I can't help you much. I never had a linux box with a LPT DB-25 port so I dont know what path does it mount to (/dev/something). If you could find that out, maby you could make a symlink to /dev/your-lpt-to-usb-adapter. Oh and by the way: Good luck developing for GBA.

---


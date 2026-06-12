---
title: "installing games? poker programs? drivers?"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by CastorTroyXXIV on 2009-11-27
hi, i am very interested in this operating system. well, this desktop i have is a emachines dating back in 04. 2.2ghz 512mb of ram, 160 gb of hd. 64mb of video. well anyway, my question would be, can i install games i have on it? like GTA san andreas, starcraft, my laptop isnt a gaming laptop. yeah, would i be able to install games i currently have to the system? 

Also would i be able to download and install programs like Full Tilt Poker? and PKR.com? programs like that? 

The desktop needs the orginaly xp disk which it doesnt have. i dont want to buy another one yet. so i figure i try this out. like windows has drivers and such, so if i just format c: of everything. Burn Ubuntu image on a disk, insert it and follow instructions, and im good? no need for drivers or anything? i know it sounds stupid but i just dont want to buy windows xp again, or use my bootleg copy of it....yet....

 Thanks for your help and calling me a noob or whatever it is the kids are saying today... thanks. :cool:

ps. about the drivers, i dont need to do anything about it right? like my video display will be fine?

---

### Post by MelDJ on 2009-11-27
the games you mentioned (except in the 2nd paragraph which don't know about) may need WINE to run. maybe wine cant even run them but you can try. see: [http://www.winehq.org/ .]("http://www.winehq.org/")

you can check if drivers for your video card by going to system-admin-hardware drivers

---

### Post by wirah on 2009-11-27
Boot off the Ubuntu CD first before you install and you will see if you have any driver problems.

If it works, install to hard disk, and all will be fine.

GTA works for me via Wine, not sure about the others.

---

### Post by CastorTroyXXIV on 2009-11-27
thank you guys so much, now i wait for the store to open to buy some cd-rs. 2hours to go...  \\:D/

---

### Post by MelDJ on 2009-11-27
why not use a usb pendrive? make it bootable with unetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by 3rdalbum on 2009-11-27
Don't just try to run all your existing Windows programs in Wine; try and find Linux equivilants. Wine is an amazing effort to run Windows programs, but statistically it works with less than 50% of Windows programs out there. Probably closer to 20%.

You should be okay for drivers. They should all be detected and ready to go. The only possible exception might be the graphics. If you have Nvidia you can probably get it to go with proprietary drivers. With ATI you are limited to the not-very-mature open-source driver. With Intel you should be fine. With any other graphics vendor you'll probably just get a basic 2D desktop and no 3D acceleration.

---


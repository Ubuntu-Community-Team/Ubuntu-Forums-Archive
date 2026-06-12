---
title: "Could someone walk me through installing this software on WIne?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by Obero on 2008-12-08
So far I've had a handle on most graphic programs, especially our good friend Gimp, however I've also wondered if I could install this piece of software that I've had for a while and used on Windows for graphical capabilities and utilties. The name, by the way, is PhotoImpression, which came with my printer.

Can anyone walk me through installing it? I have Wine on board if that's needed, which I would suppose it would. The software is on a CD, so I'm going to have to install it that way.

---

### Post by doas777 on 2008-12-08
well, just Rclick on the executable you wanna run, and click "Open application in Wine". or you can run it from the terminal with ```
wine <path-to-exe>
```

it's that simple.

I'm not seeing your app in the wine AppDB ([http://appdb.winehq.org](http://appdb.winehq.org)) so its anyones guess as to whether yours will work or what libraries should be loaded natively. 

good luck,
franklin

---

### Post by Obero on 2008-12-08
The installation was fine, but when I open the software, it just loads for a second and then disappears. I guess it didn't work? Anyway around it? It was a standard .exe file.

---

### Post by bwang on 2008-12-08
cd to the directory where your program was installed (usually somewhere in ~/.wine/drive_c/Program\ Files) and run the program from the terminal. Post any output you get.

---

### Post by lkraemer on 2008-12-08
Another solution is to install VirtualBox from www.VirtualBox.org if
you have 2, 3 or 4 Gig Ram, and then Install Win XP as a Virtual Disk
Image VDI, and then Install your PhotoSoftware.  Seems to work fine
on most things I have tried.  You probably need to allocate a little more than the standard 10 Gig VDI when you build the VDI.  10 Gig will get XP loaded, and some other software like Antivirus, and then you will be at 6-8 Gig with a few remaining.

lk

---


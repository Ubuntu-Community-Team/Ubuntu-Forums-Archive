---
title: "missing window frames and X server"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by Shooree on 2009-06-01
Hi, i just did a somewhat larger update of my 8.10 Xubuntu.

Unfortunately, something has gone wrong after the restart, the system asked to be put up in low graphics mode. So, I chose the previous config. After a few attempts at getting the display to work, I'm now left without window frames and everything that goes with it (i.e. moving, resizing windows, seeing them in the task bar, etc). My ffox window is only half the height of the screen, as I type this.

I tried removing the gfx driver, purging it, putting the stable ver. 180 on, through both Hardware Drivers dialogue and Symantec. 

The Nvidia X Server reports that I apparently am not using the Nvidia X driver, which I am. It asks me to "Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." I did run the command, it showed a couple very generic looking entries and restarted X. Nothing substantial happened. 

As a side note, I believe that I was messing with that xorg.conf file while trying to get my laptop hotkeys to work and such, so that might be a sort of root of the problem. 

To make matters worse, my dvd drive died on me, so I've no means to reinstall the system (which I was about to do, out of desperation). Please be so kind as to give your oppinion on the matter since this really prevents me from getting any work done and this is my only box. If you need any files, I'll be happy to put them up.

---

### Post by gettinoriginal on 2009-06-03
Not sure, it's been awhile since I had to do it. At the grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by Nythain on 2009-06-03
how did you install the drivers... kernel updates will "break" manually installed (including some scripts to automate the manual task) proprietary drivers... wich sometimes requires a new install of the drivers for the new kernel.

---

### Post by SOULRiDER on 2009-06-03
Try to reconfig x with
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And thenr estart.

---

### Post by ptsubin on 2009-06-03
or your compiz or other window decorator is not started..

---

### Post by Shooree on 2009-06-05
Thanks guys, it appears that the kernel did indeed break my manually installed drivers. I got some help on #xubuntu and managed to get my window frames back by disabling compiz, which wasn't working due to the system not recognising my video card, or some other reason. 

I manually installed 177 nvidia drivers, but my X server gives me:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I ran that thingy and it didn't do much good. My Hardware Drivers window doesn't show anything anymore (literally blank fields) and I can see that the drivers aren't being utilised, judging from image quality and lack of visual effects. Any thoughts? Thanks in advance.

---


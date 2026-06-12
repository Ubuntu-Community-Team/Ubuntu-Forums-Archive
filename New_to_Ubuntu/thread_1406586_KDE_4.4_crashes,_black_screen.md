---
title: "KDE 4.4 crashes, black screen"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by rex4u on 2010-02-14
Hello everyone,

I just installed KDE 4.4 from backports and it started crashing the moment I tried to add widget or to drag folder view, etc. Plasma is consistently crashing when doing anything with widgets like adding, double-cliking, dragging or anyhting.

After last login I get black screen after login and no longer can use KDE :-(
Btw, last time I had to kill session from Ctrl+Alt+F2.

Please help me solve this ........:-(

Thanks everyone in advance.............:-)

---

### Post by lovinglinux on 2010-02-14
If you don't mind configuring your stuff again, I would recommend deleting ~/.kde and rebooting. I was experiencing window manager crashes and plasma crashes after installing KDE 4.4 and deleting ~/.kde solved the problem.

Make a backup of it if you want to use some of the settings.

---

### Post by nortexoid on 2010-02-14
I was also getting crashes. Now I get them infrequently. Smooth Tasks will cause plasma to crash on startup, so be sure to remove that. You can restart plasma from krunner or konsole by typing plasma-desktop. In konsole you'll be able to better determine what causes crashes.

---

### Post by Superdarion on 2010-02-14
I had this problem as well and deleting the ,kde folder did not help.

What I did was go to synaptic (which I had already installed out of gnome-home-sickness before I upgraded to 4.4) and updated all the kde packages. Seems like Kpackagekit left some out the first time I did it.

This fixed the problem and now I can use kde 4.4. It hasn't crashed once since I fixed that and it's working great.

By the way, since I'm not too experienced at these things, I had to jump thru hoops to run synaptic without the plasma desktop 'cause it was a fresh kubuntu install and no gnome or anything and I didn't know how to do that from the command line.

Alt+F2 saved my day.

---


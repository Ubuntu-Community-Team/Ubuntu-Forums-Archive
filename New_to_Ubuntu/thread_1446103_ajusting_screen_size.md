---
title: "ajusting screen size"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by Gerwyls on 2010-04-03
Hi all, I have just installed ubuntu but can do nothing. The graphics driver has enlarged my screen so that I can only see the centre. Nvidia provides a program in windows which lets me resize the screen from the properties tab (right click), but I can't find an equivalent in ubuntu. Does anybody know how I do it? Thanks in advance,
Gerry

---

### Post by koma77 on 2010-04-04
It's on the System->Properties->Screen setting.

If you cant reach it try pressing alt+F2 and enter: gnome-display-properties

That should give you a settings utility for changing resolution.

---

### Post by byStanderone on 2010-04-04
hi,
...it seems that the nvidia driver is not yet installed or active, you can take a look at this thread, hope it helps:
[http://ubuntuforums.org/showthread.php?t=1445740](http://ubuntuforums.org/showthread.php?t=1445740)

---

### Post by phibxr on 2010-04-04
> **Gerwyls said:**
> Hi all, I have just installed ubuntu but can do nothing. The graphics driver has enlarged my screen so that I can only see the centre. Nvidia provides a program in windows which lets me resize the screen from the properties tab (right click), but I can't find an equivalent in ubuntu. Does anybody know how I do it? Thanks in advance,
Gerry

If you're using nVidia, you should get a notification about drivers being available for installation.

The issue with the resolution being too low might prevent you from seeing them though, but there are some good driver installation guides for nVidia around on these forums.

---

### Post by houseworkshy on 2010-04-04
I always have this problem on a new install of Ubuntu on this machine and lean heavily on Alt + F2.  The post linked to above has good advice.  I'd also add that Alt + F2 can be used to start the terminal ( just type terminal ) which is also useful.  In the terminal typeing "man" in front of any command will bring up its manual page  Try "man shutdown" and "man apt-get" in the terminal for good advice on commands you will probably be using in the immediate future. 
I have posted about this and was told that it sounded like a bug and to report it which I did;

[https://bugs.launchpad.net/ubuntu/+bug/518833](https://bugs.launchpad.net/ubuntu/+bug/518833)

If yours looks like the same issue please chime in as so far I'm the only one.

---


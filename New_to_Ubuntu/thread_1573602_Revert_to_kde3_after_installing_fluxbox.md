---
title: "Revert to kde3 after installing fluxbox"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by clxclx on 2010-09-13
I set up fluxbox by following this tutorial   [http://www.backtrack-linux.org/forums/backtrack-howtos/31313-setting-up-fluxbox-bt4-r1.html](http://www.backtrack-linux.org/forums/backtrack-howtos/31313-setting-up-fluxbox-bt4-r1.html)  I want to revert back to KDE3 any help would be awesome!   Distro is Backtrack 4 r1 runs on an ubuntu 8.xx deb. version.

---

### Post by jtarin on 2010-09-13
Did you uninstall KDE? If not it should be available from the login screen under "Sessions".

---

### Post by clxclx on 2010-09-13
when i boot i use "startx" from a shell to start fluxbox before "startx" would start KDE.   Where would i find "sessions"

---

### Post by jtarin on 2010-09-13
You can only find sessions from the graphical login menu of Gnome or KDE.You didn't mention you started from a shell. Do you still have it installed? Try startkde or startkde3

---

### Post by jtarin on 2010-09-13
Or startkdm or just KDM (caps)or kdm (no caps)

if none of these work look in your /home/username folder for a file called .xinitrc it's a hidden file. If you have it you can edit/comment the lines at the bottom to start you WM.

---

### Post by clxclx on 2010-09-13
startkde3 gives me a no command found or something. startkde give me this: i'll post a pic of the error.

---

### Post by jtarin on 2010-09-13
Your trying as root....try as username

---

### Post by jtarin on 2010-09-13
Any luck?

---


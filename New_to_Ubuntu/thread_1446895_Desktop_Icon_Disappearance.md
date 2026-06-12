---
title: "Desktop Icon Disappearance"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by travisl_10 on 2010-04-04
Hello, I've been noticing this on my Ubuntu Karmic install:

Occasionally when I use the keyboard to switch between files on the desktop, or to switch between files in a folder and the desktop is partially exposed, all open windows will minimize and all of the icons on the desktop will disappear. Furthermore, right-clicking on the desktop will not give a menu.

I have compiz on, but reloading compiz doesn't help, and the only way I have found to solve this is to log off/on.

Has this happened to anyone else before?

---

### Post by NightwishFan on 2010-04-04
The program nautilus used to draw the desktop is probably crashing. You can reopen it by opening a folder under the places menu. If that does not work, try this command to fix it.
```
gconftool-2 --recursive-unset /apps/nautilus
```

---

### Post by travisl_10 on 2010-04-04
It happened again just now, I tried both methods, unfortunately neither worked.

I noticed something else strange: normally (under compiz) when switching between workspace panels only the windows are observed to be moving and the wallpaper/background stays stationary, but when this error occurs the desktop wallpaper appear to be moving as well.

---

### Post by travisl_10 on 2010-04-09
I think I figured out the problem now.

I was using an older version of the 'Breathe' icon set which I installed and via Ubuntu Tweak. After getting the newer 0.52 version through the appropriate PPA ([https://launchpad.net/ubuntu/+source/breathe-icon-theme](https://launchpad.net/ubuntu/+source/breathe-icon-theme)) the problem doesn't seem to occur anymore. :-D

---


---
title: "How do I play games in full screen mode w/o top and bottom menubars?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by d4shing on 2009-11-11
Help!  I've done some searching on this site and I can't figure it out. 

I'm playing a game (in wine), and I want it to take up the full screen.  Instead it has the task menu at the bottom and the applications/places/system menu at the top, plus the wine border at the top.

Thanks in advance

---

### Post by asuastrophysics on 2009-11-11
hmm, i'm not sure if i know how to make some games fullscreen others not, but this will make all WINE programs fullscreen:

try going to Applications -> Wine -> Configure Wine

Click on the "graphics" tab

check "emulate a virtual desktop" and set the resolution to the full resolution of your screen.

---

### Post by sliketymo on 2009-11-11
Auto-hide

---

### Post by d4shing on 2009-11-11
I don't seem to have that option on the menu; i compiled a bleeding-edge distro using git.

But, I ran winecfg and checked the options like you said.  It doesn't work, I still get the menubars.

---

### Post by d4shing on 2009-11-11
> **sliketymo said:**
> Auto-hide

Which I enable, how?

---

### Post by asuastrophysics on 2009-11-11
> **d4shing said:**
> Which I enable, how?

right-click on the top and bottom panels and hit "properties"

then check "autohide"

---

### Post by 3rdalbum on 2009-11-11
What if you turn off Compiz?

Alt-F2 and type:
```
metacity --replace
```

Run your program and see what happens.

You can turn Compiz back on again by hitting Alt-F2 again and typing:

```
compiz --replace
```

---


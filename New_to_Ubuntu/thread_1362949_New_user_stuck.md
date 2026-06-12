---
title: "New user stuck?"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by Abundance_Linux on 2009-12-23
Hi there everyone,

OK i am stuck, just installed 64bit Ubuntu a few weeks ago?
what i want 2 do is:
1. make vista the default OS:
(gksudo gedit /boot/grub/menu.lst)
comes up with an empty notepad....?

2. my desktop has gone black....how do i reset. i  cant see the desktop/background img
3. Linux can't execute the graphic interface, but i have a good graphics card - ATI Radeon HD 4850 

thx

---

### Post by x33a on 2009-12-23
if you have karmic koala, then the grub configuration file has changed. 

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

as for the graphics problem, make sure you are using the right drivers.

---

### Post by chaanakya_chiraag on 2009-12-23
1) If you are using Karmic Koala (9.10), then the easiest way is to use StartupManager:
```
sudo aptitude install startupmanager
```
and use that to set the default OS

2) Do your icons show up??  Is just the background black?  Or does the desktop not show up at all?

3) What exactly do you mean by that?  Does Ubuntu show up with a terminal?  Or does it get to a graphical login screen?

---

### Post by taurus on 2009-12-23
> **chaanakya_chiraag said:**
> 1) If you are using Karmic Koala (9.10), then the easiest way is to use StartupManager:
```
sudo aptitude install startupmanager
```
and use that to set the default OS


I don't believe startupmamager works with Grub2, yet!

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by chaanakya_chiraag on 2009-12-23
> **taurus said:**
> I don't believe startupmamager works with Grub2, yet!

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Actually, it does.  However, some features are not yet supported.  The thing Abundance_Linux wants to do, however, IS supported in startupmanager

---

### Post by Abundance_Linux on 2009-12-24
Gentlemen,

i don't know, what 2 say....
i hadn't the flimsiest notion that u guys are very helpful
i guess u are all wonderful people (linux geeks) - very grateful 4 the response.
But:
Still stuck.
1. is it possible to drug/pull a dialogue box, even if your VISUAL EFFECT is on NORMAL/EXTRA?
it seems to work only with NONE desktop env. There is no CLOSE (X) or other.

Merry X'mas & A linux New yr

---

### Post by chaanakya_chiraag on 2010-01-01
Yes you can...hold the [Alt] key and drag the window :)

---


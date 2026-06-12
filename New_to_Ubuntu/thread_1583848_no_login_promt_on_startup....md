---
title: "no login promt on startup..."
date: 2010-09-28
forum: New to Ubuntu
---

### Post by ealymbaev on 2010-09-28
Always was alright until I installed RVM and ruby 1.9.2.
After this I rebooted my PC and just got default wallpaper and NO LOGIN PROMT...

I tried CTRL+ALT+F1 and:

- startx ===> already running
- gdm ====> already running
-also tried dpkg-reconfigure xserver-xorg
- also tried apt-get install --reinstall gdm

NOTHING helps (( any other help?

P.S. tried reinstalling ubuntu twice - both times after installing ruby - same thing happens (
How can i fix this?

---

### Post by Old *ix Geek on 2010-09-28
Did you try choosing the 'failsafe' option from the boot menu?

---

### Post by ealymbaev on 2010-09-29
You mean recovery mode - then failsafe mode? If yes - i tried that - the same problem...

I wonder what could RVM and ruby do to my system... )

---

### Post by Old *ix Geek on 2010-09-29
> **ealymbaev said:**
> You mean recovery mode - then failsafe mode? If yes - i tried that - the same problem...I'm not sure we're talking about the same thing. Under "Sessions" it should be the second choice down after Gnome. "Recovery mode" to me sounds like a way to restore the computer back to its original shipping configuration. :confused:

---

### Post by ealymbaev on 2010-10-05
Nothing helped ( Reinstalled Ubuntu, installed ruby from source - works good for me

---


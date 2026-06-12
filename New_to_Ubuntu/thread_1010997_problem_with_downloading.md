---
title: "problem with downloading"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by will11 on 2008-12-14
theres a problem with my ubuntu. everytime i try and download something it says " dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." i looked up what i had to do and i did it but everytime i try it my pc freezes.
HELP!
will11

---

### Post by northern lights on 2008-12-14
Open a terminal (Applications > Accessories > Terminal) and run```
sudo dpkg --configure -a
```

---

### Post by albinootje on 2008-12-14
Your pc freezes when you do : 
sudo dpkg --configure -a
in a terminal ?
Try the same in the "recovery mode", and tell us how that goes.

---

### Post by will11 on 2008-12-14
i typed in dpkg --configure -a but it doesnt do anything it says dpkg: error processing vinagre (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up libgnutls26 (2.4.1-1ubuntu0.2) ...

---

### Post by albinootje on 2008-12-14
Try in a terminal : sudo apt-get install --reinstall vinagre

---

### Post by northern lights on 2008-12-14
Did you run it as superuser?

If so, remove vinagre and reinstall it. Let's hope it's not part of the GNOME desktop metapackage. If it is the following will ask you whether you want to remove a gazillion packages rather than one. Do not follow through then.

If it isn't, you can safely run```
sudo aptitude purge vinagre && sudo apt-get autoclean && sudo apt-get update && sudo apt-get install vinagre
```

---


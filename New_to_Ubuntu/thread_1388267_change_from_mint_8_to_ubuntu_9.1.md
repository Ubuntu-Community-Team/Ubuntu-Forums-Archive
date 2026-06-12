---
title: "change from mint 8 to ubuntu 9.1"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by poonforce on 2010-01-22
hi i m using mint 8, is it possible to change from mint 8 to ubuntu 9.1 without fresh installation of ubuntu 9.1, if there is way please let me know. thanks

---

### Post by blazemore on 2010-01-23
> **poonforce said:**
> hi i m using mint 8, is it possible to change from mint 8 to ubuntu 9.1 without fresh installation of ubuntu 9.1, if there is way please let me know. thanks

```
sudo apt-get install ubuntu-desktop
```

At heart, Mint is just Ubuntu with a lick of paint and some bolt-on packages that add out-of-the-box functionality most people would add anyway. (I know it's more than that, but for the purposes of this explanation...)

Installing the ubuntu-desktop package will overwrite Mint's artwork and default settings with Ubuntu's own.
When you make a new user, it will have all the default Ubuntu look and feel. Obviously it won't overwrite any current users' settings!

---

### Post by poonforce on 2010-01-23
> **blazemore said:**
> ```
sudo apt-get install ubuntu-desktop
```

At heart, Mint is just Ubuntu with a lick of paint and some bolt-on packages that add out-of-the-box functionality most people would add anyway. (I know it's more than that, but for the purposes of this explanation...)

Installing the ubuntu-desktop package will overwrite Mint's artwork and default settings with Ubuntu's own.
When you make a new user, it will have all the default Ubuntu look and feel. Obviously it won't overwrite any current users' settings!
thanks blazemore

---

### Post by mick222 on 2010-01-23
I done this a while ago it's easier to reinstall ubuntu had a lot of problems getting rid of mint menu's.I tried to upgrade from mint to intrepid I can't reember what packages caused the problems but think mint assistant was one.You need to remove the mint repositories and this can throw up some problems

---

### Post by blazemore on 2010-01-23
To get rid of mint menu, right-click it and then click "remove from panel"
Then remove the package mint-meta-* to prevent future dist-upgrades from reinstalling it.

---


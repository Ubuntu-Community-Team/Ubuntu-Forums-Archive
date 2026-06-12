---
title: "Jaunty to 9.10"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by gasmansteve on 2009-09-14
Hi folks
Forgive what is probably an easy peasy question but if I update all my files in Jaunty (9.04) will this give my desktop the equivalent of version 9.10:confused: . Mmmm... thinking about it now ... updates to my XP box in the past didn`t make it Vista so maybe answered my own question. Doh!
Regards
Steve

---

### Post by k33bz on 2009-09-14
> **gasmansteve said:**
> Hi folks
Forgive what is probably an easy peasy question but if I update all my files in Jaunty (9.04) will this give my desktop the equivalent of version 9.10:confused: . Mmmm... thinking about it now ... updates to my XP box in the past didn`t make it Vista so maybe answered my own question. Doh!
Regards
Steve

Sorry no, it will just make it an updated 9.04.

A distro upgrade would make it 9.10

---

### Post by bodhi.zazen on 2009-09-14
You may upgrade with update-manager.

9.10 is still in Alpha, so expect bugs :

```
sudo update-manager -d
```

Once 9.10 is released you can update with update-manager

```
sudo update-manager -c
```

---

### Post by nhasian on 2009-09-14
if you wait till Karmic Koala is released you can then also just download the Ubuntu 9.10 Alternate Installer ISO and burn it to a CD.  then simply insert it into the CD tray while ubuntu is running and it will ask if you'd like to upgrade your distribution.  Its a lot faster this way if you have multiple ubuntu machines your upgrading.

Also I should point out that if you are upgrading from a previous release to Karmic, it will not migrate your filesystem to EXT4 and it will not install grub2.  Personally i've upgraded each version of ubuntu from 8.04 till 9.04 without any problems, but I recommend a fresh install for 9.10 so you can take advantage of the new filesystem speed.

---


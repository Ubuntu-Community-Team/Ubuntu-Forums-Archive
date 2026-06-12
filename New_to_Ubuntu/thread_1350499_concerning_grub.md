---
title: "concerning grub"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by dansar99 on 2009-12-09
I upgraded to Karmic thru update manager. Today ,update manager downloaded security fixes for grub2. I dont think I have grub2. How can I tell?  Looks the same to me. I really do not like to mess with things being I am in a precarious position by not having restore discs for XP.Dan

---

### Post by philinux on 2009-12-09
Upgrading to karmic will leave you with grub legacy. You will still have a menu.lst. i.e. no change.
[http://www.ubuntu.com/getubuntu/releasenotes/910overview#GRUB%202%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/910overview#GRUB%202%20by%20default)

To double check use this.

```
grub-install -v
```

Mine says 
grub-install -v
grub-install (GNU GRUB 1.97~beta4)

Because I did a clean install of Karmic and therefore got grub2.
Click the grub2 link below.

The updates are for packages in the repo. I guess grub2 is there for you but not in use.

---

### Post by ranch hand on 2009-12-09
philinux has got this right on the nose.  You actually have all of grub2 except for "grub-pc" which is the working part.

Grub-common now puts in all the basic files that you need for grub2.

You have to keep in mind that grub-legacy is no longer supported by anyone.

---

### Post by dansar99 on 2009-12-09
> **ranch hand said:**
> philinux has got this right on the nose.  You actually have all of grub2 except for "grub-pc" which is the working part.

Grub-common now puts in all the basic files that you need for grub2.

You have to keep in mind that grub-legacy is no longer supported by anyone.

What do I do to get grub2 and would that be wise? I see on the forum where people are having trouble with it.  Dan

---

### Post by ranch hand on 2009-12-09
If your boot loader is working the way you want it to, LEAVE IT ALONE.

On your system there really should be no problem with grub2.  The issue is not if it will work or not, though, the issue is if your grub-legacy is working.

If it is working then there is no problem.  Grub-common just got an update.  Don't worry about it.

---

### Post by dansar99 on 2009-12-09
> **ranch hand said:**
> If your boot loader is working the way you want it to, LEAVE IT ALONE.

On your system there really should be no problem with grub2.  The issue is not if it will work or not, though, the issue is if your grub-legacy is working.

If it is working then there is no problem.  Grub-common just got an update.  Don't worry about it.

Thank you. Left alone it will be.  Dan

---


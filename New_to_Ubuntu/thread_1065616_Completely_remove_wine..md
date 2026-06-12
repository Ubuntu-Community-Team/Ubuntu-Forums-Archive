---
title: "Completely remove wine."
date: 2009-02-10
forum: New to Ubuntu
---

### Post by AllRadioisDead on 2009-02-10
Hi, I built wine from source and I can't remove it, I deleted my wine folder, I've tried sudo apt-get remove wine, I've tried reinstall other versions of it, but I can't get rid of it. I need to install a lower version, how do I get rid of the version I built?

---

### Post by konqueror7 on 2009-02-10
you can try by...```
sudo apt-get autoremove --purge wine
```...see if that works...

---

### Post by AllRadioisDead on 2009-02-10
> **deuphil.kaufmann said:**
> you can try by...```
sudo apt-get autoremove --purge wine
```...see if that works...

Brilliant, thank you!

---


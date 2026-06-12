---
title: "Dual boot menu lockout"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by siliconwombat on 2008-12-21
Hi everyone,

Im trying to install ubuntu on a seperate hdd but as a dual boot system alongside XP Pro Sp3. I tried installing from cd on boot but it wasnt recognized so ive installed from within windows. When I restart the dual boot menu comes up but my keyboard is locked out and stays locked out until the menu options disappear. The installation appears to run perfectly but I have reinstalled jic.

Any ideas?

---

### Post by siliconwombat on 2008-12-21
Bump

---

### Post by jimmy the saint on 2008-12-21
did you try a different keyboard?

---

### Post by siliconwombat on 2008-12-21
keyboard works fine at boot then locks up at the dual boot menu and then works fine again once its passed....Its working now :) I think it may be related to installing using wubi but im new to this so not sure, trying to install again now. Thanks anyway

---

### Post by siliconwombat on 2008-12-21
Ok, found the issue, on install I installed to f: but boot .ini was configured to look at c:

Next up is the message
```
Windows could not start because of a computer disk hardware configuration problem

Could not read from the selected boot disk. Check boot path and disk hardware.
```

Could this be due to f: being a sata drive?

---


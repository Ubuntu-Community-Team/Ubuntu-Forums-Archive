---
title: "Problem with installation"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Valinx7 on 2009-07-08
anytime i try to install a program using the package installer, it says i have another software management tool open.  If i try to access the package installer manually without opening with a program, it says "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

What do i do?

---

### Post by Sealbhach on 2009-07-08
OK, well this error message suggests you run this command in the terminal:

```
sudo dpkg --configure -a
```

Make sure you have closed Synaptic and Add/Remove.

.

---

### Post by ajgreeny on 2009-07-08
Also check to see if you need to close the update manager which opens automatically now in jaunty, though minimised by default, if there are any updates available.

---


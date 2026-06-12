---
title: "Whacky crazy problem"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Indian_Guy101 on 2009-02-07
I was trying to download updates but whenever I try to download something I get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E: cache->open() failed, please report

---

### Post by avtolle on 2009-02-07
From the terminal (Applications>Accessories>Terminal)```
sudo dpkg --configure -a
```and see if that takes care of your problem.

---

### Post by Ptero-4 on 2009-02-07
you need to type 
```
sudo dpkg --configure -a
```
in the terminal. This finishes the previous install that was left incomplete. (this happens if you close the package manager, or perhaps the computer, while it´s installing, uninstalling or updating stuff).

---


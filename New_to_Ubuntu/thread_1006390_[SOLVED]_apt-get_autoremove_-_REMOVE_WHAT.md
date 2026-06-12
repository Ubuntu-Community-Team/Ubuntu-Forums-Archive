---
title: "[SOLVED] apt-get autoremove - REMOVE WHAT?"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by thadacto on 2008-12-09
What exactly will be removed if I use the following code:
apt-get autoremove

Sounds like it will remove everything on the drive

---

### Post by Eisenwinter on 2008-12-09
It removes unused dependencies.

You don't have to issue that command, but if you don't, you will have unused libraries on your machine.

---

### Post by thadacto on 2008-12-09
Many thanks, eisenwinter - I couldn't find it in the 
"man autoremove"

---

### Post by hyper_ch on 2008-12-09
```

man apt-get

```

---

### Post by Hospadar on 2008-12-09
apt keeps a list of packages that were installed automatically as a dependency for some other package, so let's say I install package X with dependencies Y and Z, then I remove X, I can use autoremove to get rid of Y and Z.

---


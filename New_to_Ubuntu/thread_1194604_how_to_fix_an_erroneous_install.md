---
title: "how to fix an erroneous install?"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by poisonborz on 2009-06-22
Hola,
I've tried to install Exaile, but the computer restarted in the process. Now I can't simply reinstall, and the package manager only says I should manually start "dpkg configure -a" (how helpful).... How to fix this?

---

### Post by oldos2er on 2009-06-22
Open a terminal (Applications, Accessories, Terminal), and run
```
sudo dpkg --configure -a
```

---


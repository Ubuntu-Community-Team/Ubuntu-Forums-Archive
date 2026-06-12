---
title: "Unable to install vim"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by sm_here on 2010-01-28
Getting this Message when trying to install vim:
Package vim-gtk has no installation candidate

Help please.

---

### Post by sisco311 on 2010-01-28
Make sure that the *universe* repositorie is enabled (System -> Administration -> Software Sources). Update & try to install it again.

```
sudo software-properties-gtk -e universe
sudo apt-get update
sudo apt-get install vim-gtk
```

---

### Post by sm_here on 2010-01-28
Thanks so much.

---


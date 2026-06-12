---
title: "Help uninstalling KNetAttach"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by som88 on 2009-10-11
Please help me uninstalling KNetAttach. I tried Synaptic Package Manager as well as apt-get remove command in the shell but neither helped.

---

### Post by wojox on 2009-10-13
Try:

```
sudo dpkg --remove --force-remove-reinstreq KNetAttach
```

---

### Post by wajdigary on 2009-12-21
> **wojox said:**
> Try:

```
sudo dpkg --remove --force-remove-reinstreq KNetAttach
```
hi i tried to remove with terminal but it said.. command not found.

i already autoremoved kdebase..

any solutions please?

---


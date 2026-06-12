---
title: "fire close animation stopped working"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-07-12
it just up and stopped working and animation addon has dissappeared from plugin list in ccsm anyone know how to fix this?

---

### Post by nhasian on 2009-07-12
first lets see if you have compiz running at all.  go to system->preferences->appearance.  In the Visual Effects tab, see if its stuck on none or if you can set it to Normal or Extra.  if you can, then we can reinstall ccsm with:

```
sudo apt-get install --reinstall compizconfig-settings-manager
```

---


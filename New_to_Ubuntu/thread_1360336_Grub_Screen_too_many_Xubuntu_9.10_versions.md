---
title: "Grub Screen too many Xubuntu 9.10 versions"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by droadtrip on 2009-12-20
[SIZE=2][COLOR=Navy]I can't find MENU.1st in order to adjust my Grub startup screen. 

Everytime I installed updates to Xubuntu, it saves the prior version of the OS and now it looks like I have too many OS's on my PC. Is there a way to hide all the old versions so i can just see one version (the latest version) of Xubuntu 9.10?[/COLOR][/SIZE]

---

### Post by k3lt01 on 2009-12-20
You could use Synaptic to remove the previous Kernels etc. Leave the current one and the last one though so you have something to fall back on incase of difficulties later on.

---

### Post by koba101 on 2009-12-20
```

sudo apt-get install startupmanager

```

System->administration->starup manager


go to advanced and tick the limit number of kernels to keep to whatever you like

should work on xubuntu as well

---


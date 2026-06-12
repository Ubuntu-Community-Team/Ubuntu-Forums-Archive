---
title: "? errors.after TestDisk/Photorec"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by bgmomof2 on 2009-08-11
You all have been great help for me.  I had 9.04 64bit running, and have tried to switch to 32 bit for more flexibility in applications and windows programs that I would like to install with wine.

Anyway, all was good until I ran TestDisk and Photorec. gksu nautilus wouldn't give me root access, Firefox wouldn't load pages, and synaptic package wouldn't work.  

Any idea what happened?  I'm trying over with a clean install.

---

### Post by Christophe Grenier on 2009-08-14
USe "df -h" to check the remaining free space. If there is none, all applications using temporary files will have problems to execute.

---


---
title: "Identify Specific version?"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by nosmadar on 2009-05-05
Is there a way to easily identify which version is running? - By version I mean the 8.04, 8.10 ... Ubuntu version numbers.  Due to trying out several versions I've lost track of what's on this machine and I'm not savvy enough to have memorized the Kernel version #s and know which Ubuntu release they correspond to.

---

### Post by IanW on 2009-05-05
Open System Monitor (menu - System/Administration/System Monitor)
Click on the system tab
Read the page

---

### Post by ktrnka on 2009-05-05
From the terminal you can execute

```
lsb_release -a
```

and

```
uname -a
```

---


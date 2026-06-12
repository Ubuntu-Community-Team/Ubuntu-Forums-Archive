---
title: "Create free space on the disk......"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Csongi on 2009-01-06
I'm having a disk with 3.72 Gb disk size in my computer........




No games and only a few application software installed......





Does anyone able to help me how to get free space back?





 Thanks:





Csongor

---

### Post by nhasian on 2009-01-06
you could try

```
sudo apt-get clean
```

also you can use the Disk Usage Analyzer in Applications->Accessories

---

### Post by ELF_O8 on 2009-01-06
Also ```
sudo apt-get autoremove
``` will remove all redundant or unneeded dependencies.

---


---
title: "is there any software to check hdd surface?"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by gabak on 2010-01-17
i would like to check if my hdd has bad sectors or not

---

### Post by lukeiamyourfather on 2010-01-17
There's almost never a need to manually check for bad sectors. The disk does this as you use it, so if it finds a bad sector its marked as such and the drive moves on to put data somewhere else. Any S.M.A.R.T. utility can tell you how many bad sectors have been found during regular use since the drive was manufactured.

[http://tips4linux.com/scan-for-bad-sectors-in-linux/](http://tips4linux.com/scan-for-bad-sectors-in-linux/)

That has the command for checking the S.M.A.R.T. bad sector count, and the second one to manually check for bad sectors (which can take a ***very*** long time).

---


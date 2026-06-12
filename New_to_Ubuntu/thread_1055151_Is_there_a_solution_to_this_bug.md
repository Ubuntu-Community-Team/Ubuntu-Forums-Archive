---
title: "Is there a solution to this bug?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by sdim on 2009-01-30
```
sd@sd:~$ sudo dpkg --configure -a
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
sd@sd:~$
```

I get this after downloading updates through dpkg.
Is there a solution to this bug?I can't understand...
Thank you.

---

### Post by taurus on 2009-01-30
[http://ubuntuforums.org/showthread.php?t=1054498](http://ubuntuforums.org/showthread.php?t=1054498)  :rolleyes:

---

### Post by LowSky on 2009-01-30
according to [THIS]("http://www.go2linux.org/problem-upgrading-debian") which is simular to your issue, it seems like you downloaded some packages that are corrupted.. you will need to uninstall them first, then rerun dpkg

---


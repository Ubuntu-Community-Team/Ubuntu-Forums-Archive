---
title: "execute .exe in xfce"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by Mr.Kuchinawa on 2011-03-25
Hi, I wanna execute a .exe file (spotify) to run it under wine in xubuntu. All the answers I can find online regarding this says that I should mark it as executable under properties, but I can find no such option.

Any help would be much appreciated.

---

### Post by blind2314 on 2011-03-25
> **Mr.Kuchinawa said:**
> Hi, I wanna execute a .exe file (spotify) to run it under wine in xubuntu. All the answers I can find online regarding this says that I should mark it as executable under properties, but I can find no such option.

Any help would be much appreciated.

If you right click on the file you want to execute, and go to Properties -> Permissions, there should be a tick mark next to "Execute". Check that, and as long as you own the file, it will set the execute bit.

Alternatively, through terminal you can do this:
```
cd /directory/path/of/file
chmod 755 filename.exe
```

---

### Post by Mr.Kuchinawa on 2011-03-25
That's exactly the problem, there is no option for marking it as executable.

(I used dolphin instead, fixed the problem)

---


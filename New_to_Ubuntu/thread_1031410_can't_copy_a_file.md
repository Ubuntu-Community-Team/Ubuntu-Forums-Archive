---
title: "can't copy a file"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by gkraju on 2009-01-05
hi i am new to linux 
i am having ubuntu 8.04 and i installed inside xp(didn't install seperately) if i want to copy a file from ubuntu i cant paste in my windows drive the paste option is disabled 
but i tried with a pen drive it works fine help ???

---

### Post by Nxion on 2009-01-05
What do you mean  **"installed inside xp(didn't install separately)" **

Did you use Wubi or some kind of virtualization software like Parallels or VMWare?

---

### Post by Crafty Kisses on 2009-01-05
This all depends on if you used a virtual install, but if you don't have a virtual install please make sure that Windows is mounted correctly, if Windows is mounted you can copy files by doing the following, remember substitute your own information:
```
cp /home/user/file /media/xp/file2
```

---


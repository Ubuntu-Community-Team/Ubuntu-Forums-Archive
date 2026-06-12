---
title: "I can't see my 2nd hard drive"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by jorru3p0 on 2010-11-20
I installed ubuntu 10.10 over xp but When it installed, my 2nd hard drive disappeared. I formatted it using Gparted but I still can't see it. When I try to mount it, it gives me an error saying: 

according to mtab, /dev/sdb1 is already mounted on /

---

### Post by mr_luksom on 2010-11-21
Can you post the results of:

Show all connected drives:
```
 fdisk -l 
```

Show all mounted drives:
```
 mount 
```

---


---
title: "[SOLVED] Can't see Window's file system from WUBI"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by WASHAD on 2008-12-26
Due to a partitioning problem, I ended up having to go with the windows install of Ubuntu. I seem to be unable to see the Windows file system as I can when I run Ubuntu as dual boot. Is that to be expected?

Thanks, 


SteveJ

---

### Post by moredhel on 2008-12-26
When you say you cannot see it - how do you mean?

Can you see in gparted? Or with

```
fdisk -l
```

---

### Post by OutOfReach on 2008-12-26
If your using Wubi then your Windows files will be in /host

Go into the filemanager and change the address to '/host'

---

### Post by WASHAD on 2008-12-26
That did it, thanks.

---

### Post by OutOfReach on 2008-12-26
No problem, mark the thread as Solved by going into Thread Tools (ontop of your first post) and selecting 'Mark thread as Solved'. :)

---


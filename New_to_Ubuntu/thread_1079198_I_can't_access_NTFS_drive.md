---
title: "I can't access NTFS drive"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by jmfa59 on 2009-02-24
All of a sudden I can't access my ntfs drive everythingwas OK before any help.
I got those two messages screen shot attached

---

### Post by pmlxuser on 2009-02-24
please make sure that when you exited your windows system normaly using shutdown. if not it locks the drive and you can't access it.

---

### Post by roccivic on 2009-02-24
go to terminal and execute this:

```
cat /etc/fstab
cat /etc/mtab
```

come back here with output ;)

Peace

---


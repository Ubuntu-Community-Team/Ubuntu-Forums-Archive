---
title: "dpkg: operation requires read/write access to dpkg status area"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by zebraneo on 2009-09-10
I don't know what to do about this:
lisa@Dolli:~$ dpkg  -i  --force-all cupswrapperMFC210C-1.0.2-3.i386.deb
dpkg: operation requires read/write access to dpkg status area

---

### Post by Excedio on 2009-09-10
> **zebraneo said:**
> I don't know what to do about this:
lisa@Dolli:~$ dpkg  -i  --force-all cupswrapperMFC210C-1.0.2-3.i386.deb
dpkg: operation requires read/write access to dpkg status area

```
sudo dpkg  -i  --force-all cupswrapperMFC210C-1.0.2-3.i386.deb
```

---


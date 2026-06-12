---
title: "Checking whether 32bit or 64bit"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Gannon8 on 2009-03-26
Heeeeello

I am wondering how I can check whether this is an Ubuntu 8.10 Server x86 or Ubuntu 8.10 Server x86_64. What commands can I use?

Thanks a lot :)

---

### Post by logos34 on 2009-03-26
command:

> uname -a

and

> lsb_release -a

---

### Post by SuperSonic4 on 2009-03-26
For just the architecture (uname -a also works but it has more information)
```
uname -m
```

---

### Post by Gannon8 on 2009-03-26
Okay, thanks a lot :)

---


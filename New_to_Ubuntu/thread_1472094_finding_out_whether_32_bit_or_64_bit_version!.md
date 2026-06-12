---
title: "finding out whether 32 bit or 64 bit version!"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by avee137 on 2010-05-04
How can we find out that whether installed version of ubuntu 9.10 is 64 bit or 32 bit ??

---

### Post by jbrown96 on 2010-05-04
```
uname -m
```

---

### Post by avee137 on 2010-05-04
> **jbrown96 said:**
> ```
uname -m
```

that gives the machine hardware info however i m interested in knowing about the OS!

---

### Post by jbrown96 on 2010-05-04
> **avee137 said:**
> that gives the machine hardware info however i m interested in knowing about the OS!

no that reports the software that is running. I know what I'm talking about.

---

### Post by 3rdalbum on 2010-05-04
> **avee137 said:**
> that gives the machine hardware info however i m interested in knowing about the OS!

If the command returns "x86_64" then you're using 64-bit. If it returns something else, then you're using 32-bit.

---

### Post by avee137 on 2010-05-04
thanks.

---


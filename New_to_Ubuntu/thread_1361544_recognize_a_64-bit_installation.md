---
title: "recognize a 64-bit installation"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by byenary on 2009-12-22
Hello,

How can i recognize wether ubuntu was installed as 64 bit, does this information appaer in /etc/issue ? I don't think so, how/where can i find this ?

Thx

---

### Post by Kevbert on 2009-12-22
In Applications-Accessories-Terminal enter
```
uname -a
```
You should get something like
```
2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 21:27:25 UTC 2009 x86_64 GNU/Linux
```
the x86_64 is 64 bit Ubuntu. The 2.6.28-17 is the linux kernel version.

---


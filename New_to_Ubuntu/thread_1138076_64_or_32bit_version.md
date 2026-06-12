---
title: "64 or 32bit version?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by dyrer on 2009-04-26
How can I identify if an installed version is 64 or 32 bit and what version 8.04, 8.10, 9.04)
Thanks

---

### Post by freak42 on 2009-04-26
uname -m

will print out either something like
686 -> 32-bit
or
x86_64 -> 64-bit

for the version I don't know any command, but in gnome
you can go to System->About Ubuntu and it's below the logo.

hth

---

### Post by jespdj on 2009-04-26
For the version of Ubuntu:
```
cat /etc/issue
```

---

### Post by dyrer on 2009-04-26
thank you guys

---


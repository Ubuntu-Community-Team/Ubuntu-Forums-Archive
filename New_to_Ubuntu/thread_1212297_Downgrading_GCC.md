---
title: "Downgrading GCC"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by Shockburner on 2009-07-13
I have the latest version of Ubuntu and GCC but I trying to compile a program that I am pretty sure it needs an older version of GCC. How could I get and install say GCC 3.4.6 (I compiled this program just fine at work on a redhat machine using GCC 3.4.6)

---

### Post by mc4man on 2009-07-13
gcc-3.4 is available in jaunty, just install it (and leave your default gcc alone.

if your source uses a ./configure then something like this should do, otherwise edit appropiate file in source
```

CC=gcc-3.4 ./configure [COLOR="RoyalBlue"]<configure options if any>[/COLOR]
```


edit Forgot to mention you'd need to install cpp-3.4 also

---

### Post by Shockburner on 2009-07-21
Thanks

---


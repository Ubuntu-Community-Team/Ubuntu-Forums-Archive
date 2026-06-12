---
title: "Uninstall opera browser"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by timreed on 2009-01-17
Help.. I recently installed Opera Browser and I can uninstall it. I tried ti delete the opera files but there seems to be a lock on them. Wont let me delete them. What kind of program has no uninstall..help

---

### Post by mamamia88 on 2009-01-17
try sudo apt-get autoremove opera should work

---

### Post by billgoldberg on 2009-01-17
open up synaptic, search for opera, and completely remove it.

It's the same for every other program.

Have you ever removed a program before?

---

### Post by binbash on 2009-01-17
sudo apt-get purge opera

---

### Post by billgoldberg on 2009-01-17
or for the heck of it

```
sudo apt-get autoremove opera --purge
```

---

### Post by union two levers on 2009-02-08
> **billgoldberg said:**
> or for the heck of it

```
sudo apt-get autoremove opera --purge
```

thanks for that, worked a treat

---


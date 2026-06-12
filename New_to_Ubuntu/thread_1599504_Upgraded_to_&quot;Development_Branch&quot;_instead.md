---
title: "Upgraded to &quot;Development Branch&quot; instead of final 10.10"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by houseman102002 on 2010-10-17
I upgraded my Ubuntu 10.04 to ubuntu 10.10 but it crashes after logging in and booting to the desktop. It brings up 3/4 of the desktop and then it crashes. I looked at the grub screen and it says "10.10 maverick development branch" rather than the normal notation for the final version. Apparently for some reason I upgraded to the beta version rather than the final version. Could this account for my troubles in logging in? And why would I get the "development branch" instead of the final? Thanks in advance.

---

### Post by Sealbhach on 2010-10-18
Check your software sources, make sure they look normal then do:

```
sudo apt-get install --reinstall ubuntu-desktop
```

.

---


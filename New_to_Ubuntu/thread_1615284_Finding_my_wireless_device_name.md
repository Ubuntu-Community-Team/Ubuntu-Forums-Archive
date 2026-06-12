---
title: "Finding my wireless device name"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by jhazard112 on 2010-11-06
Trying to find a way to find out what wireless card i have....i am unsure what I need to put into a terminal window to find this information...any help is much appreciated.

---

### Post by spcwingo on 2010-11-06
If it's interal:

```
lspci
```

If it's USB:

```
lsusb
```

---

### Post by anewguy on 2010-11-06
Or, if it's a laptop, do both as some laptops have the internal wireless connected to an internal USB.

Dave ;)

---


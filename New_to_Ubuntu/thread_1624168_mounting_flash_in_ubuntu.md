---
title: "mounting flash in ubuntu"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by jalub on 2010-11-17
cant mount my flash drive in ubuntu any help out there for the problem child:guitar:

---

### Post by deconstrained on 2010-11-17
Open a terminal, plug in the flash drive, then enter 'dmesg | tail -100' to get some diagnostic information.

---

### Post by wojox on 2010-11-17
Also

```
lsusb
```

To see if it recognizes it. You can also try manually mounting it.

---


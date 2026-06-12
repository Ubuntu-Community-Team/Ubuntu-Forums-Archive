---
title: "help disabling my windows wireless driver"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by Snypercell on 2009-02-18
i need to disable the Windows wireless driver that comes with Ubuntu 8.04.02 64bit, but i cant find the file "/etc/modprobe.d/backlist" to modify. any suggestions?

---

### Post by Elfy on 2009-02-18
It's blacklist not backlist

```
gksudo gedit /etc/modprobe.d/blacklist
```

---


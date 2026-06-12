---
title: "how to install gui in server ubuntu"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by naved ..... on 2011-04-28
how to install gui in ubuntu server 10 ?????

---

### Post by cek on 2011-04-28
It depends on what you want.  If you want the "full" ubuntu experience, you can install the ubuntu-desktop meta package:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by gg234 on 2011-04-28
Try this [http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)

---

### Post by avtolle on 2011-04-28
If you would like a minimal gnome gui, do ```
sudo apt-get update && sudo apt-get install xorg gnome-core
```.

---


---
title: "Cannot get to my desktop after 9.04 update"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by akonuatta on 2009-09-10
after ubuntu 9.04 update i get a screen to login but my desktop does not display and it read cannot load image

---

### Post by SteveNorman on 2009-09-10
try ```
/etc/init.d/gdm restart
```

or
```
 sudo dpkg-reconfigure -phigh xserver-xorg 
```

---


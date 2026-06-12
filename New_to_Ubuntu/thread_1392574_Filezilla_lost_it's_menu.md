---
title: "Filezilla lost it's menu"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by mvalviar on 2010-01-28
I've tried to use the global menu to see if it will make things easier for me. I've found out it's not for me so I removed it from my panel. However Filezilla's menu hasn't returned. How could I fix it?

---

### Post by yestaro on 2010-08-31
I have the same problem, does anyone know ?

Ubuntu 10.04, gnome-applet-globalmenu 0.7.9, FileZilla 3.3.1

---

### Post by mapes12 on 2010-08-31
Wrong post.

Sorry.

---

### Post by K-Vaughan on 2010-11-02
Hey.

I suffered from the same problem. In Ubuntu 10.10 I had used the indicator-appmenu package and found it wasn't what I wanted. Filezilla lost it's menu but I could access it via Alt+F then navigate using the arrow keys.

I found using apt-get purge <application> helped since it fully removes configuration files too.

The command I used:
```
sudo apt-get purge appmenu-gtk indicator-appmenu indicator-applet-appmenu
```

I hope this helps.

---


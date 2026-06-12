---
title: "[SOLVED] command question"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Java Geek on 2009-01-04
What does sudo dpkg --configure -a do? It somehow fixed my computer and im just curious now.

---

### Post by cardinals_fan on 2009-01-04
From the man page:
```
dpkg --configure package ... | -a | --pending
    Reconfigure an unpacked package. If -a or --pending is given instead of package, all unpacked but unconfigured packages are configured.

    Configuring consists of the following steps:

    1. Unpack the configuration files, and at the same time back up the old configuration files, so that they can be restored if something goes wrong.

    2. Run postinst script, if provided by the package. 
```

---

### Post by overdrank on 2009-01-04
> **Java Geek said:**
> What does sudo dpkg --configure -a do? It somehow fixed my computer and im just curious now.

Maybe this will help
> dpkg --configure package ... | -a | --pending
    Reconfigure an unpacked package. If -a or --pending is given instead of package, all unpacked but unconfigured packages are configured.

    Configuring consists of the following steps:

    1. Unpack the configuration files, and at the same time back up the old configuration files, so that they can be restored if something goes wrong.

    2. Run postinst script, if provided by the package. 

---

### Post by Java Geek on 2009-01-04
thank you!

---

### Post by wootah on 2009-01-04
Both the above gentlemen provided the right answer--how they got to it was by using **man**

When in man, you can search for a keyword by pressing **/** and then typing what you want followed by enter. After that, you can skip to the next found word with **n** and the previously found word with **p**

To clear all of the words that are highlighted: **ESC u**

Hope the helps :)

---


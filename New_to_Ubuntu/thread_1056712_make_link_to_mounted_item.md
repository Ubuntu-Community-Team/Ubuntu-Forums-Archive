---
title: "make link to mounted item"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Dumbestcrayon on 2009-02-01
I would like a my partition /media/Stuff to have a shortcut on the desktop. I do not want all of the mounts to show up on the desktop so doing gconf-editor and checking "Volumes-visible" isn't an option. 

I tried to right click the folder and do "Make Link" but its greyed out.


Any other options?

---

### Post by ibuclaw on 2009-02-01
Press **Alt+F2** and type in something like so
```
ln -s "/media/**MountedFolder**" ~/Desktop/**MountName**
```

Regards
Iain

---

### Post by Dumbestcrayon on 2009-02-01
> **tinivole said:**
> Press **Alt+F2** and type in something like so
```
ln -s "/media/**MountedFolder**" ~/Desktop/**MountName**
```

Regards
Iain

You're the bomb.

Thanks!

---


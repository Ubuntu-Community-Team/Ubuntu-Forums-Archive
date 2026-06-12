---
title: "Rotate screen"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-08-21
Like in XP I can press Ctrl+Alt+Arrow key and it will rotate 90 degrees for me (netbook e-reading) and I was wondering how to do that in Ubuntu.  Is it possible to set up with the same key combination?

---

### Post by philinux on 2010-08-21
> **TriBlox6432 said:**
> Like in XP I can press Ctrl+Alt+Arrow key and it will rotate 90 degrees for me (netbook e-reading) and I was wondering how to do that in Ubuntu.  Is it possible to set up with the same key combination?

You need to modify xorg.conf to include ```
Option "RandRRotation" "True"

```

See this thread. There are many more. [http://ubuntuforums.org/showthread.php?t=1116751](http://ubuntuforums.org/showthread.php?t=1116751)

---

### Post by oldsoundguy on 2010-08-21
An FYI:
NVidia has it as part of their driver package for their cards .. newest generic drivers in 10.04 for NVida also include the option.  BUT you have to use the menu to rotate the screen .. not keystrokes.
Works for me just fine.

---


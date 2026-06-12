---
title: "Can't access folders from terminal"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by Dangger on 2010-03-03
I have all my documents in a ntfs partition. Some of the folders' names have accents (Mi música instead of My Music). I can't get them open from terminal and I can't open them with Gnome Do. Any ideas?

---

### Post by Arijit_Kundu on 2010-03-03
you can go to the parent directory from terminal and type 'ls' to see the folders. Also, starting with 'Mi m' and pressing a tab will show the possible folder.

---

### Post by Jefferythewind on 2010-03-03
you need to do this first, then restart:

```
apt-get install ntfs-config
```

---


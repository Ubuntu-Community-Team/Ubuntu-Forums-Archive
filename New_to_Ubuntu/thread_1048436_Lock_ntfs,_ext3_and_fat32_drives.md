---
title: "Lock ntfs, ext3 and fat32 drives"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by melrokz on 2009-01-23
How to lock disk drives with a password of another user or root user and prevent automount on startup? (ntfs, ext3, fat32)

---

### Post by mjheagle8 on 2009-01-23
they wont be mounted automatically if you do not put them in fstab.

---

### Post by drs305 on 2009-01-23
If the entry is listed in fstab, you can include the option "noauto" to prevent auto-mounting. 

You can run this command to prevent automounting of removable / external media.
```

gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount 'false'

```

---


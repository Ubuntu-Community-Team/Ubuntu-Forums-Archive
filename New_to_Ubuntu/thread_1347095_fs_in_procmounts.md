---
title: "fs in proc/mounts"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-12-05
When booting up, I get this message.

No suitable fs in proc/mounts.

Is this important?

---

### Post by JBAlaska on 2009-12-05
"/proc/mounts, is a symlink to self/mounts which contains a list of the currently mounted devices and their mount points (and which file system is in use and what mount options are in use)."

View and edit it with:
```
gksu gedit /proc/mounts
```

---

### Post by dunbrokin on 2009-12-05
Thanks for that...but what is the fs bit about...and what should I do?

---


---
title: "2 home directorys"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by mrbiggbrain on 2008-12-17
i was wondering if it was possible to set up a symbolic link or such so that the home directory of a particualar distro could also be the home path for another such as running fedora AND ubuntu off the same home directory?

---

### Post by Cl0ud9 on 2008-12-18
I suggest putting your home directory on its own partition. Then you can edit fstab in each distribution to mount that partition in the /home directory.

---


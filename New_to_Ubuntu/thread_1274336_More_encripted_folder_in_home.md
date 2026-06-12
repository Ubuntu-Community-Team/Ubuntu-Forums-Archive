---
title: "More encripted folder in home"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by bikrus on 2009-09-24
I use ecryptfs. But it can create only one automounted crypted folder in home at login. 

Is there a way to create more encrypted folders in home which will automount at login and correctly umount on logout (in text shell or through gdm)?

ecryptfs do things well, but only for one folder.

---

### Post by Paqman on 2009-10-02
You could create the actual folders within your Private folder, and then symlink to them.

---


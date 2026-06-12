---
title: "edit chmod for all files (almost)"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-09-09
I would like to set my home folder permissions to 600 for almost all files, using chmod -R 600 /home/username but since this would make it impossible to login to my account was i wondering if it was possible to set almost all files to 600 except for those that need 700?

---

### Post by blur xc on 2009-09-09
> **SpinningAround said:**
> I would like to set my home folder permissions to 600 for almost all files, using chmod -R 600 /home/username but since this would make it impossible to login to my account was i wondering if it was possible to set almost all files to 600 except for those that need 700?

I kind of went through somethign similar.  The problem is, if you chmod -R you will change all the permissions to the directories as weel, and w/o execute permissions on directories, you can't cd into them anymore...  irritating.

Maybe this can be of help- [http://ubuntuforums.org/showthread.php?t=1261604](http://ubuntuforums.org/showthread.php?t=1261604)

BM

---

### Post by Penguin Guy on 2009-09-09
```
chmod -R a-rw     # Deny all read/write access for all users
chmod -R u+rw     # Allow all read/write access for you
```

Execute permissions will remain unchanged. Perhaps you should wait for someone else to verify that this will actually work (just in case).

---


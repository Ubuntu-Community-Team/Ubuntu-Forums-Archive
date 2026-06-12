---
title: "When in LiveCD mode how to mount devices"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-05-23
I'm having a problem either copying or backing up my /home. The .evolution file as well as other "." files won't copy. It's a file permission problem.

When in LiveCD (Natty) mode, how do I mount sda with my user password?

---

### Post by TeoBigusGeekus on 2011-05-23
Try with
```
gksu nautilus
```

---

### Post by Mark_in_Hollywood on 2011-05-23
Does gksudo nautilus preserve the file permission, links, time stamps, symlinks, group ownership and devices?

---

### Post by Mark_in_Hollywood on 2011-05-25
Since this post, I have learned that only 'tar' or 'dar' are able to safeguard files and directories while preserving the attributes and extended attributes.

---


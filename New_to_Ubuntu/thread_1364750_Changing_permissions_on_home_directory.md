---
title: "Changing permissions on home directory"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2009-12-26
If I changed the permission on my home directory (and all of its files recursively) so only owner and groups have permission to read, write and execute files, would this break anything? Would it have any negative effects?

---

### Post by taurus on 2009-12-26
No, it should not.  However, someone from the group can mess with your personal settings since he/she has permission to write to your own $HOME.

In other words, the only thing would break is probably your $HOME if somebody in the group has a bad intention.

---

### Post by I[AM]SMRT on 2009-12-26
> **taurus said:**
> No, it should not.  However, someone from the group can mess with your personal settings since he/she has permission to write to your own $HOME.

In other words, the only thing would break is probably your $HOME if somebody in the group has a bad intention.
Ah, well I was just gonna set the group permissions to r-x so that solves that. Thanks!

---

### Post by spiderbatdad on 2009-12-26
Most likely you will have problems if making the changes recursively on the entire directory. For basic privacy you only need to change the /home/user directory to 700
```
chmod 700 /home/username
```

---

### Post by taurus on 2009-12-26
> **'I[AM]SMRT said:**
> Ah, well I was just gonna set the group permissions to r-x so that solves that. Thanks!

Then group cannot write to it.  If you really want to allow people in the group to write/modify things, then create a partition or even a directory to share among the members of a group.

---


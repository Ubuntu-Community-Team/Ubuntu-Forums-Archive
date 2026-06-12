---
title: "Permissions"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Screwed it up again on 2009-02-04
Thanks to a typo I screwed up the permissions on the entire partition and now it won't boot.
> FILESYSTEM! Target doesn't have /sbin/init/
Booted up a live CD and tried, to no avail, to chroot into it; didn't think that would work anyways.

The owner of / isn't root but the first user.  How can I reset it?

---

### Post by finer recliner on 2009-02-04
I dont think "chroot" is what you want to use. Instead, try:

```

chown root /

```

this should change the owner of the / directory back to root.

---


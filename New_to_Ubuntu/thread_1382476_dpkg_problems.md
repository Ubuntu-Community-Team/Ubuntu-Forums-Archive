---
title: "dpkg problems"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by RemmyNumber7 on 2010-01-16
I am using Ubuntu 8.04 i was trying to install Air crack -ng. Anyway i get this strange error when i try to open Synaptic Package manager it says  " E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.  "  is there a command i could enter into Terminal to fix this.

---

### Post by llamabr on 2010-01-16
> **RemmyNumber7 said:**
> I am using Ubuntu 8.04 i was trying to install Air crack -ng. Anyway i get this strange error when i try to open Synaptic Package manager it says  " E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.  "  is there a command i could enter into Terminal to fix this.

```
sudo dpkg --configure -a
```?

---


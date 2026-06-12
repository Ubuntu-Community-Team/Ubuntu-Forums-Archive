---
title: "Updates break your wireless?"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by timcredible on 2008-07-08
Wireless drivers are added to the kernel.  When you do updates, sometimes there's a new kernel.  When that happens, the new kernel is the default one on the grub boot screen, and the wireless drivers you added previously aren't there.  The solution is to re-add the wireless drivers the same way you did before.  For a temporary fix, choose the old kernel at the grub boot screen, because the old kernel is still there and still has the wireless drivers.

---


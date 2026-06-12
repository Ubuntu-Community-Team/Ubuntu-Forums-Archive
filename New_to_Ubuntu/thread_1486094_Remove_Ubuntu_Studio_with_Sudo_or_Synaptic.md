---
title: "Remove Ubuntu Studio with Sudo or Synaptic?"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by isee on 2010-05-17
```
sudo apt-get purge ubuntustudio-desktop
```Does that code have the same effect as marking ubuntustudio-desktop for removal using Synaptic?  Would one be prefered?

I installed it using Synaptic if that makes any difference.  I also removed a lot of Studio packages myself using Synaptic, but if I remember correctly I had the Edubuntu desktop installed at one time, and when I uninstalled it left behind all the packages it had installed.

I remember a post about removing all Studio packages, I'll look that up if I want that.

Thanks!

---

### Post by dearingj on 2010-05-17
> **isee said:**
> ```
sudo apt-get purge ubuntustudio-desktop
```Does that code have the same effect as marking ubuntustudio-desktop for removal using Synaptic?  Would one be prefered?

Not quite. It has the same effect as marking it for "complete removal" in Synaptic. After you do this, you'll probably want to do ```
sudo apt-get autoremove --purge
``` to remove any remaining no-longer-needed packages.

---

### Post by isee on 2010-05-20
Thanks very much dearingj!

---


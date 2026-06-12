---
title: "GRUB listing 2 Ubuntu versions"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by Judgegeo on 2010-06-30
Hey guys,

I put netbook remix on my dell inspiron mini last night, after a few hours got the wireless working, and did an update. Now grub is showing 2.6.32-22-generic and 2.6.32-21-generic as boot options.

Should I just stop grub from listing the 32-21-generic and ignore it, or is there a better option?

Regards.

---

### Post by redbook4574 on 2010-06-30
> **Judgegeo said:**
> Hey guys,

I put netbook remix on my dell inspiron mini last night, after a few hours got the wireless working, and did an update. Now grub is showing 2.6.32-22-generic and 2.6.32-21-generic as boot options.

Should I just stop grub from listing the 32-21-generic and ignore it, or is there a better option?

Regards.


32.21 is your old kernel, I personally find it useful to hang on to at least one previous kernel just incase of bugs in the new kernel.

---

### Post by warfacegod on 2010-06-30
It would be wise to ignore it. They don't take up that much space on your HDD and it's a good backup plan if something goes wrong to have another kernel to boot into. If looking at it bugs you then tell GRUB to stop displaying it.

---


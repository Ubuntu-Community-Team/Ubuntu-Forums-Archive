---
title: "All these new kernels"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by moody_mark on 2009-01-12
Ive been using ubuntu a few months now and noticed that often a new kernel is released and each time i accept the updates, in grub the new kernel is listed alongside the older ones, defaulting to the new kernel each time.

While this is ok with me and hasnt affected the way the system is working at all, Im just wondering if it will take up any additional space on the disc and if so wether it would be best to purge the older kernels.

How do you purge an older kernel if you dont need it?

---

### Post by Bachstelze on 2009-01-12
> **moody_mark said:**
> Im just wondering if it will take up any additional space on the disc

Yes, you can see it for example with:

```
ls -lh /boot
```


> **moody_mark said:**
> and if so wether it would be best to purge the older kernels.

How do you purge an older kernel if you dont need it?

With your favourite package management application, remove the [font="monospace"]linux-image[/font] package corresponding to the version of the kernel you want to remove. It's better to keep at least two, though, in case one gets broken (so you can still boot the other).

---


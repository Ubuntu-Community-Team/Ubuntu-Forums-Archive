---
title: "Hardware Abstraction Layer hald"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by atngplusultra on 2009-05-12
When i boot up, occasionally, the progress bar stops and it goes to the bootlog, and the final step, before it stops responding is:
```
Restarting Hardware Abstraction Layer hald...
```
and it will be essentially frozen.

sometimes, this also happens in recovery mode, although, more times than not, it'll get to "hald" and then after 5 seconds or so, it continues to boot normally.

This was never a problem in any previous kernels.
I'm on a Toshiba Satellite laptop, and my hardware mostly cooperated with 8.10, far better than 9.04, although I'd optimally blend the two, because of how each has treated me.

Anyway, is HALD being an issue for anyone else?

---

### Post by ellgor on 2009-05-12
Hi,

Check to see if you have "libhal-dev" installed, had similar issue this fixed it for me.

Regards,Ellgor.

---

### Post by atngplusultra on 2009-05-12
unfortunately, that didn't work.

i tried fixing broken packages when i next got recovery mode to work, but my lan cable was unplugged and there wasn't one available so that did nothing, i think.

and also, a few lines before the "Restarting ... hald" line, this pops up:

```
ntfs-3g: Failed to access volume '/dev/disk/by-uuid/9C20A4DF20A4C21E': No such file or directory.
Please type '/sbin/mount.ntfs --help'
``` and so on.
maybe that's a different issue, but ...

---

### Post by badger89 on 2009-05-13
i have this problem too but its constant on my HP laptop.

---


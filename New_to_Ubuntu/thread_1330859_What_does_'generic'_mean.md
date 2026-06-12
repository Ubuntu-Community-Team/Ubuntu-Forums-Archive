---
title: "What does 'generic' mean?"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by SteelCore on 2009-11-18
```
yu@xy321:~$ uname -r
2.6.31-14-generic
```
I know that the Linux kernel has a development and a stable release but what does generic mean?
Thanks

---

### Post by insane_alien on 2009-11-18
it means the kernel is suitiblefor various processor architectures, typically 32-bit architectures and will be able to make use of the various instruction sets contained with in.

---

### Post by spikyjt on 2009-11-18
Actually it has nothing to do with architectures, the kernel has to be compiled for a specific architecture and will have been for 32bit or 64bit x86 compatible processors, most likely.

The "generic" label refers to a general configuration, suitable for most uses. It is the default desktop configuration. There are a few other configurations provided by ubuntu, such as "server", "rt" (realtime) and "virtual". These have different settings applied, depending on their application.

It has nothing to do with release (stable or otherwise) either. The major version number reveals that. Linux kernel releases are always an even number when stable and odd when developer. So 2.6 is stable, but 2.5 was its testing version. 2.6.31 is the 31st release of the 2.6 variant. 2.6.31-14 is ubuntu's 14th compilation of the 2.6.31 kernel. You won't find a development kernel in an ubuntu release.

---


---
title: "kernel panic on clean install"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-12-21
I don't understand why I'm getting a kernel panic on boot from a clean install. I tried to install 9.04 and 9.10 on an old computer and got this error on boot several times in a row before it loaded just fine.

```
[    1.439339] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)..
```
On the second boot I got the same error but the number was different, 1.258870.

---

### Post by sandyd on 2009-12-21
> **slughappy1 said:**
> I don't understand why I'm getting a kernel panic on boot from a clean install. I tried to install 9.04 and 9.10 on an old computer and got this error on boot several times in a row before it loaded just fine.

```
[    1.439339] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)..
```
On the second boot I got the same error but the number was different, 1.258870.

seems like a hard drive problem. did you try running testdisk or fsck?

---

### Post by slughappy1 on 2009-12-21
I ran the new Palimpsest Disk Utility that came with 9.10. After running self test it said that it FAILED. When I looked at the Attributes though, nothing failed.

---

### Post by slughappy1 on 2009-12-22
Any other thoughts?

---

### Post by Xoanan on 2009-12-22
Well, after a bit of digging, there is this

[http://kerneltrap.org/node/7053]("http://kerneltrap.org/node/7053")

One poster mentioned that his was caused by a bad memory module.  He pulled it and it went away.  Tricky suggestion though..

Last time, I had a Kernel Panic, I had to replace the HD.

---


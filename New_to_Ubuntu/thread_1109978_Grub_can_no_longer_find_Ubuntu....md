---
title: "Grub can no longer find Ubuntu..."
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Gyroscope352 on 2009-03-29
Using Ubuntu 8.10 on a Macbook, problem # one million. I have Ubuntu installed and updated. It is installed on a flash drive and I am booting up with a boot disc. It was working very well. Then, I tried to change the screen resolution and extend my desktop onto another monitor. Bad idea. I could no longer see the toolbar or anything like that so I had no way of changing it back. I tried restarting, but the next time I booted up I got some stuff ending in this:

Taget file system doesn't have /sbin/init
no init found, Try passing init=bootarg

Busybox <version number> built in shell (ash) Enter 'help' for a list of built in commands

(initramfs)

What now? I have Googled and found little that actually explains what I need to do. Can anyone help me out?

---

### Post by ranch hand on 2009-03-29
When you boot next and get the grub menu up hit C.  This will give you the grub CL.
```

geometry (hd0)

```
This is assuming that you only have one drive.  If Ubuntu is on a second drive replace the 0 with 1.

Post results.

---


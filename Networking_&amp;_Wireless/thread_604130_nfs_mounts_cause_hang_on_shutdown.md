---
title: "nfs mounts cause hang on shutdown"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by paulisdead on 2007-11-05
Since I installed Gutsy on my desktop at home, I've had a problem where the system gets stuck at shutdown if I have my NFS shares mounted.  Both of these are mounted via my fstab file.  If I manually umount them before shutdown, the system shuts down fine.

I might just write an init script that umounts the shares at the earliest point in the shutdown process, but I was wondering if there's a more elegant way to fix this.  Maybe bump up the nfs-common script so it runs earlier in runlevels 0 and 6?

---


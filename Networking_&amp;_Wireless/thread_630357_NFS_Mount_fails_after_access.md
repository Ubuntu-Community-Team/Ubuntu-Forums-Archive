---
title: "NFS Mount fails after access"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by William_in_Kanata on 2007-12-03
I have two Ubuntu 6.06 servers running, doing a nice job, and so far problem free. So far.

Recently when I do an NFS mount of a directory on system B to a mount point on system A, the mount looks fine, but after the first access to it, all subsequent attempts to use the mounted directory fail. If go into the directory and do an ls -l of the mounthed directory i get

? ------ ? ? ? ?

I can unmount the directory, and remount it, and it will look normal, but after the first access, it will revert to the status above.

Other Things To Know:
 - The directory being mounted is /opt on system B, and is a RAID1 array.
 - This has been working perfectly for about 6-8 weeks.
 - Nothing has changed on either system recently
 - I don't see anything that looks relevant in any of the system logs on either system.
 - Both systems are patched up to date.

Anyone seen a problem like this before? Know how to fix it?

TIA

---


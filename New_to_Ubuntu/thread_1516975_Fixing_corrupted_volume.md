---
title: "Fixing corrupted volume"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by brettgpalmer on 2010-06-24
I recently setup a mirror on two Hitachi 1TB disks and then created a volume over the top of the mirror.  The initial setup went well and it seemed to be working great but my machine recently rebooted and now the volume is inaccessible.  

I re-synced the mirror but the volume no longer shows up.  I'm after if I create a new volume over the top of the mirror I will lose everything that I originally copied to the volume.

Here is the other strange thing.  I created the mirror and it was called md2.  Now when the system reboots and I do a 'cat /proc/mdstat'  is shows as 'md_d2'.  What would cause that problem?

I'm running kubuntu 10.x.  

If anyone has suggestions on how I can recover my lost volume from this mirror I would appreciate it.  


Thanks,


Brett

---


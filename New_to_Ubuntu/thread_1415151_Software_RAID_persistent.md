---
title: "Software RAID persistent?"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by Joel Barnes on 2010-02-24
I used the ubuntu disk admin GUI to create a software RAID array for miscellaneous data. RAID1, two identical IDE disks, ext4 fs. _not_ bootable.

If I reinstall the OS, will it recognize the array? I know how to configure the auto-start and auto-mount as long as Ubuntu says "yes, these disks belong to an array" and assigns it its array UUID.

If it doesn't recognize the old array, will it recognize the data on the disks individually? The principle of RAID is that I should still have the data on both. Presuming they are synched before I start the rebuild, I guess.

Thanks,
Joel

---

### Post by Hospadar on 2010-02-24
what happens if you boot off a livecd, does it recognize the array?  I suspect you might need to do a little extra setup after you re-instal to get it all working.

Regardless, I would imagine whatever happens on the livecd would be the same as what happens on a fresh install (ideally).

---

### Post by Gone fishing on 2010-02-24
Should do - when you create the raid you have to create a raid partitions then add them to the raid device to create raid. So it should be recognized by another Linux as such.

On one of my boxes running Opensuse I have raid 1 on / and /home partitions it boots fine and will boot if either HD is unplugged. I have done this with Hardy but it did have some issues (bugs reported) and was painful but could be made to work. I guess this is probably fine in karmic.

The live CD seem like a good way of checking in a non destructive way.

---


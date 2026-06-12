---
title: "Empty /mnt folder"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by liys on 2009-07-15
Hi all,
 
I have ubuntu inside Qemu, and I just wanted to mount floppy disk but realize I have an empty /mnt folder, why's that and how can I proceed mounting floppy?
 
 
Thanks,

---

### Post by 3rdalbum on 2009-07-15
/mnt is not usually used - these days we tend to use /media.

The reason why there's not anything inside /mnt is because you have to create the mount point yourself - just create a folder in there and make sure it has the permissions that you want the floppy disk to have.

---

### Post by liys on 2009-07-15
If I want to create a floppy mount point, in addition to create mnt/floppy folder, do I need to configure fstab too?
 
Thanks,

---

### Post by roccivic on 2009-07-15
> **liys said:**
> If I want to create a floppy mount point, in addition to create mnt/floppy folder, do I need to configure fstab too?
 
Thanks,

No, IIRC, fstab is for non-removable media only (HDD, network, etc).

---


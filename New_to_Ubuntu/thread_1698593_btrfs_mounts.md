---
title: "btrfs mounts"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by rhdinah on 2011-03-02
I don't know exactly what forum to post to regarding file systems ... particularly btrfs. Please feel free to move this to the proper place. Thanks!

I've four hard drives configured as a raid0 btrfs file system and I've no problem getting this up and running. When mounting the file system I use the first drive, /dev/sdb, in the mount string:

/dev/sdb /dev/sdc /dev/sdd /dev/sde

The problem comes when using the *Places* panel menu item ... each of the drives, other than /dev/sdb I presume, show up on this menu item drop down. Each displayed drive points back to the mount of the btrfs file system. I would prefer to keep the business of the btrfs devices private. In other words not viewable in the user environment. I suppose the worst thing about this is that if you click on any of drives an icon pops up on the desktop ... which can be removed by an unmount. But again this places the details of this raid0 device in the user environment.

The question is: Is it possible to *not* have these devices show up in the Places drop down?

Thanks in advance for your useful input!

-- Robert

---


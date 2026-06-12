---
title: "Newbie Numpty Needs Help"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by garsue44 on 2009-02-03
Hi Guys Newbie Numpty here,Installed Ubuntu from disc before partitioning the drive.Result lovely ubuntu But how the heck can i reformat.Do I have to download an alternate cd & reformat from that.I want to reinstall vista the partition & dual boot the drive after.As ubuntu is easier and faster than Mr Gates system.Please be kind as it has been an expensive experiment as had to but vista disc to reinstall.

---

### Post by Coreigh on 2009-02-03
It is far easier to install and dual boot if you install Ubuntu *after* Windows. I recommend backing up any files to be saved to an external drive or CD and starting over. Use any drive partitioner you are comfortable with to split your drive. You can go with two partitions, one for Win and one for Ubuntu, or use 3 and have the third for the "My Documents" / "home" folder. In the case of three you need to use a common filesystem, FAT32 or NTFS, because Windows doesn't read EXT3. After partitioning, install Windows to the _first_ partiton it just likes this better. After Windows is working then install Ubuntu. The Ubuntu installer will handle setting up the grub dual boot configuration for you.

 Both Windows and Ubuntu can be configured to use the third partition for user files if that is the configuration you choose.

---

### Post by garsue44 on 2009-02-03
thanks Coreigh for the quick reply but being a complete idiot how do i uninstall & reformat so that i can 1st put windows back on to my drive,

---

### Post by niteshifter on 2009-02-03
> **Coreigh said:**
> ...  or use 3 and have the third for the "My Documents" / "home" folder. In the case of three you need to use a common filesystem, FAT32 or NTFS, because Windows doesn't read EXT3. ...

_Do not use a FAT32 for /home_! FAT32 does not support user permissions and so many things Linux-y will not function correctly. Nor should one use NTFS for /home as when (not if) Windows has a problem and glitches the NTFS volume you won't be able to boot normally into Ubuntu.

Uninstalling is easy: After backing up the files you wish to keep from this existing Ubuntu install, just boot from the Ubuntu LiveCD and delete all partitions on the drive using GParted.

Next prepare for the Windows install. With GParted make a partiton at the front (left hand side of GParted's bar display) and mark it as NTFS. 

Create another partition right after that one and mark it as NTFS or FAT32 (VFAT) as you wish. Note that FAT32 has a 4GB file size limit.

Leave the rest of the space unallocated.

Boot from the Windows CD and let it's setup have it. Afterward you'll have a C: and a D: drive that are the two paritions you made above. Windows setup may ask (it's been awhile for me) to enlarge those two partitions. Tell it no.

Then boot from the Ubuntu Live CD and let it's installer use the remaining area. This will be made into two partitions for you, one is for the / mount point, the other will be swap. You can also opt to manually partition from within the Ubuntu installer and make a partition for /, one for /home and one for swap.

---


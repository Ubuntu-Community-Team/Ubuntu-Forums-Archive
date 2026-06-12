---
title: "is the swap partion faster/slower depending on where it is placed?"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by genetik on 2009-10-29
Because the rim of the disk moves at a greater velocity than the center, it is my understanding that if the swap partition would work better when its data is written and read toward the rim of the disk surface.  

Is this dumb?  Or when I do a clean install of 9.10 later today can I make a "faster' swap partition by creating it on a certain side of the disk?

---

### Post by ukripper on 2009-10-29
> **genetik said:**
> Because the rim of the disk moves at a greater velocity than the center, it is my understanding that if the swap partition would work better when its data is written and read toward the rim of the disk surface.  

Is this dumb?  Or when I do a clean install of 9.10 later today can I make a "faster' swap partition by creating it on a certain side of the disk?

On normal daily desktop/laptop use, if you got 2GB RAM it is highly unlikely you would need swap in first place. rule of thumb is "DDR2/3 RAM is always faster than Swap space even if you got SSD"

---

### Post by freak42 on 2009-10-29
According to wikipedia ([http://en.wikipedia.org/wiki/Hard_disk_drive#Data_transfer_rate](http://en.wikipedia.org/wiki/Hard_disk_drive#Data_transfer_rate)) it actually is the case that data on the ouside is faster read than on the 'inside' of the disk(s), now the question remains whether this is at the logical end or beginning of the disk, I know that the same effect exists with cd-roms/optical disks, and they are filled up from the inside, so if you only fill it half, you actually fill the slower half.

hth

---

### Post by lovinglinux on 2009-10-29
I do partition my disk in a way that everything that needs constant access and speed is placed in the first partitions. Swap is the first partition I create. I also keep those partitions small and use different partitions for personal data that needs constant access from those that are used for long-term storage. For example, my home partition has only 9 Gb and it is used mostly for configuration files. My personal data (videos, photos, documents..) is stored in a larger partition, which is the last created, then I simply create symlinks inside home.

Here is my partition scheme:

sdb1 - 2 Gb swap
sdb2 - 12 GB /
sdb3 - 9 Gb /home (configuration files only and symlinks to folders in the data partition)
sdb4 - 125 Gb /home/me/data (personal files)

I have another disk, which is IDE and thus slower, where I put data files that do not need to be constantly accessed, like distro ISO files, deb files and other stuff.

I have a nice post discussing this, but I can't find it right now.

EDIT: here it is [http://ubuntuforums.org/showpost.php?p=7391830&postcount=5](http://ubuntuforums.org/showpost.php?p=7391830&postcount=5)

---


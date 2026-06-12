---
title: "Permissions and ownership"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by mlempenau on 2011-01-18
Mostly likely I have set up a conflict.  My ownership and permissions for my external drives seem to be changeable but once changed within a short time they go back.  I have named them and the name takes but then a hour or a day later they go back to the /media/sdb1/ format and the old file stays but is not used.  At this time the permissions go back too.  Everything goes back to root including ownership.  From my experience with windows I would say that I have set something up that conflicts with something else.  The same thing seems to happen with fstab file too.  So I am now lost as to where to look next.  I have tried to use Storage Device Manager as well as sudo in a terminal window.  Both of these work but then later it reverts back.  Thanks for helping.  Mike
There is also another difference ... I have one ext4 partition that is mounted, three NTFS partitions that are mounted and two FAT32 partitions that will not mount.  ext4 and FAT32 partitions on the same drive.

---

### Post by mlempenau on 2011-01-18
Anyone have any ideas?  I'm totally lost.  When I boot it says it can't find the ext4 partition but then it must find it cause it boots.

---

### Post by john77eipe on 2011-01-19
What happens when you create files using a terminal? Do the permissions of the file change after you close the terminal?

---

### Post by oldos2er on 2011-01-19
What filesystem(s) are you using on the external drives? Can you post your fstab? ```
cat /etc/fstab
```

---


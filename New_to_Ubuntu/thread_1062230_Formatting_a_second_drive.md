---
title: "Formatting a second drive"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by nullifidian53 on 2009-02-06
I just did a search and could not find anything to do with this question. I just added a second hard drive (WD 500 GB SATA) to my Dell 530N running Ubuntu 8.10. This second drive is for backup only. When I format it in EXT2 or 3 it mounts ok but will not allow me to copy data to it. When I formatted it in FAT32 I can copy data to it. Why? By the way I used Gparted to do the formatting.
Roger

---

### Post by taurus on 2009-02-06
If it is ext2/ext3 filesystem, you just change the ownership of the mount point for that drive from root to your login name.  Then, you can write to it anytime you want.

Assuming it is mounted to /media/share and your login name is fidian, you would just run something like these from a terminal.

```
sudo chown -R fidian:fidian /media/share
ls -la /media
```

---

### Post by nullifidian53 on 2009-02-06
Thanks taurus
 That explains it. I have found a LUG in my area and look forward to becoming more proficient at Linux.
Roger

---


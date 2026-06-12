---
title: "Help, new instal deleted /home"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by apox77 on 2010-05-30
OK, first, I'm an idiot and did a new install without backing up my data!
 
I have a 500GB disk that was formated to Mint 9.10 and I did a new install with Ubuntu 9.10. I checked the box to manually determine partitions and set then as such
 
sda1 boot (box checked to format)
sda2 root (box checked to format)
sda3 extended
sda5 /home (box NOT checked to format)
sda6 swap
 
upon restart, all data in my /home file is gone and there is no separate /home elsewhere. I had only 10 GB free space on my original /home and the new /home has 417 GB free space.
 
I think I mistakenly listed the /home as ext3 when it was originaly ext4.
 
Will this automatically overwrite (or hide) the data and can I recover it?
 
You help will be GREATLY appretiated!!!
 
Ed

---

### Post by TeoBigusGeekus on 2010-05-30
Can you post us the contents of your fstab file?
```
gksu gedit /etc/fstab
```

---

### Post by apox77 on 2010-05-30
```

```# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=8cf0fa40-f50f-4df3-ab8a-f625dedd3c6d /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=cfba118d-d7e5-468a-9c78-58620ce0ef24 /boot           ext3    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=b6988009-1e55-4dd0-9a74-1cc7404b3886 /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=c4f00cd3-c2f8-4976-ac17-2688314dbde6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by apox77 on 2010-05-30
I booted up with Gparted and ran testdisk.  It located two large partitions listed as deleated (due to overlap),  one lists the content of the new /home.  The other says, no files - filesystem damaged.

---

### Post by JohnLM_the_Ghost on 2010-05-30
As a general rule of thumb is that ext3 (and AFAIK ext4 as well) has a slim chance of recovering files.

Your case might be a bit different.
One thing you SHOULD do - is cease using the affected hard disk (or at least the partition in read/write).
Boot from other HDD or system and mount the partition in R/O only if needed.

Now the bad news...
The new ext3 partition is likely to have overwritten the superblocks and journals of the old partition, so the usual methods might not work. Doesn't mean you shouldn't try them. (extundelete and ext3grep comes to mind)

On other hand if you had certain type of files (like JPEG photos), you might want to look into magicrescue - since it uses no journals or superblocks of original filesystem (in fact it is filesystem independent tool), you are likely to recover quite a bunch this way.
But this tool only recognizes unfragmented patterns of certain data, and recovers no filenames or directory structures.

---


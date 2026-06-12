---
title: "External drives and mounting issues"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by ShiningEntity on 2011-05-22
So I recently decided to make the switch to Ubuntu, and I've managed to troubleshoot my way through all the issues I've encountered, especially thanks to this forum. However I'm now having an issue and I couldn't find anything on it/work out what to search for regarding it.

I have 2 external harddrives, a 1TB expansion and a 170ish GB that used to be my home drive for windows (I'm not dual booting btw, solely ubuntu). Between them I have 4 partitions, 2 on each. The problem is, although I've edited fstab appropriately, and tried things such as NTFS Config, upon boot it doesn't appear that which harddrive is named what by ubuntu (e.g. sdb and sdc) is consistent. Some times, the 1TB is sdb and the other drive is sdc, making everything mount correctly according to fstab, but other times the drives are the other way around. This means that my old windows recovery partition is mounted to /media/expansion, messing up file paths for media players and such.

Not sure of the relevance, but here's my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda1	/	ext4	errors=remount-ro	0	1
/dev/sdc1	/media/RECOVERY	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
/dev/sdb1	/media/expansion	ntfs-3g	defaults,nosuid,nodev,locale=en_GB.UTF-8	0	0
/dev/sdb2	/media/expansion2	ntfs-3g	defaults,nosuid,nodev,locale=en_GB.UTF-8	0	0
/dev/sdc2	/media/windows	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
/dev/sda5	none	swap	sw	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0


```

If anyone could help me out, I would really appreciate it.

Thanks :)

---

### Post by nothingspecial on 2011-05-22
change all those /dev/sd??s to the uuid of each partition.

To find these type

```
sudo blkid
```

and use like so

```
UUID=b3d74959-a2ed-447b-8b58-4bf9ac9b7eee /home           ext3    defaults
```

The uuid never changes.

Another option is labeling the drives, then use like so

```
LABEL=flac  /home/ns/music/flac ext3 defaults 0 0
```

The labels don't change unless you change them and using them make fstab more readable if you have a lot of entries.

---

### Post by ShiningEntity on 2011-05-22
Followed your first suggestion, and a reboot has resulted in everything correctly mounted.

Thank you :)

---


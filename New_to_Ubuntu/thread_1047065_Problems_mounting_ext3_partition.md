---
title: "Problems mounting ext3 partition"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Nevyn on 2009-01-22
Hi! I've been trying to automount two partitions on a second internal disk with ext3 file system. I want them to mount to the existing folders /media/hangar and /media/warehouse, but when I  ```
sudo mount -a
``` 
I get this: ```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
sdb5 mounts just fine, but not sdb1.
This is what my fstab looks like
```

# /dev/sdb1
(UUID) /media/warehouse	ext3 defaults	0	2
# /dev/sdb5
(UUID) /media/hangar ext3 defaults	0	2

```

I've tried my best to follow _[How to fstab]("http://ubuntuforums.org/showthread.php?t=283131")_ and can't figure out why it won't work.

Thanks in advance!

---

### Post by drs305 on 2009-01-22
Try this for troubleshooting. Of course, I am relying on the comments that they really are sdb1 and sdb5. Comments are static so they aren't necessary accurate:
```

sudo umount /dev/sdb1 /dev/sdb5

```


Reverse the mount points in fstab - try changing the mount point for sdb1 to hangar and sdb5 to warehouse. If sdb1 now mounts and sdb5 doesn't, it's probably a problem with your mount point (typo, doesn't exist, etc)

If sdb5 mounts but sdb1 still doesn't, it's probably a problem with the sdb5 partition, bad UUID, etc.

When I copy/paste it shows a space between warehouse and ext3 but when I see it on screen it sure looks different than the space between hangar and ext3. I could be my fonts but you might try adding an additional space before ext3.

Here are a few commands to run:
```

sudo blkid -c /dev/null | grep "sdb[15]"  # make sure the UUID is correct
ls -lad /media/warehouse /media/hangar    # everything looks ok, partitions found?
sudo fdisk -l | grep "sdb[15]"            # formatted correctly?

```

Format for UUIDs correct, complete UUID, since not posted?
UUID=XXX-XXX...

Instead of comparing UUIDs, you can replace it temporarily with the /dev/sdb1 to see if that works.

---

### Post by Nevyn on 2009-01-22
Thanks for the help with the thorough debug. The 
```
sudo blkid -c /dev/null | grep "sdb[15]"
```
made me realize that for whatever odd reason, sdb1 was formatted in ext2. I was dead sure it was in ext3 and missed it completely.

Thanks for the help and effort! :KS

---


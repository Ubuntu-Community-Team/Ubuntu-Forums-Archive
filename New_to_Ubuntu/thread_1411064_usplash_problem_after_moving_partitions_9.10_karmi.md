---
title: "usplash problem after moving partitions 9.10 karmic"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by trikster_x on 2010-02-19
Hello fantastic forum friends!  I have run into a small problem...

I recently removed the partition that had Hardy on it after a successful test run of Karmic on my Aspireone netbook.  Once this was done, I did a little partition finagling to organize my hard drive a bit for future distro installs.  Basically this involved absorbing the now unallocated space into the extended partition and growing and moving the partition that Karmic is located on.  

I have done this in the past with other had drives, for various reasons, and never had a problem once I updated /etc/fstab with the new UUID for the reorganized partitions.  But for some reason, this time I can't get the usplash screen to come back up.  Usplash starts normally with the progress bar moving back and forth, but as soon as you would expect it to start filling, it disappears and I am left with a verbose output.  Is there a different method for fixing this in Karmic, compared to Hardy?  Or am I running into a different problem?

I'll include my /etc/fstab and blkid output since I am sure the first conclusion for most is that I made an error with the UUIDs.

```
triksterx@triksterx-laptop:~$ sudo blkid
/dev/sda1: LABEL="PQSERVICE" UUID="0159-6699" TYPE="vfat" 
/dev/sda2: UUID="B6F06EB8F001C7B1" LABEL="ACER" TYPE="ntfs" 
/dev/sda5: UUID="dbaa6763-3b55-4558-b91f-f00e96deb6d1" TYPE="swap" 
/dev/sda6: UUID="ec4c90f8-12be-4021-a011-0d1a3a784ba9" TYPE="ext4" 
/dev/sda7: LABEL="/home" UUID="2ea0cc3b-064b-4625-a882-966691455a4a" TYPE="ext4"
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=ec4c90f8-12be-4021-a011-0d1a3a784ba9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=dbaa6763-3b55-4558-b91f-f00e96deb6d1 none  swap sw           0 0

UUID=2ea0cc3b-064b-4625-a882-966691455a4a /home ext4 nodev,nosuid 0 2
```

Any help is appreciated.

---

### Post by Dies on 2010-02-19
Did you update /etc/initramfs-tools/conf.d/resume?

---

### Post by trikster_x on 2010-02-19
Works perfectly now.  Thanks for the heads up Dies :)

---


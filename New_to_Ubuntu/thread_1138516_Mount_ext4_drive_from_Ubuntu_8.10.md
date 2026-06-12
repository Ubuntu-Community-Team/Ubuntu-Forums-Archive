---
title: "Mount ext4 drive from Ubuntu 8.10?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by looi76 on 2009-04-26
Hi, I have installed a fresh copy of Ubuntu 9.04 with ext4 filesystem. Now, When I'm using Ubuntu 8.10 I am not able to mount Ubuntu 9.04 drive since it is in ext4 format. What is the solution to this problem?
[[IMG]http://img87.imageshack.us/img87/18/screenshoterror.th.png[/IMG]   ](http://img87.imageshack.us/my.php?image=screenshoterror.png)[[IMG]http://img6.imageshack.us/img6/439/93637891.th.png[/IMG]](http://img6.imageshack.us/my.php?image=93637891.png)

---

### Post by Sealbhach on 2009-04-26
I don't think it can be done as 8.10 does not know what to do with an ext4 filesystem.


.

---

### Post by wizard10000 on 2009-04-26
> **Sealbhach said:**
> I don't think it can be done as 8.10 does not know what to do with an ext4 filesystem.

Depends on how the ext4 filesystem was created.  looi, try mounting it as ext3 - if it doesn't work it won't work.

ext4 is backwards compatible with ext3 as long as extents aren't enabled - but they are enabled by default.  Give it a try.

---

### Post by looi76 on 2009-04-26
How can I mount it as **ext3**?

---

### Post by Spiritous on 2009-04-26
I'd recommend using the Update Tool as 9.04 can handle EXT4 Better... 8.10 is hopeless

---

### Post by wizard10000 on 2009-04-26
> **looi76 said:**
> How can I mount it as **ext3**?

sudo mount -t ext3 device mount.point

So if your device was sdb1 and your mount point was /mnt/external_drive it'd be

sudo mount -t ext3 /dev/sdb1 /mnt/external_drive

You'll need to create the mount point, though - and only root can mount or unmount a drive this way.

To unmount it it's

sudo umount /dev/sdb1

Notice there's no "n" in umount.

---

### Post by Peasantoid on 2009-04-26
GParted in Hardy/Intrepid sees ext4 as ext3. Perhaps that indicates it's compatible.

---

### Post by dvo on 2009-05-22
There is at least experimental support for ext4,
which does work for my Ubuntu 8.04 installation.

Make sure that the ext4dev module is loadable into your kernel. Then try 
```
sudo mount -t ext4dev /dev/sdb1 /mnt/external_drive
```
If this does not work and /var/log/messages reports:
[FONT="Courier New"]EXT4-fs: dm-1: not marked OK to use with test code[/FONT] 
then
```
tune2fs -E test_fs /dev/sda3
```
and retry the mount.
See also [http://fedoraproject.org/wiki/FedoraExt4]("http://fedoraproject.org/wiki/FedoraExt4")

---


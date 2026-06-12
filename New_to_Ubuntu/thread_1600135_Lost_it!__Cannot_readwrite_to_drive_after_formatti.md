---
title: "Lost it!  Cannot read/write to drive after formatting"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by ianc1 on 2010-10-18
I just formatted my Western Digital drive (1TB Elements external hard drive) to EXT4 from NTFS using gparted.  I simply asked it to change the format of the partition to EXT4.

Before I did this I could write and read from the drive.  Now I can open it but cannot write to it.  Permissions tells me its owned by root.

Help.....

Any ideas.

Thanks

Ian

---

### Post by sandyd on 2010-10-18
> **ianc1 said:**
> I just formatted my Western Digital drive (1TB Elements external hard drive) to EXT4 from NTFS using gparted.  I simply asked it to change the format of the partition to EXT4.

Before I did this I could write and read from the drive.  Now I can open it but cannot write to it.  Permissions tells me its owned by root.

Help.....

Any ideas.

Thanks

Ian
mount it.

post output of
```

mount -l
```

---

### Post by ianc1 on 2010-10-18
Thanks Sandyd.  I took the plunge and tried reformatting with the disk utility in System>Administration menu.  Using this I had an option to take ownership of the partition - I assume that this was something I missed or didn't understand in gparted.

The simplified output of mount -l now yields:

/dev/sdd1 on /media/1E72-41A3 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc1 on /media/Harold type ext4 (rw,nosuid,nodev,uhelper=udisks) [Harold]

with sdc1 [Harold] being the 1TB drive.  Do these parameters look OK?  I can now read and write to this drive.

For future reference how should I have taken ownership of the partition in gparted?

Thanks

Ian

---

### Post by ianc1 on 2010-10-19
Hi all

Quick query regarding my gparted error.  It appears after formatting a partition using gparted GUI that do not have read/write etc privileges on this partition.  Firstly is this usual to have to take ownership afterwards?

If /dev/sdc1 is the external USB drive will the following code give me the correct privelages and will these be retained each time I plug the device in?

```
sudo chown -R USERNAME:USERNAME /dev/sdc1
```Thanks

---


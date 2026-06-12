---
title: "Accessing other partitions"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by jhapk on 2009-07-06
Hi,

I had a openSuse on my computer. I replaced it by Ubuntu in the same partition as openSuse, reformatting it and using a ext3 file system. But I am not able to access my 
other partitions which had all my data.
When I type "df" on the command line, I get:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda9             11487868   3464600   7439712  32% /
tmpfs                   238076         0    238076   0% /lib/init/rw
varrun                  238076       108    237968   1% /var/run
varlock                 238076         0    238076   0% /var/lock
udev                    238076       164    237912   1% /dev
tmpfs                   238076       132    237944   1% /dev/shm
lrm                     238076      2192    235884   1% /lib/modules/2.6.28-13-generic/volatile

However, I can access my other hard drives from the menu bar by
"Places -> Removable Media".

Any suggestions how can I access it using command line?

Thanks

---

### Post by cariboo on 2009-07-06
You can manually mount your other partitions eg:

```
sudo mount /dev/sda8 /media/disk
```

You will also have to create mount points in /media

```
sudo mkdir /media/data
```

You can also mount the partitions on boot by using /etc/fstab

```
# second partition /dev/sda4
UUID=7911a1c9-3c28-4a63-80c7-9cb6607b81eb /home/storage	ext4	relatime	0 0
```

---

### Post by Elfy on 2009-07-06
Add them to fstab so they mount at boot - there are a few ways of accomplishing it - edit fstab to add them, or you can use ntfs-config and pysdm if you want GUI methods of doing it.

Fstab - [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

The other 2 need installing.

If you need more help then post back.

---

### Post by Narcolepsy06 on 2009-07-06
My first guess is, you need to add them to the fstab file.  
Which is layed out here: 
[How to fstab]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by jhapk on 2009-07-07
Hi,

I edited the /etc/fstab and it now mounts the partitions fine. It looks like this:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=b451f4ea-89b4-46a7-9c2e-f14254b59055 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /chile    auto    defaults        0       0                 
/dev/sda3       /zambia   auto    defaults        0       0
/dev/sda6       /mongolia auto    defaults        0       0
/dev/sda7       /pitcairn auto    defaults        0       0
/dev/sda8       /moldova  auto    defaults        0       0

But I am getting the following two issues. 


1) On all my partitions, I am not able to write/delete files without sudo.
2) On my partition /dev/sda8 when I try to delete anything, it doesn't do it and says its a "Read-Only file system"

the output for my  "$sudo blkid" is:
/dev/sda1: UUID="0ba2e04c-aaf6-4a2c-a0a4-4676a404a094" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: TYPE="swap" 
/dev/sda3: UUID="F41E-DC63" TYPE="vfat" 
/dev/sda5: UUID="637691bc-0604-4d99-9959-cf903cde7a2f" TYPE="reiserfs" 
/dev/sda6: LABEL="NEW VOLUME" UUID="202E-B3EC" TYPE="vfat" 
/dev/sda7: LABEL="NEW VOLUME" UUID="6C38-F28B" TYPE="vfat" 
/dev/sda8: LABEL="NEW VOLUME" UUID="A84E-ED3A" TYPE="vfat" 
/dev/sda9: UUID="b451f4ea-89b4-46a7-9c2e-f14254b59055" TYPE="ext3" 

any insights on the two problems?

Thanks

---


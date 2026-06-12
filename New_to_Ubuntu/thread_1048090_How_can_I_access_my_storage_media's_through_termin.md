---
title: "How can I access my storage media's through terminal?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by feras.ws on 2009-01-23
Dear Members:

I would like to ask you about how can I access the storage media's in my computer using the terminal? because I changed the permissions for my root and installed a new Ubuntu , and I don't know how to restore my old Ubuntu .

Regards
Feras

---

### Post by hyper_ch on 2009-01-23
post the output of
```

sudo fdisk -l

```

```

df -h

```

```

cat /etc/fstab

```

---

### Post by feras.ws on 2009-01-23
Ok 
*sudo fdisk -l*

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79a9e71f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2   *         192       10941    86341632    7  HPFS/NTFS
/dev/sda3           10941       15665    37945530    7  HPFS/NTFS
/dev/sda4           15666       19457    30459240    5  Extended
/dev/sda5           15666       16029     2923798+  82  Linux swap / Solaris
/dev/sda6           16030       17245     9767488+  83  Linux
/dev/sda7           17246       18096     6835626   83  Linux
/dev/sda8           18097       19457    10932201   83  Linux

```
*df -h*
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              11G  2.4G  7.4G  25% /
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M  108K 1008M   1% /var/run
varlock              1008M  4.0K 1008M   1% /var/lock
udev                 1008M  2.8M 1005M   1% /dev
tmpfs                1008M  152K 1008M   1% /dev/shm
lrm                  1008M  2.0M 1006M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0             699M  699M     0 100% /media/cdrom0
/dev/sda6             9.2G  4.0G  4.8G  46% /media/disk
/dev/sda2              83G   48G   36G  58% /media/Vista
/dev/sda3              36G   23G   13G  66% /media/New Volume


```
*cat /etc/fstab*
```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=00961ce7-3aae-40b1-86f9-8ff865eea609 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ad534cf0-826a-475d-b6d4-61f849a8e9e1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


```

Regards
Feras

---

### Post by hyper_ch on 2009-01-23
what do you try to access? I see that all partitions are mounted (at some place) except for /dev/sda7.

What other storage device are you refering to?

---


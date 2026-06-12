---
title: "Can't mount hdb"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by cartisdm on 2009-01-21
I formatted my second harddrive AFTER I installed Mythbuntu 8.10 to ext3 using Gparted.  However, I can't seem to find this harddrive mounted when I boot up.  I keep running out of space watching TV with just my first harddrive so MythTV keeps crashing on me.

If I run a liveCD, both hda and hdb harddrives will mount and I can access them.  I don't see it anywhere when I'm actually in Mythbuntu though.  I've looked in the same folder that mounts the cd1 and cd1 drives (I can't remember what it is off the top of my head,    /media?   or   /mnt?) but I don't see it.  I also don't see it listed on the left side of the window where the other drives should be.

---

### Post by taurus on 2009-01-21
I assume you don't have an entry in /etc/fstab for your second harddrive so it would mount automatically each time you boot Ubuntu.  Open a terminal and post the outputs of these commands.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by cartisdm on 2009-01-21
sudo fdisk -1

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x117a117a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1287    10337796   83  Linux
/dev/sda2            1288        4865    28740285    5  Extended
/dev/sda5            1288        1397      883543+  82  Linux swap / Solaris
/dev/sda6            1398        4865    27856678+  83  Linux

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc82cc82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14589   117186111   83  Linux

```

sudo blkid
```

/dev/sda1: UUID="7c564dd7-3f3f-42aa-846a-21be3305eb6f" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="f1ad6f09-46f1-44f8-aa1a-8f4628c5b1ff" 
/dev/sda6: UUID="499d6a18-320d-4034-8cc6-68f4a78126da" TYPE="xfs" 
/dev/sdb1: UUID="824ba47d-4e50-4449-9b1a-19c848dc32bf" SEC_TYPE="ext2" TYPE="ext3" 
```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7c564dd7-3f3f-42aa-846a-21be3305eb6f /               ext3    errors=remount-ro 0       1
# /dev/sda6
UUID=499d6a18-320d-4034-8cc6-68f4a78126da /var/lib        xfs     defaults        0       2
# /dev/sda5
UUID=f1ad6f09-46f1-44f8-aa1a-8f4628c5b1ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.8G  9.7G     0 100% /
tmpfs                 759M     0  759M   0% /lib/init/rw
varrun                759M  372K  759M   1% /var/run
varlock               759M     0  759M   0% /var/lock
udev                  759M  2.9M  756M   1% /dev
tmpfs                 759M     0  759M   0% /dev/shm
lrm                   759M  2.0M  757M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6              27G   26G  945M  97% /var/lib
overflow              1.0M   16K 1008K   2% /tmp

```

---

### Post by taurus on 2009-01-21
Edit /etc/fstab and add this line to the end of it.

```
UUID=824ba47d-4e50-4449-9b1a-19c848dc32bf   /media/share   ext3   defaults   0   2
```
Save the change.  Then, create a new mount point and mount it, assuming you want to mount it to /media/share.

```
sudo mkdir /media/share
sudo mount -a
df -h
```

Meanwhile, clean out your cache to make some room on / so you are able to log in.

```
sudo apt-get clean
df -h
```

---

### Post by cartisdm on 2009-01-21
It works prefect now and now I can finally watch TV!

---

### Post by bleedpurple on 2009-01-25
I tried to follow the procedure here but ran into a few issues.  First I couldn't save the etc/fstab file.  I tried sudo gedit and that seemed to work.  

The result of df-h is:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G  7.4G  130G   6% /
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   52K  506M   1% /dev
devshm                506M   48K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-23-generic/volatile
/dev/sdb1              19G   44M   18G   1% /media/linuxb

the result of sudo blkid is:

/dev/sda1: UUID="db0898c0-1a52-4eaf-9bda-a67137a3264f" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="c5b1b34c-97b3-4f26-9f1c-7f93c5f47d72" 
/dev/sdb1: UUID="afe4417b-f0d6-4817-a19d-1d97fdd43fa1" TYPE="ext2" 

the result of cat /etc/fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=db0898c0-1a52-4eaf-9bda-a67137a3264f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c5b1b34c-97b3-4f26-9f1c-7f93c5f47d72 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
UUID=afe4417b-f0d6-4817-a19d-1d97fdd43fa1 /media/linuxb   ext2

For some reason the /dev/hdb1 is not showing up here.  

The result of sudo fdisk -l is:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007f4e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe7bbe7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2434    19551073+  83  Linux

---


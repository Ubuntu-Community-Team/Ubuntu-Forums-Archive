---
title: "External hard drive gone after 10.04LTS upgrade"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by ehpmail on 2010-05-02
Hi,

Somebody configured my external hard drive to my computer. I could access it by doing Places -> External

After the upgrade today, i get an error: Unable to mount external
mount: wrong fs type, bad option, bad superblock on //external/share, missing codepage or helper program, or other error (for several filesystems (e.g. nfs, cifs) you might need a /sbin/mount.<type> helper program) In some cases useful info is found in syslog - try dmesg | tal or so

---

### Post by championboxes on 2010-05-02
could you please paste the output of these two commands
```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by ehpmail on 2010-05-02
fdisk:
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70fa70fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       30400   223215142+   f  W95 Ext'd (LBA)
/dev/sda5            2612        2872     2096451   82  Linux swap / Solaris
/dev/sda6            2873        6788    31455238+  83  Linux
/dev/sda7            6789       30400   189663358+   b  W95 FAT32

fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=c38f9f60-0b75-4475-b3bb-19e26f0b47a7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=C86CEC2C6CEC174A /home/eldonp/windows ntfs    defaults,umask=000,gid=46 0       0
# /dev/sda5
UUID=24a68d06-63fb-4451-b91d-16a226d390ba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda7
//external/morpheus  /home/eldonp/external  cifs  user,password=******,uid=1000,iocharset=utf8,gid=1000,username=eldonp  0  0
/dev/sda7  /home/eldonp/documents  vfat  uni_xlate,uid=1000,iocharset=utf8,gid=1000  0  0

---

### Post by championboxes on 2010-05-02
> **ehpmail said:**
> fdisk:
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70fa70fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       30400   223215142+   f  W95 Ext'd (LBA)
/dev/sda5            2612        2872     2096451   82  Linux swap / Solaris
/dev/sda6            2873        6788    31455238+  83  Linux
/dev/sda7            6789       30400   189663358+   b  W95 FAT32

fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=c38f9f60-0b75-4475-b3bb-19e26f0b47a7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=C86CEC2C6CEC174A /home/eldonp/windows ntfs    defaults,umask=000,gid=46 0       0
# /dev/sda5
UUID=24a68d06-63fb-4451-b91d-16a226d390ba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda7
//external/morpheus  /home/eldonp/external  cifs  user,password=******,uid=1000,iocharset=utf8,gid=1000,username=eldonp  0  0
/dev/sda7  /home/eldonp/documents  vfat  uni_xlate,uid=1000,iocharset=utf8,gid=1000  0  0

I am assuming that /dev/sda7 (the fat32 drive) is your external...

I am not sure if this will work but you can try

first make a backup of your current fstab
```
sudo cp /etc/fstab /etc/fstab.backup
```

next open up the current fstab with a txt editor (replace with your favorite)
```
gksudo gedit /etc/fstab
```

remove the last two lines and replace with
```
/dev/sda7 /media/External vfat rw,uid=1000,gid=1000 0 0
```
save and exit after adding this line to the end
this line should make your external drive mount to /media/External

next you need to make the folder /media/External and own it
```
sudo mkdir /media/External
```
own it ```
sudo chown yourusername:yourusername /media/External
```

then restart...
this should help you but if it doesnt I dont know how to fix it...
If this doesnt work remove the edited fstab and replace it with the backup with these two commands
```
sudo rm /etc/fstab
sudo mv /etc/fstab.backup /etc/fstab
```

---

### Post by ehpmail on 2010-05-04
thanks alot. i tried, but had to roll back! :(

---


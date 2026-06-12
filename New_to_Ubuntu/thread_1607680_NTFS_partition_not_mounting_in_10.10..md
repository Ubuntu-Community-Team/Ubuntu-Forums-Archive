---
title: "NTFS partition not mounting in 10.10."
date: 2010-10-28
forum: New to Ubuntu
---

### Post by SarcasmOrgasm on 2010-10-28
I'm getting an error when I go into disk manager. I can't seem to find a good answer to mounting NTFS partitions on google. I just installed ubuntu recently, so I'm pretty new to linux. I'm starting to get a feel for the terminal and other things, and love it so far. But, I'm totally lost on getting this partition to show up. Here is the error I'm getting(this is through disk manager):

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed

Thanks in advance

---

### Post by garvinrick4 on 2010-10-28
Open a terminal and see what is mounted already?
```
cat /etc/mtab
```

---

### Post by bioterror on 2010-10-28
> **SarcasmOrgasm said:**
> I'm getting an error when I go into disk manager. I can't seem to find a good answer to mounting NTFS partitions on google. I just installed ubuntu recently, so I'm pretty new to linux. I'm starting to get a feel for the terminal and other things, and love it so far. But, I'm totally lost on getting this partition to show up. Here is the error I'm getting(this is through disk manager):

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed

Thanks in advance

Seems like you have two drives?
Linux is on sdb (becouse it says / )and something else is on sda.

you can say in terminal "dmesg |grep sd" and it shows you the drives which kernel sees.

And if you want to see your mounted partitions, you can say in terminal "df -h" and it shows you device, where it's mounted and the disk usage in human readable format.

---

### Post by SarcasmOrgasm on 2010-10-28
```
dmesg |grep sd
[    1.868529] sd 1:0:1:0: Attached scsi generic sg0 type 0
[    1.868623] sd 1:0:1:0: [sda] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    1.868646] sd 1:0:1:0: [sda] Write Protect is off
[    1.868648] sd 1:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.868658] sd 1:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.868777]  sda: sda1 sda2
[    1.886090] sd 1:0:1:0: [sda] Attached SCSI disk
[    2.120690] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.120765] sd 6:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.120789] sd 6:0:0:0: [sdb] Write Protect is off
[    2.120791] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.120801] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.120871]  sdb: sdb1 sdb2 < sdb5 >
[    2.157816] sd 6:0:0:0: [sdb] Attached SCSI disk
[    3.397812] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
[    3.397816] EXT4-fs (sdb1): write access will be enabled during recovery
[    3.761469] EXT4-fs (sdb1): orphan cleanup on readonly fs
[    3.761476] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 262321
[    3.761527] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 262297
[    3.917439] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 262189
[    3.917492] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 262251
[    3.918294] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 262238
[    3.918326] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 262249
[    3.918334] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 262265
[    3.918343] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 262303
[    3.918350] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 262203
[    3.918358] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 262255
[    3.918365] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 262165
[    3.918377] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 2365731
[    3.918399] EXT4-fs (sdb1): 12 orphan inodes deleted
[    3.918402] EXT4-fs (sdb1): recovery complete
[    4.089575] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    6.936867] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[   12.962879] type=1400 audit(1288247356.931:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1056 comm="apparmor_parser"
[   21.594320] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
[   26.126907] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0


```

The partition was labeled as /dev/sda1 in disk utility and yes I have a 160gb hdd where I install my OS's to, and a 1.5tb hdd where I save media

---

### Post by SarcasmOrgasm on 2010-10-28
Also, when I run "cat /etc/mtab" and "df -h" I only see /dev/sdb(x) partitions showing up.

---

### Post by bioterror on 2010-10-28
okay, let's try this way in terminal.

```

cd /media
sudo mkdir Windows (or whatever you want it to be called)
sudo umount /dev/sdb1
sudo mount.ntfs-3g /dev/sdb1 /media/Windows
```

---

### Post by SarcasmOrgasm on 2010-10-28
> **bioterror said:**
> okay, let's try this way in terminal.

```

cd /media
sudo mkdir Windows (or whatever you want it to be called)
sudo umount /dev/sdb1
sudo mount.ntfs-3g /dev/sdb1 /media/Windows
```

Great! I got it to work. Thanks so much for your help. That gives me a better understanding of mounting partitions now too. One last question though, will I have to remount it everytime I boot? Or, by doing that, will it show up from now on?

---

### Post by bioterror on 2010-10-28
> **SarcasmOrgasm said:**
> Great! I got it to work. Thanks so much for your help. That gives me a better understanding of mounting partitions now too. One last question though, will I have to remount it everytime I boot? Or, by doing that, will it show up from now on?

you can edit /etc/fstab -files to add it to mount.
It's suitable to do with UUID.

with gparted application (sudo apt-get install gparted) you can easily dig out the UUID of the partition.

then it will be like this kind of line

```
UUID=13123123-1231231-123123 /media/Windows ntfs-3g defaults   0    0
```

---

### Post by rustyboy on 2011-01-22
> **bioterror said:**
> okay, let's try this way in terminal.

```

cd /media
sudo mkdir Windows (or whatever you want it to be called)
sudo umount /dev/sdb1
sudo mount.ntfs-3g /dev/sdb1 /media/Windows
```

You are a legend. This simple explanation helped me manually mount my ntfs partitions in Xfce whereas all the googling I did turned up convoluted, hard-to-follow explanations. Thanks! :D

---

### Post by DocNaq on 2011-02-19
I tried to do the umount and I get the error.. 

umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof( 8 ) or fuser(1))

---

### Post by Morbius1 on 2011-02-19
Because despite everyone saying that this woks:
> cd /media
sudo mkdir Windows (or whatever you want it to be called)
**[COLOR=Blue]sudo umount /dev/sdb1[/COLOR]**
sudo mount.ntfs-3g /dev/sdb1 /media/WindowsThe umount command in this example is impossible. One doesn't umount a device ( /dev/sdb1 ) one umounts a mount point.

Find out what the current mount point is for sdb1 and "umount" that.

[COLOR=Blue]EDIT: Perhaps a example would be helpful:[/COLOR]
If you run the following command:
```
mount
```You will get among other things a line that looks something like this:
> /dev/sdb1 on /media/BACKUP type fuseblk ..... /dev/sdb1 is the device
/media/BACKUP is the mount point

So to unmount the mount point from the device:
```
sudo umount /media/BACKUP
```

---


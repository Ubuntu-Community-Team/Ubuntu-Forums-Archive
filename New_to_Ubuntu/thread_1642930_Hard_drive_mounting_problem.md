---
title: "Hard drive mounting problem"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by element_921 on 2010-12-11
Hi,
I am new to this forum. I recently installed ubuntu 10.10 on my laptop. After that i installed ntfs-config to auto mount drives during startup, however when i tried to start the program(ntfs-config), it would not run(i tried 3-4 times) and after that i cannot see my ntfs drive, though i cant the rest of the drives. I cannot find the details of that drive in fstab, but can find the details in fdisk -l. I am posting the outputs of both here. i don't want to format the drive as it has got some imp info.

---

### Post by sikander3786 on 2010-12-11
Instead of attaching the text files, directly copy/paste the text between your Terminal and your post. We need the output of these commands,

```
cat /etc/fstab
```

```
sudo blkid
```

While posting, click the # icon in post menu and paste your text in between the generated code tags.

And yes, I too had problems running NTFS-Config on Maverick but never bothered to find a solution. /etc/fstab entry is a safer choice ;-)

---

### Post by element_921 on 2010-12-11
Thanks for the reply. Here are the outputs.

fstab:

UUID=93c7eeac-1862-496d-884d-dd8269d35563  /swap        swap  sw        0  0  
UUID=74c83677-eed7-4455-bb8d-0d66c5745f83  /            ext4  defaults  0  1  

/dev/sda1                                  /media/sda1  ext4  defaults  0  0 

blkid:

/dev/sda1: LABEL="Cyrus" UUID="dfcc6ee8-4a3f-4314-a9a3-426bee1f375a" TYPE="ext4" 
/dev/sda6: UUID="93c7eeac-1862-496d-884d-dd8269d35563" TYPE="swap" 
/dev/sda7: UUID="74c83677-eed7-4455-bb8d-0d66c5745f83" TYPE="ext4"

---

### Post by element_921 on 2010-12-11
Output of fdisk-l : 

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b19e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1339    10755486   83  Linux
/dev/sda2            1340        7298    47854593    f  W95 Ext'd (LBA)
/dev/sda5            1462        6560    40957717+   7  HPFS/NTFS
/dev/sda6            1340        1461      974848   82  Linux swap / Solaris
/dev/sda7            6561        7298     5920768   83  Linux

Partition table entries are not in disk order

---

### Post by sikander3786 on 2010-12-11
UUID for /dev/sda5 is not listed there?

Once you find that, your entry for NTFS in fstab would look like this.

```
UUID=xxxxxxxxxxxx    /mount/point    ntfs-3g    defaults,utf8,umask=007,uid=1000,gid=1000 0 1
```

Where UUID= UUID for sda5 and /mount/point is your desired mount point.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by element_921 on 2010-12-11
Thanks for the help sikander3786, but i'm having difficulty in finding uuid of ntfs partition. I tried using the commands "blkid" and "-l /dev/disk/by-uuid", but i cannot find the uuid of that drive.. caan you help me with this...

---

### Post by element_921 on 2010-12-11
Thanks for the help sikander3786, but i'm having difficulty in finding uuid of ntfs partition. I tried using the commands "blkid" and "-l /dev/disk/by-uuid", but i cannot find the uuid of that drive.. can you help me with this...

---

### Post by 1991sudarshan on 2010-12-11
To auto mount the hard disk partitions i would suggest you to use **mount manager**.With the help of it you can easily auto mount the partitions at the system startup!!!

---

### Post by amjjawad on 2010-12-11
The best way to auto mount is: [http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

IMHO :)

---

### Post by element_921 on 2010-12-11
Thanx for the replies guys...

---

### Post by amjjawad on 2010-12-11
> **element_921 said:**
> Thanx for the replies guys...

You welcome :)
Is it solved or not yet?

---


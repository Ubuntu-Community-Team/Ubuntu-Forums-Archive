---
title: "Incorrect Disc Usage"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by DGINSD on 2011-09-04
I had always thought my Ubuntu system consumed too much of my disc space and I think I've found out why and need some help correcting it. I have an 80G hard drive with my Windows XP training wheels occupying approximately half the drive on a primary partition (41G)
 on a 39G extended I have 2 logical drives / mounted on a 15G and Home mounted on a 23G.

If I open up the System Monitor in the file system tab it shows that I have 80% of my / directory full. But then if I open up the Disc Usage Analyzer and add up all the directory's under root excluding home I only come up with 4.235G which is not even a third of the 15G set up for /.

What I've determined is somehow my system is not understanding that the Home directory is on another partition and is counting the 7.2G of space used in my home partition as space also used in my / partition.

So when my system is telling me I don't have enough space in tmp to copy a DVD cause there's only 2.6G available it's incorrect because in reality there's 10.75G.

So what is it that I have set up wrong, how do I tell my system Home is mounted on another partition and not to count its usage against the / partition?

---

### Post by TeoBigusGeekus on 2011-09-04
You'll need to edit your fstab file.
Can you mount your extra home partition and post us the output of
```
sudo blkid
```
```
mount
```
```
sudo fdisk -l
```
and 
```
nano /etc/fstab
```
?

---

### Post by DGINSD on 2011-09-04
My home partition mounts at boot, this is whats odd but for some reason the size of the home partitions usage (7.2G) is counted against the / directory as well as the home partition.

So here's the output of those commands, maybe some insight into whats going on can be gathered.

```
david@david-Inspiron-1150:~$ sudo blkid
[sudo] password for david: 
/dev/sda1: UUID="4070AFE270AFDCC2" TYPE="ntfs" 
/dev/sda5: UUID="be2872cb-1797-4ab9-8d09-feb1af9b9821" TYPE="ext4" 
/dev/sda6: UUID="fe0f9938-e79d-41a0-8ec4-f73b0b510469" TYPE="ext4" 
/dev/sda7: UUID="802a40f7-3124-4da6-aa89-9761209afa98" TYPE="swap" 

david@david-Inspiron-1150:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sda6 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
/dev/sda1 on /media/4070AFE270AFDCC2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

david@david-Inspiron-1150:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70486fc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4961    39848928+   7  HPFS/NTFS
/dev/sda2            4962        9730    38300673    5  Extended
/dev/sda5            4962        6789    14681088   83  Linux
/dev/sda6            6789        9531    22023168   83  Linux
/dev/sda7            9531        9730     1594368   82  Linux swap / Solaris

fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=be2872cb-1797-4ab9-8d09-feb1af9b9821 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=fe0f9938-e79d-41a0-8ec4-f73b0b510469 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=802a40f7-3124-4da6-aa89-9761209afa98 none            swap    sw              0       0


```

Lots O info, hope it shows something, thank u for the help.

---

### Post by TeoBigusGeekus on 2011-09-04
Can you also post the output of
```
df -h
```
?

---

### Post by DGINSD on 2011-09-04
Here you go...

```
david@david-Inspiron-1150:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              14G   11G  2.7G  81% /
none                  334M  244K  334M   1% /dev
none                  342M  900K  342M   1% /dev/shm
none                  342M   88K  342M   1% /var/run
none                  342M     0  342M   0% /var/lock
none                   14G   11G  2.7G  81% /var/lib/ureadahead/debugfs
/dev/sda6              21G  7.5G   13G  38% /home
/dev/sda1              39G   17G   22G  43% /media/4070AFE270AFDCC2

```

---

### Post by TeoBigusGeekus on 2011-09-04
Strange, very strange...
Another output I'd like to see
```
cd /
du -h --max-depth=1 2>/dev/null
```

---

### Post by DGINSD on 2011-09-04
If you wouldn't mind a brief explaination of this

```

none                  334M  244K  334M   1% /dev
none                  342M  900K  342M   1% /dev/shm
none                  342M   88K  342M   1% /var/run
none                  342M     0  342M   0% /var/lock
none                   14G   11G  2.7G  81% /var/lib/ureadahead/debugfs
```

---

### Post by DGINSD on 2011-09-04
Took a while for my machine to figure this one out but here it is.

```
david@david-Inspiron-1150:/$ du -h --max-depth=1 2>/dev/null
3.6G	./usr
16K	./lost+found
306M	./var
4.0K	./opt
335M	./lib
4.0K	./mnt
0	./sys
4.0K	./cdrom
16M	./etc
856K	./dev
4.0K	./srv
7.7M	./sbin
6.6M	./bin
16G	./media
56K	./tmp
66M	./boot
7.3G	./home
4.0K	./selinux
4.0K	./root
0	./proc
28G	.

```

I may not be able to post back real soon, going to eat a late breakfast, but I'll reply as soon as I can.

---

### Post by TeoBigusGeekus on 2011-09-04
> **DGINSD said:**
> If you wouldn't mind a brief explaination of this

```

none                  334M  244K  334M   1% /dev
none                  342M  900K  342M   1% /dev/shm
none                  342M   88K  342M   1% /var/run
none                  342M     0  342M   0% /var/lock
none                   14G   11G  2.7G  81% /var/lib/ureadahead/debugfs
```

Ignore the first 4 entries; the last one though seems suspicious.
It looks like a bug:
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/499773]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/499773")
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/736512]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/736512")
...but everyone says to ignore it and that a simple update should resolve it.
Otherwise, I don't know what to say; your fstab file seems fine.
Try this:
```
gksu gedit /etc/fstab
```
Change this line
```
UUID=fe0f9938-e79d-41a0-8ec4-f73b0b510469 /home           ext4    defaults        0      2
```
to 
```
UUID=fe0f9938-e79d-41a0-8ec4-f73b0b510469 /home           ext4    relatime        0      2
```
Reboot and check again.
Sorry, I've run out of ideas...

---

### Post by DGINSD on 2011-09-04
I did as you instructed, but no change.

So strange everything shows that the system knows Home is on a separate partition but it seems to count home twice.

---


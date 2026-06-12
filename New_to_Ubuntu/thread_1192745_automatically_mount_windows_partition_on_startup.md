---
title: "automatically mount windows partition on startup"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by dimapitt on 2009-06-20
As You have probably noticed with my question I am a complete Ubuntu newb. I just got 9.04 about 2 days ago. This hasn't been a huuge deal but I figured it's easier to have the partition automatically mounted on startup rather than having to open it every time i want to play music (all my music is on the other partition). So what do I do to have it mount on startup?

Don't make fun of me too much for this stupid question:p.

---

### Post by TeoBigusGeekus on 2009-06-20
Open a terminal and post us the results of 
```
blkid
```
and 
```
sudo fdisk -l
```
that's L.

Then post us the contents of your fstab file
```
gksudo gedit /etc/fstab
```

---

### Post by dimapitt on 2009-06-20
dev/sda1: UUID="8A6A8DEF6A8DD7F9" LABEL="SERVICEV003" TYPE="ntfs" 
/dev/sda2: UUID="78BA90B6BA90727C" LABEL="SW_Preload" TYPE="ntfs" 
/dev/sda3: UUID="1f5d3df5-40fc-4821-bb5b-c1a26b55a4ec" TYPE="ext3" 
/dev/sda4: UUID="37b05472-a6cd-432f-a217-a678d3174c23" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

(it's SW_Preload that i want mounted.)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd17e1738

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       18183   144511996    7  HPFS/NTFS
/dev/sda3           18184       19398     9759487+  83  Linux
/dev/sda4           19399       19457      473917+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         984      991747+   6  FAT16


here's the fstab (what is this exactly?) edit: actually It looks like it's what the system mounts.. I added /dev/sda2 in there as a comment. not sure what the rest is haha.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=1f5d3df5-40fc-4821-bb5b-c1a26b55a4ec /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=37b05472-a6cd-432f-a217-a678d3174c23 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by TeoBigusGeekus on 2009-06-20
The fstab is a file that does exactly what you want - it holds information about which drives should be mounted upon startup.
Mount your ntfs partition and post the output of 
```
mount
```
as well.

---

### Post by Mark Phelps on 2009-06-20
Just be aware that if your Windows partition encounters any problems (as in a bad shutdown), having it mounted automatically using FSTab could prevent Ubuntu startup.  

In my experience, it's better to NOT mount it automatically and just click the icon in Places whenever I need it.

---

### Post by dimapitt on 2009-06-20
dima@dima-laptop:~$ mount
/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/dima/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dima)
/dev/mmcblk0p1 on /media/READY_BOOST type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda2 on /media/SW_Preload type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
dima@dima-laptop:~$

---

### Post by dimapitt on 2009-06-20
oh.. crud.. that doesn't sound good O.o. I guess the extra click might save me some huuge problems in the future. Can it really prevent an Ubuntu Startup :(.

---

### Post by TeoBigusGeekus on 2009-06-20
Keeping in mind what Mark Phelps wrote, add this line in your fstab file
```
UUID="78BA90B6BA90727C" /media/SW_Preload           ntfs    relatime        0       2
```
save, reboot and post us results.

---

### Post by dimapitt on 2009-06-20
i'm scared to try this now :(.

sorry for just taking up your time. I will use windows pretty often and I'm positive that with windows i'm bound to get some error that will make me shut down improperly.

---

### Post by TeoBigusGeekus on 2009-06-20
Even if this happens, you can always boot with a live cd, change the fstab file (i.e. ntfs partition not mounted on startup) and boot again.

---

### Post by dimapitt on 2009-06-20
that is a good point... I just have to remember that it's the fstab file that I need to access haha. I will post with my results in one moment.

---

### Post by dimapitt on 2009-06-20
It works!! Thank you :D. If there is an error can I somehow get to the ubuntu partitions in windows using some sort of program?

nvm google led me to 

[http://www.fs-driver.org](http://www.fs-driver.org)

Guess I don't have to worry about having my live cd around.

---

### Post by raymondh on 2009-06-20
> **dimapitt said:**
> 

Guess I don't have to worry about having my live cd around.

Oh no ... keep the liveCD ... it still has other/valuable uses.

Congratulations on solving your issue.

Happy Ubuntu-ing.

---

### Post by dimapitt on 2009-06-20
> **raymondhenson said:**
> Oh no ... keep the liveCD ... it still has other/valuable uses.

Congratulations on solving your issue.

Happy Ubuntu-ing.

but what isn't using it just giving you access to it's drive?

---

### Post by LewRockwell on 2009-06-20
also, you'll want to make good notes of what you did here, or make print-outs of these pages for future reference.

---

### Post by dimapitt on 2009-06-20
yeah i already wrote it down haha. I have a little handy notebook now :D.

---

### Post by mjschmidt on 2009-07-02
I have installed Ubuntu using Wubi on my Windows 7 machine. Will these instructions still work for me, or do I have to do it differently?

As I said, Ubuntu is installed on my Windows partition using Wubi, but the drive I want to mount is a separate partition that holds all my media files. (So, ubuntu is on C drive, my media files are on D drive).

Thanks!

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x559d4013

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       17251   137024504    7  HPFS/NTFS
/dev/sda3           17251       23625    51200000    f  W95 Ext'd (LBA)
/dev/sda4           23625       24322     5599232   17  Hidden HPFS/NTFS
/dev/sda5           17251       23625    51198976    7  HPFS/NTFS

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281    c  W95 FAT32 (LBA)

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

---


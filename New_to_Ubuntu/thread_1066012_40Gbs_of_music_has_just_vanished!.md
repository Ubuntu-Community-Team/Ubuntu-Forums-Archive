---
title: "40Gbs of music has just vanished!"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Jingle on 2009-02-10
Waaaa.... I've got all my important personal data on another physical drive so that this doesn't happen when I play about with operating systems but somehow this afternoon about 40gb of music has vanished from my 300gb drive (which was there a couple of hours ago I played a tune on rythmbox that's not there now).  

I've not lost an entire folder, or any data from other folders on the drive but for some reason lots of sub-directories have gone.  my collection has gone from 55-60gb to just about 15gb. it's not taken the subfolders in alphabetical order or anything, but seems to have thinned the folder out.  I've still got my iTunes library XML files from windows safe, so they should have a complete listing of what I've lost.   but this is mad. I've not done any commands on the music folder other than to make a link to it from my home/music and to mount the drive. otherwise nothing else should have touched this hard drive!

the missing files aren't showing up in windows either... I had 15gb free on the drive earlier now it's 55gb free... help!

---

### Post by cariboo on 2009-02-10
Have a look at [testdisk]("http://www.cgsecurity.org/wiki/TestDisk"), it should help you recover your missing files. Testdisk is in the repositories and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by Jingle on 2009-02-10
thank you.  looking now.  whatever has happened has also randomly gone through my pictures folder and I'm missing about 2/3rd of the photos of my two year old son.

---

### Post by JK3mp on 2009-02-10
Yes testdisk works well for recovery. But are you sure you didn't try to do anything else while running the files? Also im assuming you mean are erased off your External drive right?

---

### Post by Jingle on 2009-02-10
Nope, the data has gone missing from a 300gb internal drive that I've not touched at all during my installation of ubunutu all the data was there a couple of hours ago.  the only operations I've performed on the drive have been to mount it and to create links from the affected directories too my /home directory.

Unfortunately I don't know exactly when the data went missing, but I'm sure I've not changed any partitions or anything on this drive :S  it is an NTFS drive that's had all my data when I've been using windows (which also has lost the data :S)


I've got my o/s on a 120gb drive and just bought a 1tb external to back this all up to... and I lost it the day I'm going to backup... bloody typical!

It also seems to have been fairly random in what's missing too :S

---

### Post by Cypher on 2009-02-10
Mount it and create links? Could you elaborate? Also can you show us the output of
```

sudo fdisk -l
mount

```

---

### Post by Jingle on 2009-02-10
I've added the drive to fstab to make it autoboot.....
```

/dev/sdb1	/media/Documents	ntfs-3g		0	0
```

but I followed the instructions from the ubuntu docs.   and I dont' see how that would make me randomly lose 40gb?  losing the lot I can understand.

I've installed testdisk from synaptic and now cant find out how to run the program.   lol my first proper day on linux isn't going too well.

---

### Post by Therion on 2009-02-10
That much data and you don't make backups?

---

### Post by Jingle on 2009-02-10
Sorry Cypher I was typing the last post and missed yours.

I'm referring to my 300gb drive which I belive is /dev/sdb

Sudo fdisk -l gives me:
> jingle@desktop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865        9727    39062047+  83  Linux
/dev/sda3            9728       10943     9767520    5  Extended
/dev/sda5            9728       10943     9767488+  82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05d429db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36480   293025568+   7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b12f16c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      108468   871269178+   7  HPFS/NTFS
/dev/sdc2          108469      121601   105490822+   b  W95 FAT32


Mount gives me:
> jingle@desktop:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb1 on /media/Documents type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jingle/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jingle)
/dev/sdc2 on /media/Backup type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdc1 on /media/Media type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


I wanted to make the music & pictures directories in my home folder point to the equivalent ones on my drive so that as programs went to save in the default directories they would save files onto my 300gb drive instead of in my home folder in a partition on my primary drive.  this has worked fine.

Regards mounting the drive, I added the line in my above post to fstab so the drive auto mounts when I boot up.

---

### Post by Jingle on 2009-02-10
> **Therion said:**
> That much data and you don't make backups?

I haven't had space to backup to so I've just bought at 1tb drive and it was going to be backed up tonight! I think the computer knew and has done this deliberately.  :P

---

### Post by JK3mp on 2009-02-10
Was it right after inserting that line that it deleted everything?

---

### Post by Neural oD on 2009-02-10
a possibilty could be that if you have been accessing this external drive with windows - it could have a virus that randomly deletes files or folders. That's why it's good to stay off of windows as far as is possible

---

### Post by Jingle on 2009-02-10
> **JK3mp said:**
> Was it right after inserting that line that it deleted everything?

I'm not sure if it was immediately after but the loss has happened since I inserted the line

---


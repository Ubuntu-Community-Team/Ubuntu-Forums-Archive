---
title: "Accessing windows files"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by Einherjer on 2010-11-13
Hi

I had to boot my kubuntu cd since windows won't load anymore. I want to move files from my main hard drive to my second one so i can try a format.

I was able to mount the drive using the ubuntu wiki but i don't see any files.

Thanks

---

### Post by lol768 on 2010-11-13
Is your windows drive formatted as FAT32 or NTFS? I think you need extra packages to access NTFS drives, and what command did you use to mount the drive?

---

### Post by Einherjer on 2010-11-13
NTFS Windows 7

I used sudo fdisk -l
and sudo mkdir /media/WindowsNTFS

I just installed gparted and i can<t use it... it's asking for a password!

---

### Post by cgroza on 2010-11-13
Did you do a WUBI install or a normal one from the live cd? If from WUBI then go to /host/ and your files shoul be there. If not, I think your partitions are not mounted. Install Gparted and take a look.

---

### Post by Einherjer on 2010-11-13
I have no idea what is a wubi install. I followed the steps i posted above. the drive showed up in dolphin but nothing in it.

I installed gparted but when i try to start it, the system request a password... i am using the livecd and i did not set up a password.

---

### Post by lol768 on 2010-11-13
> **Einherjer said:**
> NTFS Windows 7

I used sudo fdisk -l
and sudo mkdir /media/WindowsNTFS

I just installed gparted and i can<t use it... it's asking for a password!

Where is your mount command? From the output you have given above all you have done is create a blank folder in /media (maybe you did not post your mount command, but if you did not use the mount command read below)

Try installing ntfs-config by clicking [apt:ntfs-config](apt:ntfs-config)

Then run
```
gksudo ntfs-config
```and follow the instructions. For more info see [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Einherjer on 2010-11-13
ntfs config is already installed. i tried to run it with the command gksudo ntfs-config and nothing happens

---

### Post by Einherjer on 2010-11-13
maybe it is the hard drive that is dead?

thinking about it..i am able to access my second drive..ntfs with my files no problem

only the drive with windows installed is giving me trouble and it is the one i need access the most because i need some files there

---

### Post by CharlesA on 2010-11-13
If Windows isn't booting up any more, and you can't see any files on the drive, then it's likely that the drive is having problems.

Can you post the output of these please:

```
sudo fdisk -l
```

```
mount
```

---

### Post by Einherjer on 2010-11-13
```
Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a788b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdb5               2       30401   244187968+   7  HPFS/NTFS
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sdb5 on /media/Backup type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
```

My 150gb drive with windows on it doesnt seem to be there

---

### Post by CharlesA on 2010-11-13
Could be that the drive is dead or one of the cables came loose.

Is it detected in the BIOS?

In any case, make sure that both the power and data cable are secure and then see if the drive is detected.

---

### Post by Einherjer on 2010-11-13
It is detected by the BIOS yes
It boots Windows and then freeze half-way thru
Same with safe mode.

---

### Post by CharlesA on 2010-11-13
Define "freeze" does it Blue screen, or what?

---

### Post by Einherjer on 2010-11-13
It stops working with the Win7 logo on screen. No error message. Safe mode is the same..at one point it stops working.

---

### Post by CharlesA on 2010-11-13
If it's not being detected by the OS but is being detected by the BIOS, then it's likely a problem with the drive.

Perhaps the drive is corrupt, I don't know.

---

### Post by Einherjer on 2010-11-13
Any way i can do a diagnostic with kubuntu?

---

### Post by Einherjer on 2010-11-13
Turns out my drive is dead. Tried to copy files from it at a friend's and it failed.

---

### Post by CharlesA on 2010-11-13
Only diagnostic you could run is from the manufacturer. It would tell if it's toast or not.

Which it is. :(

---


---
title: "Linking Ubuntu and WinXP Login Identies"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by jbuczek on 2010-11-26
I'm new to Ubuntu but I've been using computers for 45 years including a couple years working at Microsoft so I'm not exactly stupid about them.

I'm dual booting Ubuntu 10.10 and WinXP SP3 and I'm trying to migrate myself and my family to 100% Linux users.  This won't happen completely until Linux has a reasonably priced equivalent of TurboCAD (i.e. pretty good CAD function but a fraction of AutoCAD price) but we're trying.

How can I make sure that a particular login ID is accepted as the same person on both systems?

In trying to work out the best way to have access to all personal documents from either system I have:
   1. One partition formatted as Ext2 with the Ext2 drivers installed in
      XP so it has full access.
   2. One partition formatted as NTFS
   3. One partition formatted as FAT32

In some cases Ubuntu is enforcing greater security than XP.  If I put a document into a folder under XP (logged in as johnb) sometimes when I try to access the document from Ubuntu (logged in as johnb) it says I do not have permission to access that document.  I have to sudo Nautilus and change the permissions. The only pattern I've seen so far is that most of the problems seem to happen on the FAT32 partition.

No problem with the reverse.  XP gives me access to documents created under Ubuntu no problem no matter where I put them.

I don't really want to make Ubuntu wide open for anyone to access anything.

How can I sync these two logins?

I'm not talking about a one time solution for johnb either.  Several people use this computer, and we all share two others where I'm trying to do the same thing, so I need a generic solution: i.e. for each user a one time setting that insures the two logins are accepted as the same user with the same rights.

Possible?

TIA

---

### Post by sandyd on 2010-11-26
> **jbuczek said:**
> I'm new to Ubuntu but I've been using computers for 45 years including a couple years working at Microsoft so I'm not exactly stupid about them.

I'm dual booting Ubuntu 10.10 and WinXP SP3 and I'm trying to migrate myself and my family to 100% Linux users.  This won't happen completely until Linux has a reasonably priced equivalent of TurboCAD (i.e. pretty good CAD function but a fraction of AutoCAD price) but we're trying.

**Varicad? [http://www.varicad.com/en/home/](http://www.varicad.com/en/home/)**

How can I make sure that a particular login ID is accepted as the same person on both systems?

In trying to work out the best way to have access to all personal documents from either system I have:
   1. One partition formatted as Ext2 with the Ext2 drivers installed in
      XP so it has full access.
   2. One partition formatted as NTFS
   3. One partition formatted as FAT32

In some cases Ubuntu is enforcing greater security than XP.  If I put a document into a folder under XP (logged in as johnb) sometimes when I try to access the document from Ubuntu (logged in as johnb) it says I do not have permission to access that document.  I have to sudo Nautilus and change the permissions. The only pattern I've seen so far is that most of the problems seem to happen on the FAT32 partition.

[B]post output of
```

mount -l
```
[/B]

No problem with the reverse.  XP gives me access to documents created under Ubuntu no problem no matter where I put them.

I don't really want to make Ubuntu wide open for anyone to access anything.

How can I sync these two logins?

I'm not talking about a one time solution for johnb either.  Several people use this computer, and we all share two others where I'm trying to do the same thing, so I need a generic solution: i.e. for each user a one time setting that insures the two logins are accepted as the same user with the same rights.

Possible?

TIA.

you can also do what I used to do.

Choose one place to store your files (either in the linux or windows partition).

Then, simply link the directories together.

I.E. user1's my documents folder in windows is linked to the mydocuments folder in linux. The folder in linux will contain their files.

---

### Post by jbuczek on 2010-11-26
OK

johnb@MaxUbu:~$ mount -l
/dev/sda7 on / type ext4 (rw,errors=remount-ro,commit=0) [UbuBoot]
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
/dev/sda3 on /media/PRIVATE type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions) [PRIVATE]
/dev/sda4 on /media/PUBLIC type vfat (rw) [PUBLIC]
/dev/sda8 on /home type ext2 (rw) [UbuHome]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/johnb/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=johnb)

---

### Post by sandyd on 2010-11-26
> **jbuczek said:**
> OK

johnb@MaxUbu:~$ mount -l
/dev/sda7 on / type ext4 (rw,errors=remount-ro,commit=0) [UbuBoot]
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
/dev/sda3 on /media/PRIVATE type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions) [PRIVATE]
/dev/sda4 on /media/PUBLIC type vfat (rw) [PUBLIC]
/dev/sda8 on /home type ext2 (rw) [UbuHome]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/johnb/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=johnb)

```

sudo umount /dev/sda4
sudo nano /etc/fstab
```
add this if it doesn't exist
```

/dev/sda4               /media/PUBLIC     vfat         noatime,exec,users,rw,umask=000    0 0

```

run
```

sudo mount /dev/sda4
```

---


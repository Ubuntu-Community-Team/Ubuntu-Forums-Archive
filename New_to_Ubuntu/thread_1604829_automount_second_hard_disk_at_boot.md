---
title: "automount second hard disk at boot"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by A.Zan on 2010-10-24
i have 2 drives, how can i automount the 2nd one ?
thanks

---

### Post by cavh on 2010-10-24
Presuming you have been able to manually mount the 2nd disk, type this in a terminal

```
cat /etc/mtab
```

and then copy the line showing your 2nd disk into the file */etc/fstab* and reboot.

---

### Post by A.Zan on 2010-10-25
> **cavh said:**
> Presuming you have been able to manually mount the 2nd disk, type this in a terminal

```
cat /etc/mtab
```and then copy the line showing your 2nd disk into the file */etc/fstab* and reboot.

my 2nd disk label is volume,

so i have to add into that file the whole line ?

/dev/sdb1 /media/Volume fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0

---

### Post by potchefstroom on 2010-10-25
the original goes:

/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0

so try:

/dev/sdb1 /media/Volume ext4 rw,errors=remount-ro,commit=0 0 0

---

### Post by Verbeck on 2010-10-25
to summarise :
1.first is the drive file or UUID. to find that run [FONT=monospace]sudo blkid -c /dev/null
2.second type where you would mount the drive. the directory should exist
3.type the file system type. the above command should display it
4.mounting options[/FONT], the community ubuntu documentation should be able to help
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[FONT=monospace]
[/FONT]

---

### Post by A.Zan on 2010-10-26
step 1 returns:

/dev/sdb1: LABEL="Volume" UUID="9EA8C9D9A8C9AFD7" TYPE="ntfs"

so i found out filesystem it's not ext4 but ntfs, is this right ?

---

### Post by Morbius1 on 2010-10-26
>  /dev/sdb1: LABEL="Volume" UUID="9EA8C9D9A8C9AFD7" TYPE="ntfs"1st: Unmount the partition if is already mounted:
```
sudo umount /media/Volume
```2nd: Create a permanent mountpoint for sdb1 to live in:
```
sudo mkdir /media/Volume
```3rd: Add a line in fstab to automount that partition:

In it's simplest form a line in fstab to mount that partition at boot would look like this:

```
/dev/sdb1 /media/Volume ntfs defaults 0 0
```This will mount the ntfs partition to /media/Volume with owner = root but with read/write permissions to everyone.

4th: Check for errors an mount the new partition
```
sudo mount -a
```

---

### Post by A.Zan on 2010-10-26
**Perfect**
Thanks !


> **Morbius1 said:**
> 1st: Unmount the partition if is already mounted:
```
sudo umount /media/Volume
```2nd: Create a permanent mountpoint for sdb1 to live in:
```
sudo mkdir /media/Volume
```3rd: Add a line in fstab to automount that partition:

In it's simplest form a line in fstab to mount that partition at boot would look like this:

```
/dev/sdb1 /media/Volume ntfs defaults 0 0
```This will mount the ntfs partition to /media/Volume with owner = root but with read/write permissions to everyone.

4th: Check for errors an mount the new partition
```
sudo mount -a
```

---

### Post by mipesom on 2010-12-21
> **Morbius1 said:**
> 1st: Unmount the partition if is already mounted:
```
sudo umount /media/Volume
```2nd: Create a permanent mountpoint for sdb1 to live in:
```
sudo mkdir /media/Volume
```3rd: Add a line in fstab to automount that partition:

In it's simplest form a line in fstab to mount that partition at boot would look like this:

```
/dev/sdb1 /media/Volume ntfs defaults 0 0
```This will mount the ntfs partition to /media/Volume with owner = root but with read/write permissions to everyone.

4th: Check for errors an mount the new partition
```
sudo mount -a
```
Thanks. Very helpful! :)

---

### Post by seawolf167 on 2010-12-21
If you have more questions, for a very good fstab how to, click the fstab link in my signature

---


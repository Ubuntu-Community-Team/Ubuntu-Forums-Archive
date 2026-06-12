---
title: "Memory stick has no write permissions"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by nikhilneela on 2011-01-12
Hi all, I have a brand new dell laptop for which there is an option to place a memory card. I tried to copy some files into the memory card. But there is only read permission for that. why is this so? and chmod 777 does not work. the following is my /etc/fstab file entries
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda8       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=5665a63e-74a4-4002-b054-ea44c29e4835 none            swap    sw              0       0
/dev/sda7 /media/Entertainment ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda6 /media/Softwares ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/Studies ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda3 /media/OS ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

---

### Post by blind2314 on 2011-01-12
If you do an ```
ls -la
``` on the mountpoint of the memory card, what are the results?
 
Also, I see no reason why a ```
sudo chmod 777 /mountpoint
``` where mountpoint is the directory the memory card is mounted wouldn't work. Can you post specifics that you're trying?

---

### Post by blind2314 on 2011-01-12
If you do an ```
ls -la
``` on the mountpoint of the memory card, what are the results?
 
Also, I see no reason why a ```
sudo chmod 777 /mountpoint
``` where mountpoint is the directory the memory card is mounted wouldn't work. Can you post specifics that you're trying?

---

### Post by oldos2er on 2011-01-12
What filesystem is the memory card using? If it's not a native Linux filesystem, chmod won't work.

---

### Post by blind2314 on 2011-01-12
Fair point, I just assumed something of the FAT variety.

---

### Post by Hippytaff on 2011-01-12
The card needs to be formatted as ext3 or ext4

---


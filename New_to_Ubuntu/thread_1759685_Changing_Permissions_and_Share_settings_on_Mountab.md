---
title: "Changing Permissions and Share settings on Mountable Volume"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by seventhsamurai on 2011-05-16
Hi Guys

I am running Ubuntu 10.04.2 LTS and I have a mounted partition that I use for storage only. I have samba installed and sharing folders within my internal network works like a charm, as long as the shared directory is on my Ubuntu system drive/partition.

However, when I try to share a directory on my mounted storage partition, it does not retain the share settings after I change them. I am also unable to change the access permissions. I even tried accessing permissions as root, and still it did not allow me.

I would really appreciate any help on how I can share this folder on my mounted storage volume over my internal network.

Thanks in advance.

---

### Post by seventhsamurai on 2011-05-16
Sorry to bump. Someone please help.

---

### Post by Plueonic on 2011-05-16
If the partition is formated as NTFS/FAT, it won't follow linux filesystem permission and you'll have to adjust the permissions from the mount options (in fstab if you configured it to mount it automatically)
It would be helpful if you post the output of the following;
```
cat /etc/fstab
```
```
cat /etc/mtab
```
```
sudo blkid -c /dev/null
```

---

### Post by seventhsamurai on 2011-05-16
Hi [Plueonic]("http://ubuntuforums.org/member.php?u=1301093"), thanks for offering to help. Here are the outputs for what you asked. The volume I am trying to share a folder on is an NTFS partition called **Data2**:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=2883985d-afed-4fba-9198-af61cb6a664a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=b97c3472-713f-472c-bc6f-04afe57bb7aa none            swap    sw              0       0

```

```
/dev/sda7 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/gjmpc4/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=gjmpc4 0 0
/dev/sda5 /media/DATA fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sda8 /media/Data2 fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
```

```
/dev/sda1: LABEL="XP PROF" UUID="E44CBB7E4CBB49D6" TYPE="ntfs" 
/dev/sda5: LABEL="DATA" UUID="94A4C504A4C4EA36" TYPE="ntfs" 
/dev/sda6: LABEL="Storage1" UUID="1BA4D7BD41306813" TYPE="ntfs" 
/dev/sda7: UUID="2883985d-afed-4fba-9198-af61cb6a664a" TYPE="ext4" 
/dev/sda8: LABEL="Data2" UUID="670714C6650D1E0A" TYPE="ntfs" 
/dev/sda9: UUID="b97c3472-713f-472c-bc6f-04afe57bb7aa" TYPE="swap" 
```

---

### Post by Plueonic on 2011-05-16
First unmount the partition
```
sudo umount /dev/sda8
```Make the permanent mount point
```
sudo mkdir /media/Data2
```Enter to a new line in /etc/fstab - run *gksu gedit /etc/fstab* to open it as root
(For more options, see [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)) 
```
UUID=670714C6650D1E0A   /media/Data2  ntfs defaults,gid=46,umask=0000  0  0
```To apply the changes, reboot or run;
```
sudo mount -a
```*The umask=0000 would allow anyone to read/write/execute files on that partition (you could use 2 to turn off write permissions for 'others'. eg; umask=0002)

Hope that helps

---

### Post by seventhsamurai on 2011-05-16
Thank you so much for your time and help. Worked beautifully and I'm able to access it just fine across the network now.

---

### Post by Plueonic on 2011-05-16
Glad i could help ;)

---


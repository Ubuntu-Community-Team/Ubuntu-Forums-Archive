---
title: "accessing another partition"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by jangp4 on 2011-02-28
Just installedd 10.10 on what I thought was my Ubuntu partition but now cannot access my Windows partition?  Is it dead? gone?  Oh dear.

---

### Post by seawolf167 on 2011-02-28
Welcome to the forums!

If you choose the option to "install them side by side blah blah blah" you should be able to access your Windows partition by going to Places -> XYZ GB Filesystem (the XYZ will be numbers corresponding to your Windows partition size)

If that doesn't work, please open a terminal (Applications -> Accessories -> Terminal) and post the output of 

```
sudo fdisk -l
```and 

```
mount
```P.S. Always have backups of anything you don't want to loose. I recommend [Clonezilla]("http://www.clonezilla.org")

---

### Post by jangp4 on 2011-02-28
as a newbie this is all gobbledegook to me Hope uou can help.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc502c502

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9727    78132096    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf1703e41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+   7  HPFS/NTFS
/dev/sdb2            1217        9605    67384642+  83  Linux
/dev/sdb3            9606        9729      996030   82  Linux swap / Solaris

jangp4@jangp4-desktop:~$ mount
/dev/sdb2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /media/windata type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1 on /media/windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jangp4/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jangp4)
jangp4@jangp4-desktop:~$

---

### Post by seawolf167 on 2011-02-28
> **jangp4 said:**
> ...

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1   *           1        9727    78132096    7  HPFS/NTFS**

...

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1               1        1216     9767488+   7  HPFS/NTFS**
/dev/sdb2            1217        9605    67384642+  83  Linux
/dev/sdb3            9606        9729      996030   82  Linux swap / Solaris

...

none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
[B]/dev/sdb1 on /media/windata type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1 on /media/windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)[/B]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jangp4/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jangp4)
jangp4@jangp4-desktop:~$

Looks like its all still there. You should be able to access it through the Places menu (they are called "windata" and "windows").

If they are not there, simply open Nautilus (i.e. any window), and keep clicking the up arrow to go up a directory level until you cannot anymore, then double click "media", then with "windata" or "windows".

---

### Post by Mark Phelps on 2011-03-01
> **jangp4 said:**
> Just installedd 10.10 on what I thought was my Ubuntu partition but now cannot access my Windows partition?  Is it dead? gone?  Oh dear.

Do you mean you can not SELECT your Windows install?

If that is the case, you need to boot into Ubuntu, open a terminal, and enter "sudo update-grub".  That will regenerate the default GRUB menu and should add an entry for Windows.

When you reboot, you should then see a GRUB menu with an added Windows entry.

---

### Post by gdonwallace on 2011-03-01
If the windows file system is still there, You should see it under Places from the menu.

Click "Places" and it should list something like "XXX file system".  On my laptop it is listed as 125gb File system.  That is your windows partition.

Now on the other way around, Windows will not see your Ubuntu file system.  Windows does not read any hard drive tags that are not DOS/NTFS/FAT32, which Ubuntu is none of these.

Good Luck.

---


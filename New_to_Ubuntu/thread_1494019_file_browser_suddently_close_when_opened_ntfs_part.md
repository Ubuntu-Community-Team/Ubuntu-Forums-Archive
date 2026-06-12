---
title: "file browser suddently close when opened ntfs partition"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by ferrystitch on 2010-05-26
im instaled dual boot ubuntu 10.04 and win xp

i mount my ntfs partition on drive d (sda3) to /home/ferrystitch/data

then when i open /home/ferrystitch/data with File Browser
windows suddenly close...
i was update all things connect to nautilus

after the windows close, in the task bar, windows title change from file browser to file manager, then disappear...
------------------------------------
fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
224 heads, 19 sectors/track, 27540 cylinders
Units = cylinders of 4256 * 512 = 2179072 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91769176

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7218    15359894+   7  HPFS/NTFS
/dev/sda2            7219       10660     7323648   83  Linux
/dev/sda3           12031       27539    33003142+   7  HPFS/NTFS
/dev/sda4           10661       12030     2914305    5  Extended
/dev/sda5           10661       11807     2440192   83  Linux
/dev/sda6           11808       12030      473088   82  Linux swap / Solaris

Partition table entries are not in disk order
-----------------------------------
fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda2 :
UUID=4b423edc-ffb9-43a6-af24-bab56f189202    /    ext3    errors=remount-ro    0    1
#Entry for /dev/sda5 :
UUID=7fbe2260-0fd5-45b0-8266-ef88b91bc69e    /home    ext3    defaults    0    2
#Entry for /dev/sda3 :
UUID=4A68829568827F85    /home/ferrystitch/data    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda6 :
UUID=07394162-354e-4cfa-b700-47b4fcf8052a    none    swap    sw    0    0
---------------------------------------
mount

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
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
/dev/sda5 on /home type ext3 (rw)
/dev/sda3 on /home/ferrystitch/data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ferrystitch/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ferrystitch)
---------------------------------------------------

pls help me, how to fix it...

---

### Post by ferrystitch on 2010-05-27
is this problem only happened to me?

---

### Post by Gone fishing on 2010-05-27
I've not had a similar problem but I wonder if there is a problem with the ntfs partition and if using a windows startup disk or similar and running chkdsk might fix it?

---

### Post by ferrystitch on 2010-05-27
i was try to scan disk on win xp...
and i was try to uninstall ubuntu and not mount my partition on /home
so this ubuntu was fresh new install... and nothing happened...
file browser suddenly close when i opened ntfs partition...

is there no solution for this problem?

---


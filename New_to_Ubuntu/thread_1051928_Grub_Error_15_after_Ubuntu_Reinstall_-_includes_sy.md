---
title: "Grub Error 15 after Ubuntu Reinstall - includes system info"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by cyan on 2009-01-27
Another noob who knows just enough to get himself in trouble.

I was recently trying to set up home on a separate partition using the psychocats tutorial [here]("http://www.psychocats.net/ubuntu/separatehome").  I wasn't successful and screwed up my install of Ubuntu 8.04.  I decided to do a clean install and made a separate home directory using the manual install.  I thought everything worked fine but when I tried to restart I got the dreaded Error 15 in Grub.  I tried repairing grub using a live CD but I kept getting the File Not Found when I did the find command.

I saw a post that suggesting getting some info and posting the output here.  Any help is much appreciated.  

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /etc/fstab /boot

sda6: _________________________________________________________________________

    File system:       swap

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sdb1 already mounted or sdb1 busy

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13662e6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    59440499    29720218+   7  HPFS/NTFS
/dev/sda2        59440500   312576704   126568102+   5  Extended
/dev/sda5        59440563   150336269    45447853+  83  Linux
/dev/sda6       306439938   312576704     3068383+  82  Linux swap / Solaris
/dev/sda7       150336333   170819144    10241406   83  Linux
/dev/sda8       170819208   306439874    67810333+  83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 2051 MB, 2051014656 bytes
1 heads, 32 sectors/track, 125184 cylinders, total 4005888 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xddfae254

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     4005887     2002928    6  FAT16

sfdisk -V /dev/sdb:

Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="30001C24001BEF98" TYPE="ntfs" 
/dev/sda5: UUID="bd68bf8e-bdd2-49ec-8df1-4e8dae22d5d3" TYPE="ext3" 
/dev/sda6: UUID="41ec99a9-f88a-44ef-9be2-88f9584a2874" TYPE="swap" 
/dev/sda7: UUID="5d2b3dce-d6e0-4f05-a6ce-0fe80ad0ecb6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="cbf594d7-19e2-49fb-918c-d6dbb4e16106" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="CORSAIR" UUID="6C78-99AF" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
none on /proc type proc (rw)
none on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda5 on /mnt/root type ext3 (rw)
none on /mnt/root/proc type proc (rw)
/dev on /mnt/root/dev type none (rw,bind)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=bd68bf8e-bdd2-49ec-8df1-4e8dae22d5d3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=cbf594d7-19e2-49fb-918c-d6dbb4e16106 /home           ext3    relatime        0       2
# /dev/sda6
UUID=41ec99a9-f88a-44ef-9be2-88f9584a2874 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================== sda5/boot: ==================================

total 12872
drwxr-xr-x  2 root root    4096 2008-09-04 11:14 .
drwxr-xr-x 22 root root    4096 2009-01-27 05:20 ..
-rw-r--r--  1 root root   67648 2008-08-22 20:03 config-2.6.24-21-eeepc
-rw-r--r--  1 root root 5111601 2008-09-04 11:14 initrd.img-2.6.24-21-eeepc
-rw-r--r--  1 root root 5111267 2008-08-24 16:35 initrd.img-2.6.24-21-eeepc.bak
-rw-r--r--  1 root root  103204 2008-08-22 20:03 memtest86+.bin
-rw-r--r--  1 root root  879903 2008-08-22 20:03 System.map-2.6.24-21-eeepc
-rw-r--r--  1 root root 1850200 2008-08-22 20:03 vmlinuz-2.6.24-21-eeepc

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-27
It looks like the problem is for some reason Grub was not installed when you installed Ubuntu. Can you try reinstalling again? I would recommend accepting the defaults in the "Advanced" button near the end of the installation process, and then Grub should hopefully be installed correctly. Let me know how that goes or if you run into problems.

---

### Post by cyan on 2009-01-28
Thank you for the help! The issue was that when I installed over the old install, I didn't click the "format partition?" box in setting up the partitions.  I should have guessed something was wrong when I saw that the "clean" install had about 32gigs of data.  My old data was still there.

I went back and re-installed and made sure to click the "format partition" box and everything is great now.  Thank you!

---

### Post by caljohnsmith on 2009-01-28
That's great, I'm really glad to hear you figured out the true source of the problem; cheers and enjoy your new Ubuntu install. :)

---


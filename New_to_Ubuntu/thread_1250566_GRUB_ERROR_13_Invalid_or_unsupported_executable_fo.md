---
title: "GRUB ERROR 13: Invalid or unsupported executable format.."
date: 2009-08-26
forum: New to Ubuntu
---

### Post by Kaymeerah on 2009-08-26
Hi, i get GRUB error 13 when trying to start Windows XP

here is a bootinfo log:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 3593791 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dd8f2

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    29,302,559    29,302,497  83 Linux
/dev/sda2          29,302,560   951,176,519   921,873,960   5 Extended
/dev/sda5          29,302,623    33,206,354     3,903,732  82 Linux swap / Solaris
/dev/sda6          33,206,418   951,176,519   917,970,102  83 Linux
/dev/sda3    *    951,176,520 1,953,520,064 1,002,343,545   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc8c0c8c0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sdb2         102,398,310   143,364,059    40,965,750   7 HPFS/NTFS
/dev/sdb3         143,364,060   488,392,064   345,028,005   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     8,193,149     8,193,087  83 Linux
/dev/sdc2         102,392,640   625,136,399   522,743,760   f W95 Ext d (LBA)
/dev/sdc5         102,392,703   625,136,399   522,743,697   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="414db187-651e-45c7-9110-d7c5953cb5c3" TYPE="ext4" 
/dev/sda3: UUID="6A255FA46939099A" LABEL="DATA" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="960b0b5e-0d93-4eb5-94fe-7802cbf18afc" 
/dev/sda6: UUID="03eac62c-d90c-4f9e-b0ac-6b57020217f2" TYPE="ext4" 
/dev/sdb1: UUID="308CD8158CD7D386" LABEL="System" TYPE="ntfs" 
/dev/sdb2: UUID="28C4E20BC4E1DB58" LABEL="Temp" TYPE="ntfs" 
/dev/sdb3: UUID="1A90564190562393" LABEL="Iso" TYPE="ntfs" 
/dev/sdc1: LABEL="boot" UUID="a3190150-fd77-48a6-86c0-4a2aa3a5f74c" TYPE="ext4" 
/dev/sdc5: UUID="4238B29338B28587" LABEL="Games" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /home type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kaymeerah/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kaymeerah)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=kaymeerah)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=414db187-651e-45c7-9110-d7c5953cb5c3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=414db187-651e-45c7-9110-d7c5953cb5c3

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04 Jaunty Jackalope 64-bit
uuid		414db187-651e-45c7-9110-d7c5953cb5c3
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=414db187-651e-45c7-9110-d7c5953cb5c3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04 Jaunty Jackalope 64-bit (recovery mode)
uuid		414db187-651e-45c7-9110-d7c5953cb5c3
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=414db187-651e-45c7-9110-d7c5953cb5c3 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		414db187-651e-45c7-9110-d7c5953cb5c3
#kernel		/boot/vmlinuz-2.6.28-11-generic # # # #  #  #root=UUID=414db187-651e-45c7-9110-d7c5953cb5c3 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		414db187-651e-45c7-9110-d7c5953cb5c3
#kernel		/boot/vmlinuz-2.6.28-11-generic #root=UUID=414db187-651e-45c7-9110-d7c5953cb5c3 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04 Jaunty Jackalope 64-bit memtest86+
uuid		414db187-651e-45c7-9110-d7c5953cb5c3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=414db187-651e-45c7-9110-d7c5953cb5c3 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sdc6 during installation
UUID=03eac62c-d90c-4f9e-b0ac-6b57020217f2 /home           ext4    relatime        0       2
# swap was on /dev/sdc5 during installation
UUID=960b0b5e-0d93-4eb5-94fe-7802cbf18afc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.4GB: boot/grub/menu.lst
   1.8GB: boot/grub/stage2
   1.6GB: boot/initrd.img-2.6.28-11-generic
   6.9GB: boot/initrd.img-2.6.28-15-generic
   1.7GB: boot/vmlinuz-2.6.28-11-generic
   1.2GB: boot/vmlinuz-2.6.28-15-generic
   6.9GB: initrd.img
   1.6GB: initrd.img.old
   1.2GB: vmlinuz
   1.7GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.2
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.2="Microsoft Windows XP Professional" /fastdetect /noexecute=optin

================================ sdb3/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.1
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP: Wolfie Edition" /fastdetect /noexecute=optin
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.1="Microsoft Windows XP Professional" /fastdetect /noexecute=optin

```

I know there are awful lots of windows bootloaders but only sdb1 (hd1,0) is in use, why am i getting this error and what can i do to reinstall?

---

### Post by LewRockwell on 2009-08-26
Try changing this:```
title Microsoft Windows XP Professional
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```To This:```
title Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)
makeactive
chainloader +1
```

if that works you might try throwing your "savedefault" back in there below "makeactive"

.

---

### Post by Kaymeerah on 2009-08-26
it hangs at grub loading stage2 ...

---

### Post by LewRockwell on 2009-08-26
you've got a fairly involved installation but you might give SuperGrubDisk a shot at fixing it

looks like stage two might either be missing or damaged or not in the correct location

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by Kaymeerah on 2009-08-26
thats the problem, windows is installed at sdb1, which is hd1,0 in grub, STAGE2 is installed at hd0, as whole grub is, (hd0 is MBR in my case) and linux is on hd0,0

---

### Post by LewRockwell on 2009-08-26
windows doesn't play well with others unfortunately

it's the bully of the block and always wants to be on the first drive...and in the first partition if at all possible

.

---

### Post by louieb on 2009-08-26
I Dual boot Ubuntu on master (sda1)  and XP on slave (sda2)  Both drives are PATA (aka ide, flat wide ribbon cable to motherboard).  
This is what works for me.
```

title Win XP 
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1

```
The same entry works on another PC where both drives are SATA and the drive with Ubuntu is 1st in the boot order.  

> it hangs at grub loading stage2 ... 	

Just curious were does it hang?  after booting? after selecting XP?

---

### Post by stalkier on 2009-08-26
> **Kaymeerah said:**
> Hi, i get GRUB error 13 when trying to start Windows XP

here is a bootinfo log:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 3593791 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dd8f2

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    29,302,559    29,302,497  83 Linux
/dev/sda2          29,302,560   951,176,519   921,873,960   5 Extended
/dev/sda5          29,302,623    33,206,354     3,903,732  82 Linux swap / Solaris
/dev/sda6          33,206,418   951,176,519   917,970,102  83 Linux
/dev/sda3    *    951,176,520 1,953,520,064 1,002,343,545   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc8c0c8c0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sdb2         102,398,310   143,364,059    40,965,750   7 HPFS/NTFS
/dev/sdb3         143,364,060   488,392,064   345,028,005   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     8,193,149     8,193,087  83 Linux
/dev/sdc2         102,392,640   625,136,399   522,743,760   f W95 Ext d (LBA)
/dev/sdc5         102,392,703   625,136,399   522,743,697   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="414db187-651e-45c7-9110-d7c5953cb5c3" TYPE="ext4" 
/dev/sda3: UUID="6A255FA46939099A" LABEL="DATA" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="960b0b5e-0d93-4eb5-94fe-7802cbf18afc" 
/dev/sda6: UUID="03eac62c-d90c-4f9e-b0ac-6b57020217f2" TYPE="ext4" 
/dev/sdb1: UUID="308CD8158CD7D386" LABEL="System" TYPE="ntfs" 
/dev/sdb2: UUID="28C4E20BC4E1DB58" LABEL="Temp" TYPE="ntfs" 
/dev/sdb3: UUID="1A90564190562393" LABEL="Iso" TYPE="ntfs" 
/dev/sdc1: LABEL="boot" UUID="a3190150-fd77-48a6-86c0-4a2aa3a5f74c" TYPE="ext4" 
/dev/sdc5: UUID="4238B29338B28587" LABEL="Games" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /home type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kaymeerah/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kaymeerah)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=kaymeerah)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=414db187-651e-45c7-9110-d7c5953cb5c3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=414db187-651e-45c7-9110-d7c5953cb5c3

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04 Jaunty Jackalope 64-bit
uuid		414db187-651e-45c7-9110-d7c5953cb5c3
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=414db187-651e-45c7-9110-d7c5953cb5c3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04 Jaunty Jackalope 64-bit (recovery mode)
uuid		414db187-651e-45c7-9110-d7c5953cb5c3
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=414db187-651e-45c7-9110-d7c5953cb5c3 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		414db187-651e-45c7-9110-d7c5953cb5c3
#kernel		/boot/vmlinuz-2.6.28-11-generic # # # #  #  #root=UUID=414db187-651e-45c7-9110-d7c5953cb5c3 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		414db187-651e-45c7-9110-d7c5953cb5c3
#kernel		/boot/vmlinuz-2.6.28-11-generic #root=UUID=414db187-651e-45c7-9110-d7c5953cb5c3 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04 Jaunty Jackalope 64-bit memtest86+
uuid		414db187-651e-45c7-9110-d7c5953cb5c3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=414db187-651e-45c7-9110-d7c5953cb5c3 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sdc6 during installation
UUID=03eac62c-d90c-4f9e-b0ac-6b57020217f2 /home           ext4    relatime        0       2
# swap was on /dev/sdc5 during installation
UUID=960b0b5e-0d93-4eb5-94fe-7802cbf18afc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.4GB: boot/grub/menu.lst
   1.8GB: boot/grub/stage2
   1.6GB: boot/initrd.img-2.6.28-11-generic
   6.9GB: boot/initrd.img-2.6.28-15-generic
   1.7GB: boot/vmlinuz-2.6.28-11-generic
   1.2GB: boot/vmlinuz-2.6.28-15-generic
   6.9GB: initrd.img
   1.6GB: initrd.img.old
   1.2GB: vmlinuz
   1.7GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.2
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.2="Microsoft Windows XP Professional" /fastdetect /noexecute=optin

================================ sdb3/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.1
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP: Wolfie Edition" /fastdetect /noexecute=optin
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.1="Microsoft Windows XP Professional" /fastdetect /noexecute=optin

```

I know there are awful lots of windows bootloaders but only sdb1 (hd1,0) is in use, why am i getting this error and what can i do to reinstall?

Weird how I got the exact same error. I couldnt get mine to work. So after like 20 minutes of messing with it I just formated the partition. Of course, I do not use Windows anymore so... I am not sayig there is anything wrong with dual-booting, hell boot as many OS's as you want. It is awesome if you are a web or app developer.

---

### Post by Kaymeerah on 2009-08-27
yes it hangs when i select XP, though i gave it a thought, and i came to think of that i unplug the other HDDs when i install windows, which sets a new MBR cause it uses the older MBR (aka GRUB drive), so if i set the windows drive to MBR, then install windoze there, just to boot into the grub command line later and set hd0 to MBR again it might work

i think its confused hardware making this error, a MBR calling an another MBR doesnt go well...

---

### Post by Kaymeerah on 2009-08-27
now windows install says "THIS PARTITION IS NOT WINDOWS XP COMPATIBLE" blabla so on, wont let me format or anything

EDIT: nevermind, the retarded windows install made it a logical partition when i deleted it...

EDIT2: seems i HAVE to unplug the other hdds for windows to agree at all

---

### Post by Kaymeerah on 2009-08-27
been working on this for 3 days without a fix, worked fine before, im now giving up and reinstalling everything

---


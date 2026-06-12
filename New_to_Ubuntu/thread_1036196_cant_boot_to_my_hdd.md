---
title: "cant boot to my hdd"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Gipsy25 on 2009-01-10
ok hi ... i have 2 hard drives ... 1)200gb in which i HAD vista and the 2nd hdd i have ubuntu ... (810) now the grub was installed on my 2nd hdd i only modified grub so i can boot to vista whenever i wanted ... so before i could just enter my vista hdd and boot just fine ... 

I decided to reinstall vista and after the reinstall it was missing the NTLDR file so i tried to fix it using bootrec and the options available for that command ... 

Now for some reason i get an error that doesn't allow me to boot after a fresh and clean install. This is the error:

**************************************************
booting windows vista 
acpi 
vista loader 2.1.2
Done!
fallback 1
find --set-root /bootmgr
Error 17: file not found
Booting 'windows nt/2000/xp'
fallback 2!
find --set-root /ntldr 
error 17 file not found
booting 'enter command line'

boot failed' press any key to enter command line

### ok when i do that ... i get this other message ###

grub4DOS 0.4.3 2007-03-13 Memory bla bla bla 
[minimal bash-like line editing is supported. For the first word, TAB list possible command completations. Anywereelse TAB list possible completations of device/filename. ESC at any time exits]

GRUB> 
********************************************************
I understand the grub comes from ubuntu however i dont know how that could be possible .. because the only thing i did was to make a reference on the ubuntu hdd to my vista so it would appear on the menu so i could boot to my vista hdd ... 

I really dont know how to fix did .... i also tried a clean install, formating and installing i also try FIXMBR ... no luck ... if you can help i would appreciate it .... 

thanks in advance 
Gipsy

---

### Post by Gipsy25 on 2009-01-10
ok hi ... i have 2 hard drives ... 1)200gb in which i HAD vista and the 2nd hdd i have ubuntu ... (810) now the grub was installed on my 2nd hdd i only modified grub so i can boot to vista whenever i wanted ... so before i could just enter my vista hdd and boot just fine ... 

I decided to reinstall vista and after the reinstall it was missing the NTLDR file so i tried to fix it using bootrec and the options available for that command ... 

Now for some reason i get an error that doesn't allow me to boot after a clean install. This is the error:

**************************************************
booting windows vista 
acpi 
vista loader 2.1.2
Done!
fallback 1
find --set-root /bootmgr
Error 17: file not found
Booting 'windows nt/2000/xp'
fallback 2!
find --set-root /ntldr 
error 17 file not found
booting 'enter command line'

boot failed' press any key to enter command line

### ok when i do that ... i get this other message ###

grub4DOS 0.4.3 2007-03-13 Memory bla bla bla 
[minimal bash-like line editing is supported. For the first word, TAB list possible command completations. Anywereelse TAB list possible completations of device/filename. ESC at any time exits]

GRUB> 
************************************************** ******
I understand the grub comes from ubuntu however i dont know how that could be possible .. because the only thing i did was to make a reference on the ubuntu hdd to my vista so it would appear on the menu so i could boot to my vista hdd ... (hd0,hd1) (hd1,hd0)

I really dont know how to fix this .... i tried a clean install, formating and installing i also try FIXMBR ... no luck ... if you can help i would appreciate it .... 

Is there any way to format the partition and get rid of grub completly?


thanks in advance 
Gipsy

---

### Post by cerealtx on 2009-01-10
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

the only logical thing that i can think of is that you have 2 bootloaders fighting and kocking each other our, hopefully that link can help was updated for 8.04 so should be farely relevant

---

### Post by Gipsy25 on 2009-01-10
I did that after i installed ubuntu on the second hdd ... i cant use the bcd tool because i am not able to boot on vista just ubuntu ... as a matter of fact ... i didn't even use bcd on vista because it wasn't necessary ... (i have 2 hdd's ... ) so ... i dont know ... sorry i wish i could give more information about the issue ...

now is there any way i can actually get rid of grub completly and try to reinstall vista again ... ????

thank you for the reply .. i appreciate it ... 

Thank you very much for taking the time and reply 

regards ...

---

### Post by caljohnsmith on 2009-01-10
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by Gipsy25 on 2009-01-10
```
ok this is the result :

**********************************************
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab /boot

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /grldr /Boot

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbfd1bfd1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     1959929      979933+  83  Linux
/dev/sda2         1959930   120101939    59071005    5  Extended
/dev/sda5         1959993    31262489    14651248+  83  Linux
/dev/sda6        31262553   111346514    40041981   83  Linux
/dev/sda7       111346578   120101939     4377681   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x17341733

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    42491924    21245931    6  FAT16
/dev/sdb2        42491988   390716864   174112438+   f  W95 Ext'd (LBA)
/dev/sdb5        42491990   164778704    61143357+   7  HPFS/NTFS

sfdisk -V /dev/sdb:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 2 does not start at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9cfb5d61-67ea-4c87-8620-bcf628ab6c63" TYPE="ext3" 
/dev/sda5: UUID="8cbc7b10-7741-4db6-b353-45e37750611e" TYPE="ext3" 
/dev/sda6: UUID="69a7dc82-73e2-4e7d-8bfe-e4f93707335a" TYPE="ext3" 
/dev/sda7: UUID="3d430f0d-8d4f-420b-9d07-b8ab8dcbc349" TYPE="swap" 
/dev/sdb1: UUID="4A7CAD8F7CAD767B" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb5: UUID="DB052DFCBCB0D94E" LABEL="Gipsy2" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /boot type ext3 (rw,relatime)
/dev/sda6 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gipsy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gipsy)

============================= sda1/grub/menu.lst: =============================

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
# kopt=root=UUID=8cbc7b10-7741-4db6-b353-45e37750611e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9cfb5d61-67ea-4c87-8620-bcf628ab6c63

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		9cfb5d61-67ea-4c87-8620-bcf628ab6c63
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8cbc7b10-7741-4db6-b353-45e37750611e ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		9cfb5d61-67ea-4c87-8620-bcf628ab6c63
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8cbc7b10-7741-4db6-b353-45e37750611e ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9cfb5d61-67ea-4c87-8620-bcf628ab6c63
kernel		/vmlinuz-2.6.27-7-generic root=UUID=8cbc7b10-7741-4db6-b353-45e37750611e ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9cfb5d61-67ea-4c87-8620-bcf628ab6c63
kernel		/vmlinuz-2.6.27-7-generic root=UUID=8cbc7b10-7741-4db6-b353-45e37750611e ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9cfb5d61-67ea-4c87-8620-bcf628ab6c63
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


================================== sda1/grub: ==================================

total 224
drwxr-xr-x 2 root root   4096 2008-12-14 01:28 .
drwxr-xr-x 4 root root   4096 2008-12-17 13:00 ..
-rw-r--r-- 1 root root    197 2008-12-13 19:25 default
-rw-r--r-- 1 root root     45 2008-12-13 19:25 device.map
-rw-r--r-- 1 root root   8108 2008-12-13 19:25 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-13 19:25 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-13 19:25 installed-version
-rw-r--r-- 1 root root   8712 2008-12-13 19:25 jfs_stage1_5
-rw-r--r-- 1 root root   5090 2008-12-14 01:28 menu.lst
-rw-r--r-- 1 root root   5016 2008-12-14 01:28 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-13 19:25 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-13 19:25 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-13 19:25 stage1
-rw-r--r-- 1 root root 121460 2008-12-13 19:25 stage2
-rw-r--r-- 1 root root   9556 2008-12-13 19:25 xfs_stage1_5

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8cbc7b10-7741-4db6-b353-45e37750611e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=9cfb5d61-67ea-4c87-8620-bcf628ab6c63 /boot           ext3    relatime        0       2
# /dev/sda6
UUID=69a7dc82-73e2-4e7d-8bfe-e4f93707335a /home           ext3    relatime        0       2
# /dev/sda7
UUID=3d430f0d-8d4f-420b-9d07-b8ab8dcbc349 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda5/boot: ==================================

total 8
drwxr-xr-x  2 root root 4096 2008-12-13 19:14 .
drwxr-xr-x 20 root root 4096 2008-12-14 01:28 ..

================================== sdb1/Boot: ==================================

total 516
drwxrwxrwx 1 root root   4096 2009-01-10 15:09 .
drwxrwxrwx 1 root root   8192 2009-01-10 15:07 ..
-rwxrwxrwx 1 root root  12288 2009-01-10 15:09 BCD
-rwxrwxrwx 1 root root  21504 2009-01-10 15:09 BCD.LOG
-rwxrwxrwx 2 root root      0 2009-01-10 02:36 BCD.LOG1
-rwxrwxrwx 2 root root      0 2009-01-10 02:36 BCD.LOG2
-rwxrwxrwx 1 root root  24576 2009-01-10 15:07 bcd.old
-rwxrwxrwx 1 root root  65536 2009-01-10 02:36 bootstat.dat
drwxrwxrwx 1 root root      0 2009-01-10 02:36 cs-CZ
drwxrwxrwx 1 root root      0 2009-01-10 02:36 da-DK
drwxrwxrwx 1 root root      0 2009-01-10 02:36 de-DE
drwxrwxrwx 1 root root      0 2009-01-10 02:36 el-GR
drwxrwxrwx 1 root root      0 2009-01-10 02:36 en-US
drwxrwxrwx 1 root root      0 2009-01-10 02:36 es-ES
drwxrwxrwx 1 root root      0 2009-01-10 02:36 fi-FI
drwxrwxrwx 1 root root      0 2009-01-10 02:36 Fonts
drwxrwxrwx 1 root root      0 2009-01-10 02:36 fr-FR
drwxrwxrwx 1 root root      0 2009-01-10 02:36 hu-HU
drwxrwxrwx 1 root root      0 2009-01-10 02:36 it-IT
drwxrwxrwx 1 root root      0 2009-01-10 02:36 ja-JP
drwxrwxrwx 1 root root      0 2009-01-10 02:36 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 02:51 memtest.exe
drwxrwxrwx 1 root root      0 2009-01-10 02:36 nb-NO
drwxrwxrwx 1 root root      0 2009-01-10 02:36 nl-NL
drwxrwxrwx 1 root root      0 2009-01-10 02:36 pl-PL
drwxrwxrwx 1 root root      0 2009-01-10 02:36 pt-BR
drwxrwxrwx 1 root root      0 2009-01-10 02:36 pt-PT
drwxrwxrwx 1 root root      0 2009-01-10 02:36 ru-RU
drwxrwxrwx 1 root root      0 2009-01-10 02:36 sv-SE
drwxrwxrwx 1 root root      0 2009-01-10 02:36 tr-TR
drwxrwxrwx 1 root root      0 2009-01-10 02:36 zh-CN
drwxrwxrwx 1 root root      0 2009-01-10 02:36 zh-HK
drwxrwxrwx 1 root root      0 2009-01-10 02:36 zh-TW

=============================== StdErr Messages: ===============================

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
```

****************************************************************
Thanks for the help i hope this is useful ...

Gipsy

---

### Post by Gipsy25 on 2009-01-10
Also let m add that after i tried to install XP on the computer thinking that i could just change or modify the MBR from there ... one of the partition i had (i have 3 partitions on the vista hdd) was lost ... now it shows as "free space" and all the information was deleted ... dont know what happen ... i just know that i only modified c: ... at first it was RAW and then changed to "unallocated spac" now shows as free space ...

---

### Post by Partyboi2 on 2009-01-10
Have you tried reinstalling grub?
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by caljohnsmith on 2009-01-10
It looks like the Vista entry you are using in your Grub's menu.lst is correct, because you are obviously booting the sda drive on start up in order to boot into Ubuntu. But your Vista partition has the "grldr" file in it's root directory, which is the Grub4DOS boot loader, so did you at some point download either Grub4DOS or EasyBCD? Either way, it looks like what you need to do at this point is fix your Vista boot loader; in order to do that, I would boot your Vista Install CD, go to the command line, and do:
```
bootrec /rebuildbcd
```
And I think that should hopefully get Vista booting OK again. If not, let me know exactly what happens when you boot Vista from your Grub menu, and we can work from there.

---

### Post by Rocket2DMn on 2009-01-10
Threads merged.

---

### Post by Gipsy25 on 2009-01-10
well grub is installed correctly since i can boot just fine to my ubuntu hdd (I dont know muchabout ubuntu .. i am just learning too) now grub should not be installed on my second drive and for some reason my vista drive shows it.

I am a little confused here so i ran a boot info script and this is the result ... 
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab /boot

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /grldr /Boot

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbfd1bfd1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     1959929      979933+  83  Linux
/dev/sda2         1959930   120101939    59071005    5  Extended
/dev/sda5         1959993    31262489    14651248+  83  Linux
/dev/sda6        31262553   111346514    40041981   83  Linux
/dev/sda7       111346578   120101939     4377681   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x17341733

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    42491924    21245931    6  FAT16
/dev/sdb2        42491988   390716864   174112438+   f  W95 Ext'd (LBA)
/dev/sdb5        42491990   164778704    61143357+   7  HPFS/NTFS

sfdisk -V /dev/sdb:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 2 does not start at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9cfb5d61-67ea-4c87-8620-bcf628ab6c63" TYPE="ext3" 
/dev/sda5: UUID="8cbc7b10-7741-4db6-b353-45e37750611e" TYPE="ext3" 
/dev/sda6: UUID="69a7dc82-73e2-4e7d-8bfe-e4f93707335a" TYPE="ext3" 
/dev/sda7: UUID="3d430f0d-8d4f-420b-9d07-b8ab8dcbc349" TYPE="swap" 
/dev/sdb1: UUID="4A7CAD8F7CAD767B" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb5: UUID="DB052DFCBCB0D94E" LABEL="Gipsy2" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /boot type ext3 (rw,relatime)
/dev/sda6 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gipsy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gipsy)

============================= sda1/grub/menu.lst: =============================

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
# kopt=root=UUID=8cbc7b10-7741-4db6-b353-45e37750611e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9cfb5d61-67ea-4c87-8620-bcf628ab6c63

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		9cfb5d61-67ea-4c87-8620-bcf628ab6c63
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8cbc7b10-7741-4db6-b353-45e37750611e ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		9cfb5d61-67ea-4c87-8620-bcf628ab6c63
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8cbc7b10-7741-4db6-b353-45e37750611e ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9cfb5d61-67ea-4c87-8620-bcf628ab6c63
kernel		/vmlinuz-2.6.27-7-generic root=UUID=8cbc7b10-7741-4db6-b353-45e37750611e ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9cfb5d61-67ea-4c87-8620-bcf628ab6c63
kernel		/vmlinuz-2.6.27-7-generic root=UUID=8cbc7b10-7741-4db6-b353-45e37750611e ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9cfb5d61-67ea-4c87-8620-bcf628ab6c63
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


================================== sda1/grub: ==================================

total 224
drwxr-xr-x 2 root root   4096 2008-12-14 01:28 .
drwxr-xr-x 4 root root   4096 2008-12-17 13:00 ..
-rw-r--r-- 1 root root    197 2008-12-13 19:25 default
-rw-r--r-- 1 root root     45 2008-12-13 19:25 device.map
-rw-r--r-- 1 root root   8108 2008-12-13 19:25 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-13 19:25 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-13 19:25 installed-version
-rw-r--r-- 1 root root   8712 2008-12-13 19:25 jfs_stage1_5
-rw-r--r-- 1 root root   5090 2008-12-14 01:28 menu.lst
-rw-r--r-- 1 root root   5016 2008-12-14 01:28 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-13 19:25 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-13 19:25 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-13 19:25 stage1
-rw-r--r-- 1 root root 121460 2008-12-13 19:25 stage2
-rw-r--r-- 1 root root   9556 2008-12-13 19:25 xfs_stage1_5

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8cbc7b10-7741-4db6-b353-45e37750611e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=9cfb5d61-67ea-4c87-8620-bcf628ab6c63 /boot           ext3    relatime        0       2
# /dev/sda6
UUID=69a7dc82-73e2-4e7d-8bfe-e4f93707335a /home           ext3    relatime        0       2
# /dev/sda7
UUID=3d430f0d-8d4f-420b-9d07-b8ab8dcbc349 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda5/boot: ==================================

total 8
drwxr-xr-x  2 root root 4096 2008-12-13 19:14 .
drwxr-xr-x 20 root root 4096 2008-12-14 01:28 ..

================================== sdb1/Boot: ==================================

total 516
drwxrwxrwx 1 root root   4096 2009-01-10 15:09 .
drwxrwxrwx 1 root root   8192 2009-01-10 15:07 ..
-rwxrwxrwx 1 root root  12288 2009-01-10 15:09 BCD
-rwxrwxrwx 1 root root  21504 2009-01-10 15:09 BCD.LOG
-rwxrwxrwx 2 root root      0 2009-01-10 02:36 BCD.LOG1
-rwxrwxrwx 2 root root      0 2009-01-10 02:36 BCD.LOG2
-rwxrwxrwx 1 root root  24576 2009-01-10 15:07 bcd.old
-rwxrwxrwx 1 root root  65536 2009-01-10 02:36 bootstat.dat
drwxrwxrwx 1 root root      0 2009-01-10 02:36 cs-CZ
drwxrwxrwx 1 root root      0 2009-01-10 02:36 da-DK
drwxrwxrwx 1 root root      0 2009-01-10 02:36 de-DE
drwxrwxrwx 1 root root      0 2009-01-10 02:36 el-GR
drwxrwxrwx 1 root root      0 2009-01-10 02:36 en-US
drwxrwxrwx 1 root root      0 2009-01-10 02:36 es-ES
drwxrwxrwx 1 root root      0 2009-01-10 02:36 fi-FI
drwxrwxrwx 1 root root      0 2009-01-10 02:36 Fonts
drwxrwxrwx 1 root root      0 2009-01-10 02:36 fr-FR
drwxrwxrwx 1 root root      0 2009-01-10 02:36 hu-HU
drwxrwxrwx 1 root root      0 2009-01-10 02:36 it-IT
drwxrwxrwx 1 root root      0 2009-01-10 02:36 ja-JP
drwxrwxrwx 1 root root      0 2009-01-10 02:36 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 02:51 memtest.exe
drwxrwxrwx 1 root root      0 2009-01-10 02:36 nb-NO
drwxrwxrwx 1 root root      0 2009-01-10 02:36 nl-NL
drwxrwxrwx 1 root root      0 2009-01-10 02:36 pl-PL
drwxrwxrwx 1 root root      0 2009-01-10 02:36 pt-BR
drwxrwxrwx 1 root root      0 2009-01-10 02:36 pt-PT
drwxrwxrwx 1 root root      0 2009-01-10 02:36 ru-RU
drwxrwxrwx 1 root root      0 2009-01-10 02:36 sv-SE
drwxrwxrwx 1 root root      0 2009-01-10 02:36 tr-TR
drwxrwxrwx 1 root root      0 2009-01-10 02:36 zh-CN
drwxrwxrwx 1 root root      0 2009-01-10 02:36 zh-HK
drwxrwxrwx 1 root root      0 2009-01-10 02:36 zh-TW

=============================== StdErr Messages: ===============================

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
```

I hope this can help to clarify the situation

---

### Post by caljohnsmith on 2009-01-10
Yes, I agree that your Grub boot loader is installed just fine, but I think the issue is with your Vista boot loader, and not Grub. You some how have Grub4DOS or EasyBCD's NeoGrub installed in your Vista partition, and that is what has modified your Vista booting sequence. If you would run the command from your Vista Install CD that I gave, I think that will fix the problem. Also one other thing I notice is that your Vista partition is incorrectly labelled as FAT32 in the partition table when it really is NTFS. To correct that, you can do:
```
sudo sfdisk -c /dev/sdb 1 7
```

EDIT: Since you said you all ready tried the "bootrec /rebuildbcd" command without success, how about instead doing the following commands from your Vista CD:
```
bcdedit /store C:\boot\bcd /set {default} osdevice boot
bcdedit /store C:\boot\bcd /set {default} device boot
bcdedit /store C:\boot\bcd /set {bootmgr} device boot
bcdedit /store C:\boot\bcd /set {memdiag} device boot
```
Let me know how that goes.

---

### Post by Gipsy25 on 2009-01-10
Thank you very much in advanced ... yes ... when i saw the missing NTLDR message i did boot from the cd and tried "bootrec /rebuildbcd" it  said successful command or something like that and after the restart ... it did the same thing ... 
same error 17 fallbac 1 and then the error 17 ...
i will try that again ... 

and see if it will take it this time ... funny thing my ubuntu boots just fine ... (is there anyway i can delete, remove grub from my vista hdd ???? and keep the information i have in the other 2 partitions ???) 

I downloaded gparted and i i checked the hdd there is no errors found either ... ...

Thanks for the help guys ...

---

### Post by Gipsy25 on 2009-01-10
i tried to use the command given ... this is the message i got ... 

```
gipsy@i386-rbn:~$ sudo sfdisk -c /dev/sdb 1 7
[sudo] password for gipsy: 
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Done
```

Trying bootrec now ... and also the commands posted too 
Guys thank you so much for all the help ... i mean that

---

### Post by Gipsy25 on 2009-01-10
ok i tried i tried first "bootrec /rebuildbcd"
this is the message i get ... and i believe is wrong ... 

"successfully scanned windows instalations"
total identified windows installations: 0
the operation completed succesfully 

*************************************************8888
so i tried the command given before ...
bcd /store c:\boot\bcd /set [default] osdevice boot

and i got this message:
an error ocurred while attempting to reference the specified entry. the system cannot find the file specified.

---

### Post by Gipsy25 on 2009-01-10
ok i tried i tried first "bootrec /rebuildbcd"
this is the message i get ... and i believe is wrong ... 

"successfully scanned windows instalations"
total identified windows installations: 0
the operation completed succesfully 

*************************************************8 888
so i tried the command given before ...
bcd /store c:\boot\bcd /set [default] osdevice boot

and i got this message:
an error ocurred while attempting to reference the specified entry. the system cannot find the file specified

thanks ... :(

---

### Post by caljohnsmith on 2009-01-10
OK, from your Vista CD, how about trying:
```
diskpart
```
And at the diskpart prompt:
```
list volume
exit
```
That should give the drive letters of all your partitions, so see if it lists your Vista sdb1 installation. If it does, use the drive letter it lists in the bcdedit commands. Let me know how that goes.

---

### Post by meierfra. on 2009-01-10
> bcd /store c:\boot\bcd /set [COLOR="Red"][[/COLOR]default[COLOR="Red"]] [/COLOR]osdevice boot
The square brackets need to be curly brackets:

```
bcd /store c:\boot\bcd /set [COLOR="Red"]{[/COLOR]default[COLOR="Red"]}[/COLOR] osdevice boot

```

---

### Post by Gipsy25 on 2009-01-10
OK, thank you so much for all the help ... finaly i was able to boot on vista ... my mistake .. i was not using curly brackets on the bcd commands, meierfra wrote that up to my attention .... good call thanks meierfra) 

Also want to thank to caljohnsmith for taking the time and helping me with this i REALLY APPRECIATE IT guys ... 
Now i am able to boot and use the pc ... 

Now if you can tell me what went wrong so i dont make the same mistake ... how can i avoid to install grub AGAIN on mine VISTA hdd ... i am sure i did it myself however i dont know how.


1)now i have another question ... i lost my 3rd partion and i had lots of info in there ... is ther any possible way i can get it back ?????? and recover the info 
2)i am afraid of using the same setup i had before connecting both hard drives and booting from my ubuntu hdd to get to vista ... is there any other way .. or this shouldn't happen unless the user (me) makes a mistake ???


Guys ... thank you so much ...i mean that you helped me a lot today ...

---

### Post by caljohnsmith on 2009-01-10
> **Gipsy25 said:**
> 
Now if you can tell me what went wrong so i dont make the same mistake ... how can i avoid to install grub AGAIN on mine VISTA hdd ... i am sure i did it myself however i dont know how.

I don't know how you installed Grub4DOS, but you might have done it if you used EasyBCD in Vista; EasyBCD uses "NeoGrub" which is a derivative of Grub4DOS I think.
> **Gipsy25 said:**
> 
1)now i have another question ... i lost my 3rd partion and i had lots of info in there ... is ther any possible way i can get it back ?????? and recover the info 
Do you mean sda3 or sdb3? It looks like maybe you mean on your Vista drive? Because there is a large chunk of unused space on your Vista drive that might have been a former partition. How did you lose the partition? You might be able to use "testdisk" to recover it, but it would help if you could give some more details first about how it was lost.
> **Gipsy25 said:**
> 
2)i am afraid of using the same setup i had before connecting both hard drives and booting from my ubuntu hdd to get to vista ... is there any other way .. or this shouldn't happen unless the user (me) makes a mistake ???

You should be fine about booting either Vista or Ubuntu from your Grub menu now. I don't know what led up to your problems, but if you are careful, there's no harm in dual booting.

---


---
title: "Reinstall Grub Bootloader"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2009-01-14
I'm triple booting XP, OSX, and Ubuntu. Ive been using Grub bootloader to manage this all. Well I entered OSX and installed Chameleon EFI under OSX86 Tools (big mistake on my part). Now when I restarted my laptop I get a black screen with blinking cursor and nothing happens. Well I used parted magic to change the flags to make XP Partition "boot." Well this allowed me to enter XP but I have no options to enter OSX or Ubuntu. Any ideas how to get Grub bootloader back? I have a USB Flash with Live Ubuntu on it, Im hoping there is a way to do this without reinstalling Ubuntu. Thanks in advance.

---

### Post by rsambuca on 2009-01-14
Just boot from the live Ubuntu and open a terminal.

```
sudo grub
```

at the grub> prompt, enter

```
find /boot/grub/menu.lst
```

it will answer something of the form (hdX,Y)

then enter (replace the X and Y with your specific drive and partition numbers)

```
root (hdX,Y)
```

then write the grub to the MBR with 

```
setup (hd0)
```

then type in 'quit' to exit the grub shell.

---

### Post by RookieUbuntuUser58 on 2009-01-14
After entering Code 2 I get "Error 15: File Not Found." Any ideas where to go from there.

---

### Post by thomasr on 2009-01-14
Here is a nice how to for reinstalling grub:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Worked for me.

---

### Post by RookieUbuntuUser58 on 2009-01-14
> **thomasr said:**
> Here is a nice how to for reinstalling grub:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Worked for me.

Yeah I tried that method and the one in this thread (pretty similiar). Both report "Error 15: File Not Found" after the second code

---

### Post by RookieUbuntuUser58 on 2009-01-15
Bump really need help with this.

---

### Post by Elfy on 2009-01-15
Can ypoui boot the livecd and run ```
sudo fdisk -l
```

It will give you the number of your linux partition along with the rest in the form /dev/sdxy - run the foillowing and replace sdxy with your real dev number

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/sdxy /mnt/tmp
```

Assuming you get no errors, run thes and post the outputs please. Please also use code tags for each one.

```
cat /mnt/tmp/boot/grub/menu.lst
ls -al /mnt/tmp/boot
ls -al /mnt/tmp/boot/grub
sudo fdisk -l
blkid
```

---

### Post by RookieUbuntuUser58 on 2009-01-15
Here are the results for each of those codes here:> ```
cat /mnt/tmp/boot/grub/menu.lst
ls -al /mnt/tmp/boot
ls -al /mnt/tmp/boot/grub
sudo fdisk -l
blkid
```


```
cat: /mnt/tmp/boot/grub/menu.lst: No such file or directory

```

```
total 8
drwxr-xr-x  2 root root 4096 2009-01-05 17:08 .
drwxr-xr-x 20 root root 4096 2009-01-05 23:16 ..

```

```
ls: cannot access /mnt/tmp/boot/grub: No such file or directory

```

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38b83a1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5610    45062293+   7  HPFS/NTFS
/dev/sda2            5611       11347    46082452+  af  Unknown
/dev/sda3           11348       18195    55006560    5  Extended
/dev/sda4           18196       19457    10137015    b  W95 FAT32
/dev/sda5           11348       11921     4610623+  af  Unknown
/dev/sda6           11922       17878    47849571   83  Linux
/dev/sda7           17879       18182     2441848+  82  Linux swap / Solaris
/dev/sda8           18183       18195      104391   83  Linux

Disk /dev/sdb: 1001 MB, 1001390080 bytes
16 heads, 32 sectors/track, 3820 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x63664f08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          16        3820      973888    b  W95 FAT32

```

```
/dev/sdb1: LABEL="TRAVELDRIVE" UUID="1C6F-7294" TYPE="vfat" 

```

---

### Post by Elfy on 2009-01-15
When you did this bit - which drive did you use, sda6 or sda8?

sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/sdxy /mnt/tmp

TRy it again using the other drive number, before you do that if you haven't rebooted the livecd run this 

```
sudo umount /mnt/tmp
```

You shouldn't get > No such file or directoryif you still do can you follow the instructions [here]("http://ubuntuforums.org/showpost.php?p=6551995&postcount=4")

Make sure you surround the whole thing with code tags - don't put each in code tags - it'll take forever :)

---

### Post by MeURi on 2009-01-15
Assuming the Ubuntu root gets mounted under */mnt/tmp*, shouldn't it be (from GRUB prompt)
```

find /mnt/tmp/boot/grub/menu.lst

```
?

---

### Post by RookieUbuntuUser58 on 2009-01-15
> **forestpixie said:**
> When you did this bit - which drive did you use, sda6 or sda8?

sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/sdxy /mnt/tmp

TRy it again using the other drive number, before you do that if you haven't rebooted the livecd run this 

```
sudo umonut /mnt/tmp
```

You shouldn't get if you still do can you follow the instructions [here]("http://ubuntuforums.org/showpost.php?p=6551995&postcount=4")

Make sure you surround the whole thing with code tags - don't put each in code tags - it'll take forever :)

The first one I tried was sda6 and I just tried sda8 and it gave me all No such file or directory. I ran that code in the link you provided and also got:

```
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory

```

---

### Post by RookieUbuntuUser58 on 2009-01-15
Looks like Im gonna have to reinstall everything.:x

---

### Post by Elfy on 2009-01-15
Try a 

```
ls /mnt/tmp/
```
Sorry - the download wasn't in that post get it from here [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)

Then run the command again
sudo bash ~/Desktop/boot_info_script*.sh

Also I had a typo - command to run before rerunning the commands should have been

sudo umount /mnt/tmp

---

### Post by RookieUbuntuUser58 on 2009-01-15
Heres the result of ls /mnt/tmp/:

```
bin    dev   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
boot   etc   initrd.img.old  media       proc  srv   usr  vmlinuz.old
cdrom  home  lib             mnt         root  sys   var

```

and the result of the script

```
============================= Boot Info Summary: ==============================

 => Drive sdb does not have a valid partition table.
 => Lilo is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda5: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab /boot

sda7: _________________________________________________________________________

    File system:       swap

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sdc1 already mounted or sdc1 busy
mount: according to mtab, /dev/sdc1 is mounted on /cdrom

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38b83a1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    90124649    45062293+   7  HPFS/NTFS
/dev/sda2        90124650   182289554    46082452+  af  Unknown
/dev/sda3       182289555   292302674    55006560    5  Extended
/dev/sda4       292302675   312576704    10137015    b  W95 FAT32
/dev/sda5       182289618   191510864     4610623+  af  Unknown
/dev/sda6       191510928   287210069    47849571   83  Linux
/dev/sda7       287210133   292093829     2441848+  82  Linux swap / Solaris
/dev/sda8       292093893   292302674      104391   83  Linux

sfdisk -V /dev/sda:

partition 5: start: (c,h,s) expected (1023,254,63) found (0,1,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 1001 MB, 1001390080 bytes
16 heads, 32 sectors/track, 3820 cylinders, total 1955840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x63664f08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8064     1955839      973888    b  W95 FAT32

sfdisk -V /dev/sdc:

Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="FE9050739050347D" LABEL="OS_Install" TYPE="ntfs" 
/dev/sda2: UUID="D64B9290F85A5E93" LABEL="OSX Leopard" TYPE="hfsplus" 
/dev/sda4: LABEL="SHARED DATA" UUID="4965-0599" TYPE="vfat" 
/dev/sda5: UUID="78B437671F3DFBEC" LABEL="Mac OS X Install DVD Slipstream" TYPE="hfsplus" 
/dev/sda6: UUID="02f1c523-5a89-4456-985c-ff3aa3956182" TYPE="ext3" 
/dev/sda7: UUID="094ac38f-f8b6-47f2-8594-b698ee5fbfd8" TYPE="swap" 
/dev/sda8: UUID="82517249-aa07-4829-b0b1-4ca7009568b6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="TRAVELDRIVE" UUID="18CB-62CB" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda6 on /mnt/tmp type ext3 (rw)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect








=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=02f1c523-5a89-4456-985c-ff3aa3956182 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=82517249-aa07-4829-b0b1-4ca7009568b6 /boot           ext3    relatime        0       2
# /dev/sda7
UUID=094ac38f-f8b6-47f2-8594-b698ee5fbfd8 none            swap    sw              0       0

================================== sda6/boot: ==================================

total 8
drwxr-xr-x  2 root root 4096 2009-01-05 17:08 .
drwxr-xr-x 20 root root 4096 2009-01-05 23:16 ..

============================= sda8/grub/menu.lst: =============================

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
timeout		30

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
# kopt=root=UUID=02f1c523-5a89-4456-985c-ff3aa3956182 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=82517249-aa07-4829-b0b1-4ca7009568b6

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
uuid		82517249-aa07-4829-b0b1-4ca7009568b6
kernel		/vmlinuz-2.6.27-9-generic root=UUID=02f1c523-5a89-4456-985c-ff3aa3956182 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

##title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
##uuid		82517249-aa07-4829-b0b1-4ca7009568b6
##kernel		/vmlinuz-2.6.27-9-generic root=UUID=02f1c523-5a89-4456-985c-ff3aa3956182 ro  single
##initrd		/initrd.img-2.6.27-9-generic

##title		Ubuntu 8.10, kernel 2.6.27-7-generic
##uuid		82517249-aa07-4829-b0b1-4ca7009568b6
##kernel		/vmlinuz-2.6.27-7-generic root=UUID=02f1c523-5a89-4456-985c-ff3aa3956182 ro quiet splash 
##initrd		/initrd.img-2.6.27-7-generic
##quiet

##title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
##uuid		82517249-aa07-4829-b0b1-4ca7009568b6
##kernel		/vmlinuz-2.6.27-7-generic root=UUID=02f1c523-5a89-4456-985c-ff3aa3956182 ro  single
##initrd		/initrd.img-2.6.27-7-generic

##title		Ubuntu 8.10, memtest86+
##uuid		82517249-aa07-4829-b0b1-4ca7009568b6
##kernel		/memtest86+.bin
##quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
##title		Other operating systems:
##root

title          Mac OSX 10.5 Leopard
root           (hd0,1)
savedefault
makeactive
chainloader    +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1


================================== sda8/grub: ==================================

total 191
drwxr-xr-x 2 root root   1024 2009-01-07 16:51 .
drwxr-xr-x 4 root root   1024 2009-01-07 18:54 ..
-rw-r--r-- 1 root root    197 2009-01-05 17:16 default
-rw-r--r-- 1 root root     30 2009-01-05 17:16 device.map
-rw-r--r-- 1 root root   8108 2009-01-05 17:16 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-05 17:16 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-05 17:16 installed-version
-rw-r--r-- 1 root root   8712 2009-01-05 17:16 jfs_stage1_5
-rw-r--r-- 1 root root   5185 2009-01-07 16:51 menu.lst
-rw-r--r-- 1 root root   5177 2009-01-07 16:41 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-05 17:16 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-05 17:16 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-05 17:16 stage1
-rw-r--r-- 1 root root 121460 2009-01-05 17:16 stage2
-rw-r--r-- 1 root root   9556 2009-01-05 17:16 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/sda2

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 b9 01 00 00 00 b0  02 66 ba 00 e2 00 00 e8  |.f.......f......|
00000040  8f 00 81 3e 00 e4 48 2b  0f 85 7c 00 66 a1 28 e4  |...>..H+..|.f.(.|
00000050  66 0f c8 66 c1 e8 09 66  a3 06 e6 b0 04 8d 36 e3  |f..f...f......6.|
00000060  e3 8d 3e 20 e5 e8 98 01  75 3c 8d b6 1d 01 8b 34  |..> ....u<.....4|
00000070  81 3c 00 02 75 30 8b 5c  5e 86 fb 81 c3 ff 01 c1  |.<..u0.\^.......|
00000080  eb 09 80 fb 7e 77 1f 66  8b 44 08 66 0f c8 66 31  |....~w.f.D.f..f1|
00000090  c9 66 ba 00 02 02 00 8d  7c 68 e8 57 02 bf dd e3  |.f......|h.W....|
000000a0  e8 60 00 e9 19 00 66 8b  16 c0 e5 e8 1d 03 b0 7e  |.`....f........~|
000000b0  66 ba 00 02 02 00 e8 18  00 bf e3 e1 e8 44 00 8a  |f............D..|
000000c0  16 04 e6 ea 00 02 00 20  bf dd e1 e8 35 00 f4 eb  |....... ....5...|
000000d0  fd 66 60 06 89 e5 52 31  d2 66 c1 ea 04 8e c2 5b  |.f`...R1.f.....[|
000000e0  1e 1e 66 03 0e 00 e6 66  51 06 53 30 e4 50 68 10  |..f....fQ.S0.Ph.|
000000f0  00 8a 16 04 e6 89 e6 b4  42 cd 13 72 cb 89 ec 07  |........B..r....|
00000100  66 61 c3 66 60 57 be d3  e1 e8 07 00 5e e8 03 00  |fa.f`W......^...|
00000110  66 61 c3 bb 01 00 ac 3c  00 74 06 b4 0e cd 10 eb  |fa.....<.t......|
00000120  f5 c3 66 60 ad 86 e0 ab  3c 00 74 1c 89 c1 ad 09  |..f`....<.t.....|
00000130  c0 75 01 48 86 e0 80 fc  00 77 0a 3c 61 72 06 3c  |.u.H.....w.<ar.<|
00000140  7a 77 02 24 df ab e2 e6  66 61 c3 66 60 b2 00 66  |zw.$....fa.f`..f|
00000150  8b 44 02 66 3b 45 02 75  0f 80 3c 00 75 0a 66 8b  |.D.f;E.u..<.u.f.|
00000160  44 06 66 3b 45 06 74 48  77 44 72 3d 66 60 31 d2  |D.f;E.tHwDr=f`1.|
00000170  87 f7 66 ad 66 89 c1 87  f7 66 ad 66 39 c8 77 2e  |..f.f....f.f9.w.|
00000180  72 27 87 f7 ad 89 c1 87  f7 ad 80 f9 00 74 1f 39  |r'...........t.9|
00000190  c8 74 0b 77 07 fe ce 89  c1 e9 02 00 fe c6 f3 a7  |.t.w............|
000001a0  77 0c 72 05 88 f2 e9 07  00 fe ca e9 02 00 fe c2  |w.r.............|
000001b0  88 96 14 00 80 fa 00 66  61 c3 50 57 8b 3e 0a e6  |.......fa.PW.>..|
000001c0  57 47 47 49 49 b0 00 f3  aa 89 3e 0a e6 5d 89 2d  |WGGII.....>..].-|
000001d0  5f 58 c3 0d 0a 62 6f 6f  74 31 3a 20 00 65 72 72  |_X...boot1: .err|
000001e0  6f 72 00 73 74 61 72 74  75 70 66 69 6c 65 00 00  |or.startupfile..|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on /dev/sda5

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e c0 8e d8 b0 48 e8  |.1............H.|
00000010  3d 01 66 8b 44 08 e8 54  01 66 31 c0 66 a3 00 e4  |=.f.D..T.f1.f...|
00000020  80 7c 04 af 75 03 e9 09  00 be a6 7d e8 10 01 e9  |.|..u......}....|
00000030  c2 00 b0 5d e8 18 01 b0  01 31 db 8e c3 bb 00 14  |...].....1......|
00000040  66 b9 02 00 00 00 e8 ae  00 73 03 e9 9b 00 a1 00  |f........s......|
00000050  14 3d 42 44 75 3f b0 7c  e8 f4 00 66 8b 1e 14 14  |.=BDu?.|...f....|
00000060  66 0f cb 66 c1 fb 09 66  31 c0 a1 7e 14 86 c4 52  |f..f...f1..~...R|
00000070  66 f7 e3 5a 66 31 db 8b  1e 1c 14 86 df 66 01 d8  |f..Zf1.......f..|
00000080  66 40 66 40 66 89 c1 b0  01 31 db 8e c3 bb 00 14  |f@f@f....1......|
00000090  e8 64 00 72 54 b0 7d e8  b5 00 a1 00 14 3d 48 2b  |.d.rT.}......=H+|
000000a0  74 05 3d 48 58 75 42 b0  2a e8 a3 00 66 a1 28 14  |t.=HXuB.*...f.(.|
000000b0  66 0f c8 66 c1 f8 09 66  8b 1e c0 15 66 0f cb 52  |f..f...f....f..R|
000000c0  66 f7 e3 5a 66 48 66 48  66 01 c1 b0 21 e8 7f 00  |f..ZfHfHf...!...|
000000d0  b0 7e bb 00 20 8e c3 bb  00 02 e8 1a 00 72 0a b0  |.~.. ........r..|
000000e0  59 e8 6b 00 ea 00 02 00  20 be bd 7d e8 50 00 b0  |Y.k..... ..}.P..|
000000f0  58 e8 5b 00 f4 eb fd 66  60 89 e5 1e 1e 66 03 0e  |X.[....f`....f..|
00000100  00 e4 66 03 4c 08 66 51  06 53 30 e4 50 50 b0 2d  |..f.L.fQ.S0.PP.-|
00000110  e8 3c 00 66 89 c8 e8 54  00 b0 3d e8 31 00 58 e8  |.<.f...T..=.1.X.|
00000120  4b 00 68 10 00 89 e6 b4  42 cd 13 73 0d e8 3d 00  |K.h.....B..s..=.|
00000130  b0 52 e8 1a 00 31 c0 cd  13 f9 89 ec 66 61 c3 bb  |.R...1......fa..|
00000140  01 00 fc ac 3c 00 74 06  b4 0e cd 10 eb f5 c3 66  |....<.t........f|
00000150  60 bb 01 00 b4 0e cd 10  66 61 c3 66 60 31 c9 88  |`.......fa.f`1..|
00000160  c1 b0 20 e3 05 e8 e7 ff  e2 f9 66 61 c3 66 60 b9  |.. .......fa.f`.|
00000170  04 00 66 0f c8 50 c0 c8  04 e8 17 00 58 e8 13 00  |..f..P......X...|
00000180  66 c1 c8 08 e2 ef b0 0a  e8 c4 ff b0 0d e8 bf ff  |f...............|
00000190  66 61 c3 24 0f 04 30 3c  39 76 02 04 07 e8 af ff  |fa.$..0<9v......|
000001a0  c3 b4 00 cd 16 c3 0a 0d  48 46 53 2b 20 70 61 72  |........HFS+ par|
000001b0  74 69 74 69 6f 6e 20 65  72 72 6f 72 00 0a 0d 45  |tition error...E|
000001c0  72 72 6f 72 20 6c 6f 61  64 69 6e 67 20 62 6f 6f  |rror loading boo|
000001d0  74 65 72 00 00 00 00 00  00 00 00 00 00 00 00 00  |ter.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
sed: can't read sda2/etc/issue: No such file or directory
sed: can't read sda5/etc/issue: No such file or directory
```

---

### Post by RookieUbuntuUser58 on 2009-01-15
Anyone see anything in those logs I posted to help fix the problem?

---

### Post by Elfy on 2009-01-15
It's all there try this again - reboot with livecd 

[http://ubuntuforums.org/showpost.php?p=4542943&postcount=2](http://ubuntuforums.org/showpost.php?p=4542943&postcount=2)

I'd expect it to be saying that it's on hd0,7

---

### Post by RookieUbuntuUser58 on 2009-01-15
> **forestpixie said:**
> It's all there try this again - reboot with livecd 

[http://ubuntuforums.org/showpost.php?p=4542943&postcount=2](http://ubuntuforums.org/showpost.php?p=4542943&postcount=2)

I'd expect it to be saying that it's on hd0,7

I wonder if it is not working cause Im using a Live USB with Ubuntu on it to try and reinstall?

I tried ```
sudo mount /dev/Block device from sudo fdisk -l 
```from that thread but when I try it with sda6 it says "mount: can't find /dev/sda6 in /etc/fstab or /etc/mtab." Tried others doesn't work either.


I tried the ```
find /boot/grub/stage1
``` and again get "Error 15: File Not Found"

---

### Post by Elfy on 2009-01-15
Not quite sure how you managed to get /boot on sda6 and /grub on sda8 here. You say that you're expecting grub to be the bootloader but the script says you're using lilo.

I don't really know what chameleon is - I assume it's some type of bootloader from googling it.

Error 15 can appear when disk and partition are correct but it's the wrong file.

Try this 

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/sda8 /mnt/tmp
```

Then use the information in [http://ubuntuforums.org/showpost.php?p=4542943&postcount=2](http://ubuntuforums.org/showpost.php?p=4542943&postcount=2) again

If it fails to see it - replace
> 
find /boot/grub/stage1
with
> find /mnt/tmp/boot/grub/stage1

If not I don't know, you could try supergrub - download it and burn as an iso and boot with it - there are usb versions as well

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by RookieUbuntuUser58 on 2009-01-15
It didn't work. Honestly I dont know how all these things happened, for example instead of grub I have lilo. Seems chameleon messed up my system more than I though. I'm gonna erase all my partitions except XP and reinstall OSX. Unfortunately Ubuntu takes longer to setup so I can't reinstall it.:(

---


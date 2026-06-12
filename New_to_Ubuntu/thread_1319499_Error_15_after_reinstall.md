---
title: "Error 15 after reinstall"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by Lineata on 2009-11-08
I'm running Netbook Remix 9.04, and something possessed me to attempt to add another partition. Things didn't go quite as planned, so I figured it would be easiest to just do a clean install. I did precisely that and restored my backup, and everything was back to normal ... or so I thought, until I rebooted and was presented with "Error 15: File not found." 

I looked around to try to find my own solution, but I'm afraid I'm in way over my head. Any suggestions? I ran the Boot Info Script, which gave the following results:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
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

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 16.1 GB, 16139681792 bytes
255 heads, 63 sectors/track, 1962 cylinders, total 31522816 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0fc0398a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    30,105,809    30,105,747  83 Linux
/dev/sda2          30,105,810    31,519,529     1,413,720   5 Extended
/dev/sda5          30,105,873    31,519,529     1,413,657  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4013 MB, 4013948928 bytes
124 heads, 62 sectors/track, 1019 cylinders, total 7839744 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8ef631df

Partition  Boot         Start           End          Size  Id System

/dev/sdb1     ? 2,112,536,064 4,071,284,395 1,958,748,332  66 Unknown
/dev/sdb2     ? 3,449,352,939 7,393,689,600 3,944,336,662   7 HPFS/NTFS
/dev/sdb3     ? 3,279,813,678 5,233,273,711 1,953,460,034  7d Unknown
/dev/sdb4     ? 4,179,361,792 4,187,684,891     8,323,100  6f Unknown

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb1 overlaps with /dev/sdb2
/dev/sdb1 overlaps with /dev/sdb3
/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb2 overlaps with /dev/sdb3
/dev/sdb2 overlaps with /dev/sdb4
/dev/sdb3 ends after the last sector of /dev/sdb
/dev/sdb3 overlaps with /dev/sdb4
/dev/sdb4 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="a53ab18b-32b5-4683-87a2-5c38a4e1f568" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="d1053099-6ece-4461-9770-234097ee71eb" TYPE="swap" 
/dev/sdb: UUID="49ED-21FF" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sdb on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b62b897e-3771-4d99-aa0c-236afc8c48f0

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d1053099-6ece-4461-9770-234097ee71eb none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  10.4GB: boot/grub/menu.lst
  10.4GB: boot/grub/stage2
  10.4GB: boot/initrd.img-2.6.28-11-generic
  10.4GB: boot/initrd.img-2.6.28-14-generic
  10.4GB: boot/initrd.img-2.6.28-15-generic
  10.4GB: boot/initrd.img-2.6.28-16-generic
  10.4GB: boot/vmlinuz-2.6.28-11-generic
  10.4GB: boot/vmlinuz-2.6.28-14-generic
  10.4GB: boot/vmlinuz-2.6.28-15-generic
  10.3GB: boot/vmlinuz-2.6.28-16-generic
  10.4GB: initrd.img
  10.4GB: initrd.img.old
  10.3GB: vmlinuz
  10.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  eb 58 90 6d 6b 64 6f 73  66 73 00 00 02 08 20 00  |.X.mkdosfs.... .|
00000010  02 00 00 00 00 f8 00 00  20 00 40 00 00 00 00 00  |........ .@.....|
00000020  c0 96 1d 00 62 07 00 00  00 00 00 00 02 00 00 00  |....b...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 ff 21 ed 49 20  20 20 20 20 20 20 20 20  |..).!.I         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c0 8e d0  |  FAT32   ..1...|
00000060  bc b4 7b 06 57 8e c0 b9  08 00 bf b4 7b f3 a5 8e  |..{.W.......{...|
00000070  d8 bb 78 00 0f b4 37 0f  a0 56 88 16 21 c7 20 d2  |..x...7..V..!. .|
00000080  78 15 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |x....?.G..d....||
00000090  88 4d f8 cd 13 eb 27 f6  45 f0 7f 75 08 66 8b 45  |.M....'.E..u.f.E|
000000a0  f8 66 a3 1c 7c b4 08 cd  13 72 13 20 e4 75 0f c1  |.f..|....r. .u..|
000000b0  ea 08 42 89 16 1a 7c 83  e1 3f 89 0e 18 7c fb bb  |..B...|..?...|..|
000000c0  aa 55 b4 41 8a 16 21 c7  cd 13 72 10 81 fb 55 aa  |.U.A..!...r...U.|
000000d0  75 0a f6 c1 01 74 05 c6  06 05 7d 00 66 a1 f8 7d  |u....t....}.f..}|
000000e0  bb 00 7e e8 10 00 66 81  3e 2c 7e e8 e1 06 77 0f  |..~...f.>,~...w.|
000000f0  85 c6 00 e9 42 02 bd 01  00 66 03 06 1c 7c 66 31  |....B....f...|f1|
00000100  d2 e9 00 00 eb 4f 55 e8  d5 00 66 0f b7 fd b9 10  |.....OU...f.....|
00000110  00 66 52 66 50 06 53 57  6a 10 89 e6 66 60 8a 16  |.fRfP.SWj...f`..|
00000120  21 c7 1e 16 1f b4 42 cd  13 1f 66 61 8d 64 10 72  |!.....B...fa.d.r|
00000130  10 5d 66 01 f8 29 fd c1  e7 09 01 fb 21 ed 75 c6  |.]f..)......!.u.|
00000140  c3 66 60 31 c0 8a 16 21  c7 cd 13 66 61 e2 c2 c6  |.f`1...!...fa...|
00000150  06 05 7d 4f 5d 66 52 66  50 55 53 66 0f b7 36 18  |..}O]fRfPUSf..6.|
00000160  7c 66 0f b7 3e 1a 7c 66  f7 f6 31 c9 87 ca 66 f7  ||f..>.|f..1...f.|
00000170  f7 e8 6b 00 29 ce 39 f5  76 02 89 f5 c0 e4 06 41  |..k.).9.v......A|
00000180  08 e1 88 c5 88 d6 8a 16  21 c7 95 b4 02 bd 10 00  |........!.......|
00000190  66 60 cd 13 66 61 72 17  66 0f b6 c8 c1 e0 09 5b  |f`..far.f......[|
000001a0  01 c3 5d 66 58 66 5a 66  01 c8 29 cd 75 a7 c3 4d  |..]fXfZf..).u..M|
000001b0  75 de 95 d1 2e fc 7d 75  df 31 f6 8e d6 bc b0 7b  |u.....}u.1.....{|
000001c0  8e de 66 8f 06 78 00 be  ea 7d ac 20 c0 74 09 b4  |..f..x...}. .t..|
000001d0  0e bb 07 00 cd 10 eb f2  98 cd 16 cd 19 eb fe 3b  |...............;|
000001e0  2e fc 7d 76 04 8b 2e fc  7d c3 42 6f 6f 74 20 65  |..}v....}.Boot e|
000001f0  72 72 6f 72 0d 0a 00 00  1c f9 1c 00 7f 00 55 aa  |rror..........U.|
00000200

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory
```

---

### Post by listerdl on 2009-11-08
The same thing happened to me about an hour ago and I fixed it by simply re-installing the USB drive.

Are you installing the drive via the admin > create a USB Start-up disk?

If so then re-do that and it might well overwrite the problem.

---

### Post by LewRockwell on 2009-11-08
looks like you've got an SD card or thumb drive that is goofed up

you'll want to read this then:

[http://ubuntuforums.org/showthread.php?t=1300716](http://ubuntuforums.org/showthread.php?t=1300716)

.

---

### Post by Lineata on 2009-11-08
I'll certainly reformat the USB stick, but do you think that's what's causing the GRUB problem? I'm using it as my LiveCD (and running off it right now), but it isn't inserted when I'm attempting to boot for real and getting the errors. 

(Sorry if I'm a bit clueless here!)

---

### Post by yanceypd on 2009-11-08
Recheck bios on bootup that it points to correct drive.  Happened to me.:D

---

### Post by LewRockwell on 2009-11-08
you might try reinstalling grub

[http://sunnyideas.wordpress.com/2008/04/05/reinstalling-grub-on-ubuntu/](http://sunnyideas.wordpress.com/2008/04/05/reinstalling-grub-on-ubuntu/)

.

---

### Post by Lineata on 2009-11-08
I tried reinstalling GRUB, but no luck. 

I did notice one thing, but I'm not sure if it's of any significance. Up near the top of the script results, it says:

```
/dev/sda1: UUID="a53ab18b-32b5-4683-87a2-5c38a4e1f568" SEC_TYPE="ext2" TYPE="ext3"
```

But, down in the kernel-y part, the UUID seems to be different. Is this related, or am I grasping at straws?

```
title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        b62b897e-3771-4d99-aa0c-236afc8c48f0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b62b897e-3771-4d99-aa0c-236afc8c48f0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d1053099-6ece-4461-9770-234097ee71eb none            swap    sw              0   
```

---

### Post by LewRockwell on 2009-11-08
figure out which is the correct UUID and then correct those entries which are incorrect

that should fix things

.

---

### Post by Lineata on 2009-11-08
Where/how do I go about correcting the incorrect ones? (I don't want to edit the wrong thing by mistake and botch things even further...)

---

### Post by LewRockwell on 2009-11-08
> **Lineata said:**
> Where/how do I go about correcting the incorrect ones? (I don't want to edit the wrong thing by mistake and botch things even further...)

boot into the LiveCD

Here we create a backup copy of your current menu.lst file```
cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```Then we want to edit the file and replace the old UUID with the new one```
gksudo gedit /boot/grub/menu.lst
```After you edit the file don't forget to save it

Looks like your old UUID is b62b897e-3771-4d99-aa0c-236afc8c48f0

So you should replace those with the new one which is a53ab18b-32b5-4683-87a2-5c38a4e1f568

(double-check those and your procedural notes before you make changes)

keep us posted on your progress!

.

---

### Post by kansasnoob on 2009-11-08
I see LewRockwell beat me while I was typing, but if you're still having trouble:

You'd have to replace all of the UUID's in the menu.lst with the UUID shown in blkid -c/dev/null.

I think it would be easiest to mount and chroot sda1, then back up the old menu.lst and create a new one like this:

```
sudo mount /dev/sda1 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```

```
sudo chroot /mnt
```

You'll notice the bash prompt change to #. No sudo is needed for these next commands:

```
mv /boot/grub/menu.lst /boot/grub/menu.lst_old
```

```
update-grub
```

Note: update-grub should result in this (you have to say yes (y) to generate the new menu.lst):

> Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

**Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) [B][COLOR="Red"]y[/COLOR]**[/B]
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-12-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


To see if things are now right just run the following to compare UUID's:

```
blkid -c /dev/null
```

```
cat /boot/grub/menu.lst
```

If it's still wrong edit the menu.lst while stiil mounted & chroot using the commands LewRockwell gave. (In that case you might find the UUID's in /etc/fstab and /etc/initramfs-tools/conf.d/resume are also wrong, but we can deal with that after you get booting.

When done:

```
exit
```

```
sudo umount /mnt/dev
```

```
sudo umount /mnt/proc
```

```
sudo umount /mnt
```

Hopefully that'll do it.

---

### Post by LewRockwell on 2009-11-08
```
> **kansasnoob said:**
> I see LewRockwell beat me while I was typing, but if you're still having trouble:

You'd have to replace all of the UUID's in the menu.lst with the UUID shown in blkid -c/dev/null.

I think it would be easiest to mount and chroot sda1, then back up the old menu.lst and create a new one like this:

[CODE]sudo mount /dev/sda1 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```

```
sudo chroot /mnt
```

You'll notice the bash prompt change to #. No sudo is needed for these next commands:

```
mv /boot/grub/menu.lst /boot/grub/menu.lst_old
```

```
update-grub
```

Note: update-grub should result in this (you have to say yes (y) to generate the new menu.lst):



To see if things are now right just run the following to compare UUID's:

```
blkid -c /dev/null
```

```
cat /boot/grub/menu.lst
```

If it's still wrong edit the menu.lst while stiil mounted & chroot using the commands LewRockwell gave. (In that case you might find the UUID's in /etc/fstab and /etc/initramfs-tools/conf.d/resume are also wrong, but we can deal with that after you get booting.

When done:

```
exit
```

```
sudo umount /mnt/dev
```

```
sudo umount /mnt/proc
```

```
sudo umount /mnt
```

Hopefully that'll do it.[/code]

definitely thorough, intimidating to the faint-at-heart though...lol

.

---

### Post by Lineata on 2009-11-08
LewRockwell's steps worked like a charm. (I'll keep the more comprehensive variant in mind for the next time I get myself in this sort of situation!)

Thank you so, so much for all the help!

---


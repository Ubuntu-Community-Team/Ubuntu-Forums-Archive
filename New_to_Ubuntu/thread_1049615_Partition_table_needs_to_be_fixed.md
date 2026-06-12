---
title: "Partition table needs to be fixed"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by fluzao on 2009-01-24
My computer is a Asus M50sa Laptop.
Let me describe where I stand right now. Booting with GParted Live CD, GParted shows all the space on my hd unallocated. The output for fdisk -l is:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x6906069f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8192000    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sda2            1020       30217   234524896+   7  HPFS/NTFS
/dev/sda3           30218       32899    21543165    7  HPFS/NTFS
/dev/sda4           32900       60802   224130847+   f  W95 Ext'd (LBA)
/dev/sda5           32900       33872     7815556   83  Linux
/dev/sda6           33873       36060    17575076   83  Linux
/dev/sda7           36061       36888     6650868   82  Linux Swap / Solaris
/dev/sda8           36889       60802   192074752    7  HPFS/NTFS
```

Here is what I think is on each partition:

sda1: ASUS Vista recovery partition
sda2: Original Vista partition
sda3: XP install I did before installing Ubuntu. Was working perfectly before Ubuntu
sda4: I have no clue!
sda5: /home
sda6: /
sda7: swap
sda8: windows data

What is currently happening on boot?
It boots from sda1 and enters the ASUS Recovery screen.

My short term goals:
Have XP on sda3 working again.

My long term goals:
Have the computer dual boot XP on sda3 and Ubuntu on sda6. Vista on sda2 don't have to work, but I would like to access its contents.

How thing happened?
1. Laptop came with Vista. Gave up after a few weeks. Using GParted created a Partition for XP.
2. Vista stoped working, but I didn't care. Installed XP on the new partition. XP was working flawlessly.
3. Installed Ubuntu 8.10 64-bits. Ubuntu was working fine, but GRUB only had two options for other OS: one lead to the recovery CD (sda1), the other to the non-working Vista install (sda2).

Tried to fix GRUB, making an entry for hd(0,2), but it did not work. From that on, I've tried many things but kinda lost control.

Final information. Using testdisk on GParted Live CD, it seems that it gets the correct partition table (similar to the one above, but without sda4). But when I ask it to write and reboot, GParted still has everything unallocated and fdisk -l produces the same output.

I am grateful for any help.

---

### Post by caljohnsmith on 2009-01-24
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by fluzao on 2009-01-25
Thanks caljohnsmith. Here it is:

```
============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  The info in boot sector on the starting sector of the 
                       MFT is wrong. The info in the boot sector on the 
                       starting sector of the MFT Mirror is wrong.
    Mounting failed:
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda3': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda3 sda3 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda3 sda3 ntfs-3g defaults,force 0 0

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 2048.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda8': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda8 sda8 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda8 sda8 ntfs-3g defaults,force 0 0

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

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6906069f

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *         2,048   16,386,047   16,384,000   b W95 FAT32
/dev/sda2         16,386,048  485,435,840  469,049,793   7 HPFS/NTFS
/dev/sda3        485,436,105  528,522,434   43,086,330   7 HPFS/NTFS
/dev/sda4        528,522,435  976,784,129  448,261,695   f W95 Ext'd (LBA)
/dev/sda5        528,522,561  544,153,672   15,631,112  83 Linux
/dev/sda6        544,153,743  579,303,894   35,150,152  83 Linux
/dev/sda7        579,303,963  592,605,698   13,301,736  82 Linux swap / Solaris
/dev/sda8        592,621,568  976,771,071  384,149,504   7 HPFS/NTFS

/dev/sda4 ends after the last sector of /dev/sda
/dev/sda8 ends after the last cylinder of /dev/sda

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 1031 MB, 1031798784 bytes
32 heads, 62 sectors/track, 1015 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x73696420

Partition  Boot        Start          End         Size  Id System

/dev/sdb1     ?1,919,950,9582,464,388,050  544,437,093  20 
/dev/sdb2     ?1,330,184,2021,869,160,489  538,976,288  6b 
/dev/sdb3     ?  538,989,3911,937,352,3021,398,362,912  53 OnTrack DM6 Aux3
/dev/sdb4    * 1,394,627,6631,394,648,999       21,337  49 

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb1 overlaps with /dev/sdb3
/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb2 overlaps with /dev/sdb3
/dev/sdb2 overlaps with /dev/sdb4
/dev/sdb3 ends after the last sector of /dev/sdb
/dev/sdb3 overlaps with /dev/sdb4
/dev/sdb4 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="RECOVERY" UUID="800E-1B1C" TYPE="vfat" 
/dev/sda3: UUID="E88471208470F284" TYPE="ntfs" 
/dev/sda5: UUID="07bd81b2-d434-4f11-8d1b-4d2b9220cd95" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="0aaadb23-2016-48bd-81ae-868b10c6f890" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="9aaa6be1-d8e1-4d58-a474-34e54fe6813d" TYPE="swap" 
/dev/sda8: UUID="501862151861F9FC" LABEL="DATA" TYPE="ntfs" 
/dev/sdb: SEC_TYPE="msdos" UUID="4574-0809" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdb on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077,usefree)

=========================== sda6/boot/grub/menu.lst: ===========================

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
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=0aaadb23-2016-48bd-81ae-868b10c6f890 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0aaadb23-2016-48bd-81ae-868b10c6f890

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
uuid		0aaadb23-2016-48bd-81ae-868b10c6f890
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0aaadb23-2016-48bd-81ae-868b10c6f890 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		0aaadb23-2016-48bd-81ae-868b10c6f890
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0aaadb23-2016-48bd-81ae-868b10c6f890 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0aaadb23-2016-48bd-81ae-868b10c6f890
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0aaadb23-2016-48bd-81ae-868b10c6f890 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0aaadb23-2016-48bd-81ae-868b10c6f890
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0aaadb23-2016-48bd-81ae-868b10c6f890 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0aaadb23-2016-48bd-81ae-868b10c6f890
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title		Windows XP
root		(hd0,2)
savedefault
#makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Windows Vista/Longhorn (loader)
#root		(hd0,0)
#savedefault
#makeactive
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title		Windows Vista/Longhorn (loader)
#root		(hd0,1)
#savedefault
#makeactive
#chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=0aaadb23-2016-48bd-81ae-868b10c6f890 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=07bd81b2-d434-4f11-8d1b-4d2b9220cd95 /home           ext3    relatime        0       2
# /dev/sda8
UUID=9aaa6be1-d8e1-4d58-a474-34e54fe6813d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location  of files loaded by Grub: ===================


 292.0GB: boot/grub/menu.lst
 292.0GB: boot/grub/stage2
 292.1GB: boot/initrd.img-2.6.27-7-generic
 292.1GB: boot/initrd.img-2.6.27-9-generic
 292.0GB: boot/vmlinuz-2.6.27-7-generic
 292.1GB: boot/vmlinuz-2.6.27-9-generic
 292.1GB: initrd.img
 292.1GB: initrd.img.old
 292.1GB: vmlinuz
 292.0GB: vmlinuz.old

=========================== Unknown MBRs or Boot Sectors =======================

Unknown MBR on /dev/sdb

00000000  eb 3e 90 2a 35 3e 2b 6b  49 48 43 00 02 20 08 00  |.>.*5>+kIHC.. ..|
00000010  02 00 02 00 00 f8 f8 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 c0 1e 00 00 01 29 09  08 74 45 20 20 20 20 20  |......)..tE     |
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 f1 7d  |      FAT16   .}|
00000040  fa 33 c9 8e d1 bc fc 7b  16 07 bd 78 00 c5 76 00  |.3.....{...x..v.|
00000050  1e 56 16 55 bf 22 05 89  7e 00 89 4e 02 b1 0b fc  |.V.U."..~..N....|
00000060  f3 a4 06 1f bd 00 7c c6  45 fe 0f 8b 46 18 88 45  |......|.E...F..E|
00000070  f9 fb 38 66 24 7c 04 cd  13 72 3c 8a 46 10 98 f7  |..8f$|...r<.F...|
00000080  66 16 03 46 1c 13 56 1e  03 46 0e 13 d1 50 52 89  |f..F..V..F...PR.|
00000090  46 fc 89 56 fe b8 20 00  8b 76 11 f7 e6 8b 5e 0b  |F..V.. ..v....^.|
000000a0  03 c3 48 f7 f3 01 46 fc  11 4e fe 5a 58 bb 00 07  |..H...F..N.ZX...|
000000b0  8b fb b1 01 e8 94 00 72  47 38 2d 74 19 b1 0b 56  |.......rG8-t...V|
000000c0  8b 76 3e f3 a6 5e 74 4a  4e 74 0b 03 f9 83 c7 15  |.v>..^tJNt......|
000000d0  3b fb 72 e5 eb d7 2b c9  b8 d8 7d 87 46 3e 3c d8  |;.r...+...}.F><.|
000000e0  75 99 be 80 7d ac 98 03  f0 ac 84 c0 74 17 3c ff  |u...}.......t.<.|
000000f0  74 09 b4 0e bb 07 00 cd  10 eb ee be 83 7d eb e5  |t............}..|
00000100  be 81 7d eb e0 33 c0 cd  16 5e 1f 8f 04 8f 44 02  |..}..3...^....D.|
00000110  cd 19 be 82 7d 8b 7d 0f  83 ff 02 72 c8 8b c7 48  |....}.}....r...H|
00000120  48 8a 4e 0d f7 e1 03 46  fc 13 56 fe bb 00 07 53  |H.N....F..V....S|
00000130  b1 04 e8 16 00 5b 72 c8  81 3f 4d 5a 75 a7 81 bf  |.....[r..?MZu...|
00000140  00 02 42 4a 75 9f ea 00  02 70 00 50 52 51 91 92  |..BJu....p.PRQ..|
00000150  33 d2 f7 76 18 91 f7 76  18 42 87 ca f7 76 1a 8a  |3..v...v.B...v..|
00000160  f2 8a 56 24 8a e8 d0 cc  d0 cc 0a cc b8 01 02 cd  |..V$............|
00000170  13 59 5a 58 72 09 40 75  01 42 03 5e 0b e2 cc c3  |.YZXr.@u.B.^....|
00000180  03 18 01 27 0d 0a 49 6e  76 61 6c 69 64 20 73 79  |...'..Invalid sy|
00000190  73 74 65 6d 20 64 69 73  6b ff 0d 0a 44 69 73 6b  |stem disk...Disk|
000001a0  20 49 2f 4f 20 65 72 72  6f 72 ff 0d 0a 52 65 70  | I/O error...Rep|
000001b0  6c 61 63 65 20 74 68 65  20 64 69 73 6b 2c 20 61  |lace the disk, a|
000001c0  6e 64 20 74 68 65 6e 20  70 72 65 73 73 20 61 6e  |nd then press an|
000001d0  79 20 6b 65 79 0d 0a 00  49 4f 20 20 20 20 20 20  |y key...IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 80 01  |SYSMSDOS   SYS..|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

MFT Sector of sda2

00000000  4d 00 50 00 00 00 00 00  01 c5 7f 04 00 00 00 00  |M.P.............|
00000010  eb c4 7f 04 00 00 00 00  eb c4 7f 04 00 00 00 00  |................|
00000020  68 00 00 00 00 00 00 00  01 00 00 00 68 00 00 00  |h...........h...|
00000030  00 00 00 00 00 00 00 00  0b 00 0b 00 28 00 20 00  |............(. .|
00000040  48 00 20 00 18 00 01 00  08 01 00 00 00 00 00 00  |H. .............|
00000050  f4 44 00 00 00 00 00 00  f4 44 0c 00 00 00 00 00  |.D.......D......|
00000060  00 00 7d 7f 00 00 00 00  d0 0f 75 7f 00 00 00 00  |..}.......u.....|
00000070  d0 0f 75 7f 00 00 00 00  00 00 0d 02 00 00 00 00  |..u.............|
00000080  00 00 7d 7f 00 00 00 00  78 0f 75 7f 00 00 00 00  |..}.....x.u.....|
00000090  d0 0f 75 7f 00 00 00 00  00 00 0d 02 00 00 00 00  |..u.............|
000000a0  14 c5 7f 04 00 00 00 00  01 c5 7f 04 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  28 00 00 00 00 00 00 00  |........(.......|
000000c0  01 00 00 00 68 00 00 00  00 00 00 00 00 00 00 00  |....h...........|
000000d0  1b 00 01 00 28 00 00 00  28 00 08 00 18 00 00 00  |....(...(.......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 7d 7f 00 00 00 00  1f c5 7f 04 00 00 00 00  |..}.............|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  98 00 00 00 00 00 00 00  01 00 00 00 68 00 00 00  |............h...|
00000120  00 00 00 00 00 00 00 00  14 00 14 00 28 00 38 00  |............(.8.|
00000130  60 00 38 00 e4 09 01 00  00 00 40 0c 00 00 00 00  |`.8.......@.....|
00000140  01 00 00 00 00 00 00 00  e4 7d 1c 00 00 00 00 00  |.........}......|
00000150  b0 b7 53 33 50 7d c9 01  00 40 a5 87 42 06 c6 01  |..S3P}...@..B...|
00000160  b0 b7 53 33 50 7d c9 01  b0 b7 53 33 50 7d c9 01  |..S3P}....S3P}..|
00000170  48 00 00 00 00 00 00 00  41 00 00 00 00 00 00 00  |H.......A.......|
00000180  20 00 00 00 00 00 00 00  b0 b7 53 33 50 7d c9 01  | .........S3P}..|
00000190  b0 b7 53 33 50 7d c9 01  b0 b7 53 33 50 7d c9 01  |..S3P}....S3P}..|
000001a0  b0 b7 53 33 50 7d c9 01  00 00 00 00 00 00 00 00  |..S3P}..........|
000001b0  00 00 00 00 00 00 00 00  20 00 00 00 00 00 00 00  |........ .......|
000001c0  38 c5 7f 04 00 00 00 00  1f c5 7f 04 00 00 00 00  |8...............|
000001d0  00 00 00 00 00 00 00 00  28 00 00 00 00 00 00 00  |........(.......|
000001e0  01 00 00 00 68 00 00 00  00 00 00 00 00 00 00 00  |....h...........|
000001f0  1b 00 01 00 28 00 00 00  28 00 08 00 18 00 5a a8  |....(...(.....Z.|
00000200
Unknown BootLoader  on sda4

00000000  74 c1 e7 d6 be d8 87 71  54 c9 f9 7d 8e 73 5f 85  |t......qT..}.s_.|
00000010  9f f0 4f af 8a 1a 0f 84  3c 71 af f8 6f 5d bb 26  |..O.....<q..o].&|
00000020  e3 c4 f7 0a b1 2a 36 3c  b5 04 2b 85 3d d8 0f 5e  |.....*6<..+.=..^|
00000030  d5 fb 81 25 cb 2b 0f 22  19 8c 4a 46 d1 20 da 4a  |...%.+."..JF. .J|
00000040  1e 84 e7 da bc fc 5d 29  55 ab cb 29 1d b8 9a 51  |......])U..)...Q|
00000050  c2 e2 dc 29 42 d1 7a a3  a7 82 38 e4 24 b3 6d f7  |...)B.z...8.$.m.|
00000060  c7 5a 86 ee ed 2c 60 b9  bb 72 d1 da 58 5b bd dd  |.Z...,`..r..X[..|
00000070  ec e7 a4 31 a8 24 93 f9  55 78 25 e5 00 6c 17 1b  |...1.$..Ux%..l..|
00000080  ba fd da e1 3e 25 2d e5  e7 81 fc 67 a7 41 78 60  |....>%-....g.Ax`|
00000090  4b df 0e dc a9 89 18 87  9d c2 92 a0 62 aa 1c 95  |K...........b...|
000000a0  1b e7 d5 23 97 13 ed 1c  94 25 bb 3e 37 b7 fd a5  |...#.....%.>7...|
000000b0  be 20 fc 56 f1 86 ad a1  fc 28 d3 e2 ba b1 f0 fb  |. .V.....(......|
000000c0  c9 1d e6 a3 22 6e da 03  11 b5 30 3e f1 c0 ff 00  |...."n....0>....|
000000d0  26 be 7a f0 36 a9 e2 5f  13 7e dc 5a 3c 1e 39 81  |&.z.6.._.~.Z<.9.|
000000e0  d3 c4 72 5b 05 fb 44 a9  b3 ed 21 38 44 51 d1 71  |..r[..D...!8DQ.q|
000000f0  f3 67 d7 15 e8 7f f0 4e  49 20 b9 f0 bf c4 58 2e  |.g.....NI ....X.|
00000100  04 5a 37 89 7c 35 e2 bf  ec 57 b4 0d f3 06 2f b9  |.Z7.|5...W..../.|
00000110  9a 42 d8 6d a1 79 dd cf  6a a1 e2 7b db 1b bf f8  |.B.m.y..j..{....|
00000120  28 0f 87 0e 8f 2d ad d4  56 b3 c5 a4 8b 84 72 61  |(....-..V.....ra|
00000130  8a f4 a9 fd e1 6e 8c b8  2c 0e 7d 6b ba ad 3a b2  |.....n..,.}k..:.|
00000140  a4 a5 19 69 d0 eb 87 d5  b0 b8 fa d8 1a 54 f5 51  |...i.........T.Q|
00000150  dc fd 4a d5 f5 cb 1f 0e  e8 ba b6 b1 a8 17 7b 3d  |..J...........{=|
00000160  26 dc dc 34 e0 6d 45 41  9e b9 fa 57 c3 7e 13 f8  |&..4.mEA...W.~..|
00000170  e3 f1 07 e3 6e a9 e3 49  fe 1b db da db 68 be 18  |....n..I.....h..|
00000180  0d 30 79 e1 2d 14 ea 99  f9 fa f4 6e 07 d4 d7 d1  |.0y.-......n....|
00000190  5f b4 77 db 74 ef 82 9e  3b 87 4d 67 32 b6 85 25  |_.w.t...;.Mg2..%|
000001a0  a3 c5 18 dc ae 83 3c 2f  a7 cd 5f 99 1f b1 1f 87  |......</.._.....|
000001b0  3e 26 6b 1e 02 d6 a5 f0  8f 89 ec f4 2b e5 00 fe  |>&k.........+...|
000001c0  ff ff 83 fe ff ff 7e 00  00 00 08 83 ee 00 00 fe  |......~.........|
000001d0  ff ff 05 fe ff ff 8d 83  ee 00 87 59 18 02 00 00  |...........Y....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4



=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sda1: device is busy
umount: /tmp/BootInfo/sda1: device is busy
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

### Post by caljohnsmith on 2009-01-25
OK, how about doing:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda2
sudo ntfsfix /dev/sda3
```
And please post the output. Based on the errors you got, it looks like the ntfsfix on sda2 will probably fail, but hopefully it will work on sda3. If it works on sda3, how about posting the output of:
```
sudo mount /dev/sda3 /mnt && ls -l /mnt && cat /mnt/boot.ini
```
And we can go from there.

---

### Post by fluzao on 2009-01-25
```
ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda2
Mounting volume... Failed to load $MFT : Input/output error
Failed to startup volume : Input/output error
FAILED
Attempting to correct errors... Failed to load $MFT : Input/output error
FAILED
Failed to startup volume : Input/output error
Volume is corrupt. You should run chkdsk.

ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda3
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda3 was processed successfully.

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt && ls -l /mnt && cat /mnt/boot.ini
total 2095176
drwxrwxrwx 1 root root          0 2009-01-20 16:10 ATI
drwxrwxrwx 1 root root       4096 2009-01-23 10:52 blp
drwxrwxrwx 1 root root       4096 2009-01-20 14:12 Documents and Settings
drwxrwxrwx 1 root root          0 2009-01-20 20:15 Intel
drwxrwxrwx 1 root root          0 2009-01-23 11:00 MSOCache
-rwxrwxrwx 1 root root 2145386496 2009-01-23 10:57 pagefile.sys
drwxrwxrwx 1 root root      12288 2009-01-23 14:53 Program Files
drwxrwxrwx 1 root root          0 2009-01-20 15:59 RECYCLER
drwxrwxrwx 1 root root       4096 2009-01-20 14:11 System Volume Information
drwxrwxrwx 1 root root      49152 2009-01-23 11:01 WINDOWS
cat: /mnt/boot.ini: No such file or directory
```

---

### Post by caljohnsmith on 2009-01-25
How about booting your XP Install CD, go to the command line ("recovery console"), and do:
```
map
```
That gives the drive letters for your NTFS partitions, choose the sda2 partition drive letter and try:
```
chkdsk /r D:
```
And replace "D" with the sda2 drive letter. Also run the chkdsk command as many times as it takes until it reports no errors. Then try mounting sda2 again in Ubuntu:
```
sudo mount -t ntfs-3g /dev/sda2 /mnt && ls -l /mnt
```
Let me know how that goes.

---

### Post by fluzao on 2009-01-26
First, when entering the recovery console, it asked me "Which Windows installation would you like to log onto", 1: F:\WINDOWS being the only option. Not bad, to be honest, as F: was the letter XP was using.

The result for map is:

```
C: FAT32       8001MB     \Device\Harddisk0\Partition1
E:           229028MB     \Device\Harddisk0\Partition2
F: NTFS       21039MB     \Device\Harddisk0\Partition3
H:             7632MB     \Device\Harddisk0\Partition4
I:            17163MB     \Device\Harddisk0\Partition5
J:             6495MB     \Device\Harddisk0\Partition6
D: NTFS      187574MB     \Device\Harddisk0\Partition7
G:             8001MB     \Device\CdRom0
```

```
chkdsk /r E:

The volume appears to contain one or more unrecoverable problems.
```

So, it was no surprise when this happened:

```
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda2 /mnt && ls -l /mnt
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
```

Honestly, sda2 is the least of my concerns.

---

### Post by caljohnsmith on 2009-01-26
> **fluzao said:**
> 

```

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total [COLOR="Red"]976773168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6906069f

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *         2,048   16,386,047   16,384,000   b W95 FAT32
/dev/sda2         16,386,048  485,435,840  469,049,793   7 HPFS/NTFS
/dev/sda3        485,436,105  528,522,434   43,086,330   7 HPFS/NTFS
/dev/sda4        528,522,435  [COLOR="Red"]976,784,129[/COLOR]  448,261,695   f W95 Ext'd (LBA)
/dev/sda5        528,522,561  544,153,672   15,631,112  83 Linux
/dev/sda6        544,153,743  579,303,894   35,150,152  83 Linux
/dev/sda7        579,303,963  592,605,698   13,301,736  82 Linux swap / Solaris
/dev/sda8        592,621,568  976,771,071  384,149,504   7 HPFS/NTFS

[COLOR="Red"]/dev/sda4 ends after the last sector of /dev/sda[/COLOR]
/dev/sda8 ends after the last cylinder of /dev/sda

```
As shown highlighted in red above, your extended partition ending sector exceeds the total available sectors on the HDD, so that's why gparted sees the drive as unallocated: the partition table is unfortunately corrupt. How about we correct that problem first, and then if you still want to try and get sda2 mountable and readable, we can work on that afterwards. To correct the partition table problem, how about doing the following command:
```
echo "528522435,448248637,f" | sudo sfdisk --no-reread -fuS /dev/sda -N4 -O ~/Desktop/sda_sectors_modified.save
```
And please post the output. The above command will create a backup of the few sectors being modified as a small "sda_sectors_modified.save" file on your desktop, so if for some reason anything were to go wrong, we can easily restore your original partition table with that file. Therefore, please copy that file to a different drive, or you could for instance save it to your email account or something like that. Next reboot, and please post the new output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
```
And we can work from there.

---

### Post by fluzao on 2009-01-26
Thanks.

Output for the first command:

```
Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048  16386047   16384000   b  W95 FAT32
/dev/sda2      16386048 485435840  469049793   7  HPFS/NTFS
/dev/sda3     485436105 528522434   43086330   7  HPFS/NTFS
/dev/sda4     528522435 976784129  448261695   f  W95 Ext'd (LBA)
/dev/sda5     528522561 544153672   15631112  83  Linux
/dev/sda6     544153743 579303894   35150152  83  Linux
/dev/sda7     579303963 592605698   13301736  82  Linux swap / Solaris
/dev/sda8     592621568 976771071  384149504   7  HPFS/NTFS
Warning: given size (448248637) exceeds max allowable size (448245630)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048  16386047   16384000   b  W95 FAT32
/dev/sda2      16386048 485435840  469049793   7  HPFS/NTFS
/dev/sda3     485436105 528522434   43086330   7  HPFS/NTFS
/dev/sda4     528522435 976771071  448248637   f  W95 Ext'd (LBA)
/dev/sda5     528522561 544153672   15631112  83  Linux
/dev/sda6     544153743 579303894   35150152  83  Linux
/dev/sda7     579303963 592605698   13301736  82  Linux swap / Solaris
/dev/sda8     592621568 976771071  384149504   7  HPFS/NTFS
Warning: partition 4 extends past end of disk
Successfully wrote the new partition table

Re-reading the partition table ...

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

-> just for the records, sda_sectors_modified.save was saved in the home folder, not on desktop.

After reboot:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6906069f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    16386047     8192000    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sda2        16386048   485435840   234524896+   7  HPFS/NTFS
/dev/sda3       485436105   528522434    21543165    7  HPFS/NTFS
/dev/sda4       528522435   976771071   224124318+   f  W95 Ext'd (LBA)
/dev/sda5       528522561   544153672     7815556   83  Linux
/dev/sda6       544153743   579303894    17575076   83  Linux
/dev/sda7       579303963   592605698     6650868   82  Linux swap / Solaris
/dev/sda8       592621568   976771071   192074752    7  HPFS/NTFS

Disk /dev/sdb: 1031 MB, 1031798784 bytes
32 heads, 62 sectors/track, 1015 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x73696420

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  1919950958  2464388050   272218546+  20  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(356, 97, 46) logical=(967717, 6, 59)
Partition 1 has different physical/logical endings:
     phys=(357, 116, 40) logical=(1242131, 2, 23)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?  1330184202  1869160489   269488144   6b  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 57) logical=(670455, 23, 57)
Partition 2 has different physical/logical endings:
     phys=(269, 101, 57) logical=(942117, 5, 52)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?   538989391  1937352302   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(271668, 1, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(976488, 1, 49)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   *  1394627663  1394648999       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(702937, 10, 36)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(702948, 2, 44)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order



ubuntu@ubuntu:~$ sudo parted /dev/sda print

Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  8390MB  8389MB  primary   fat32        boot 
 2      8390MB  249GB   240GB   primary   ntfs              
 3      249GB   271GB   22.1GB  primary   ntfs              
 4      271GB   500GB   230GB   extended               lba  
 5      271GB   279GB   8003MB  logical   ext3              
 6      279GB   297GB   18.0GB  logical   ext3              
 7      297GB   303GB   6810MB  logical   linux-swap        
 8      303GB   500GB   197GB   logical   ntfs              

Information: Don't forget to update /etc/fstab, if necessary.  

```

Good news, GParted now can see all the partitions. You probably can realize that from the commands you asked above, but it is a good confirmation for a beginner like me anyway. sda2 is shown with a warning (triangle+!) signs, though.

---

### Post by caljohnsmith on 2009-01-26
Great, it looks like your partition table is OK now, so (hopefully) you shouldn't have any more problems with gparted not recognizing the partitions on that drive. Do you still want to try and salvage your sda2 Vista partition? Or what is your goal now?

---

### Post by fluzao on 2009-01-26
Good question. I made a backup of the parts of sda2 that were important before starting everything, but I would like to give one last try to save this partition.

Should I try chkdsk again? Should I use your /r or the /f GParted suggested?

Thanks once again.

---

### Post by caljohnsmith on 2009-01-26
Using "chkdsk /r" is actually better than "chkdsk /f", because the /r option includes the /f option, but /r also has chkdsk deal with bad sectors. You could try it again, but I doubt it will work since it previously refused to work on your sda2 partition. I would suggest using "testdisk" again, because we should check first whether the sda2 partition you previously recovered is the correct one; it may be the Vista partition is fine, but you might have accidentally recovered the wrong partition (wrong start/stop points). So if that sounds OK with you, how about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and if any of them show your Vista root directory.

---

### Post by fluzao on 2009-01-26
After the Deep search, this is was testdisk output:
```

TestDisk 6.6, Data Recovery Utility, February 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63

The harddisk (500 GB / 465 GiB) seems too small! (< 500 GB / 465 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
D HPFS - NTFS          36888 251 36 60801  47 46  384149504 [DATA]

[ Continue ]

NTFS, 196 GB / 183 GiB

```

After Continue:
```

TestDisk 6.6, Data Recovery Utility, February 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
D FAT32                    0  32 33  1019 254 63   16384252 [RECOVERY]
D HPFS - NTFS           1019 251  1 30216 254 63  469050057
D HPFS - NTFS           1020   0  1 30216 254 63  469049805 [VistaOS]
D HPFS - NTFS           1020   0 13 30216 254 63  469049793
D Linux                28629   1  1 29621 254 63   15952482
* HPFS - NTFS          30217   0  1 32898 254 63   43086330
L Linux                32899   2  1 33871 254 63   15631119
D Linux                33872   1  1 36059 254 63   35150157
D Linux Swap           34455   1  1 34697 254 63    3903732
D Linux                34698   1  1 35913 254 63   19534977
D Linux                34953   2  1 37141 254 63   35166159
D Linux Swap           36060   1  1 36887 254 63   13301757
L Linux Swap           59668   1  1 60800 254 63   18201582
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT32, 8388 MB / 8000 MiB

```

checking files/folders with **p**, in order of the list above

D FAT32         yes
D HPFS - NTFS   "Can't open filesystem. Filesystem seems damaged."
D HPFS - NTFS   yes. looks like my old VistaOS partition
D HPFS - NTFS   "Can't open filesystem. Filesystem seems damaged."
D Linux         "No file found, filesystem seems damaged."
* HPFS - NTFS   yes. looks like my Win XP. The one I will use in the end.
L Linux         yes. my Ubuntu /home
D Linux         yes. my Ubuntu /
D Linux Swap    
D Linux         "No file found, filesystem seems damaged."
D Linux         "No file found, filesystem seems damaged."
D Linux Swap    
L Linux Swap

Now I am really concerned with my Data (sda8) partition. The one testdisk is saying cannot be recovered.

I am still on testdisk in the screen after the deep search. Should I do anything?

---

### Post by caljohnsmith on 2009-01-26
While you still have testdisk sitting at the screen with the deep search results, please don't do anything yet with it; instead open a new tab in your terminal, and try the following:
```
sudo umount /mnt && sudo mount -t ntfs-3g -o force /dev/sda8 /mnt && ls -l /mnt
nautilus /mnt &
```
And please post the output. Can you access your DATA partition files with that last nautilus command?

---

### Post by fluzao on 2009-01-26
Interestingly, DATA is already listed on Places and I can see its contents.

Now, following your instructions:
```

ubuntu@ubuntu:~$ sudo umount /mnt && sudo mount -t ntfs-3g -o force /dev/sda8 /mnt && ls -l /mnt
umount: /mnt: not mounted
ubuntu@ubuntu:~$ nautilus /mnt &
[1] 9685
```

Nautilus opens, but /mnt looks empty.

---

### Post by caljohnsmith on 2009-01-26
I see you are using testdisk version 6.6, and the latest version is 6.10; I think it would be good to run that version instead, because it may give a different verdict about your DATA partition. How about downloading the testdisk 6.10 package to your desktop from [here]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2"), and then do:
```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
And then use version 6.10 to do a deep search again, please post the results, and also let me know again which partitions you can see the directory contents of. In the meantime, can you backup your DATA partition to some other drive?

---

### Post by fluzao on 2009-01-26
Did a backup of [DATA].

This new testdisk found many things more. The green lines are the ones with contents. In blue are my comments on the contents.

```

TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
[COLOR="Green"]* FAT32                    0  32 33  1019 250 63   16384000 [RECOVERY][/COLOR] [COLOR="Blue"]Asus Vista Recovery[/COLOR]
D HPFS - NTFS           1019 251  1 30216 250 51  469049793
D HPFS - NTFS           1019 251  1 36888 219  3  576233472
[COLOR="Green"]D HPFS - NTFS           1020   0  1 30216 254 51  469049793 [VistaOS][/COLOR] [COLOR="Blue"]Vista[/COLOR]
D HPFS - NTFS           1020   0 13 30216 254 63  469049793
D Linux                28629   1  1 29621 254 61   15952480
[COLOR="Green"]D HPFS - NTFS          30217   0  1 32898 254 63   43086330[/COLOR] [COLOR="Blue"]XP Install, most important to me[/COLOR]
D HPFS - NTFS          31420 196  9 60801  80 15  471998464
[COLOR="Green"]D Linux                32899   2  1 33871 254 56   15631112[/COLOR] [COLOR="Blue"]/home[/COLOR]
[COLOR="Green"]D Linux                33872   1  1 36059 254 58   35150152[/COLOR] [COLOR="Blue"]/[/COLOR]
D Linux Swap           34455   1  1 34697 254 43    3903712
D Linux                34698   1  1 35913 254 62   19534976
D Linux                34953   2  1 37141   0 58   35150152
D Linux Swap           36060   1  1 36887 254 42   13301736
[COLOR="Green"]D HPFS - NTFS          36888 251 36 60801  47 46  384149504 [DATA][/COLOR] [COLOR="Blue"]My Data - good to see you again![/COLOR]
D Linux                50296 233 50 51289 232 47   15952480
D Linux                50382 149  8 51375 148  5   15952480
D Linux                50491  83 25 51484  82 22   15952480
D Linux                50503  46 40 51496  45 37   15952480
D Linux                50506  94 21 51499  93 18   15952480
D Linux Swap           59668   1  1 60800 254 41   18201560
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, 
     Enter: to continue
SWAP2 version 1, 9319 MB / 8887 MiB

```

I have to go home. Will leave the computer on with the testdisk open. It took forever for a deep search. Will be back tomorrow.

---

### Post by caljohnsmith on 2009-01-26
According the start/stop/size numbers for all the partitions that give you directory listings, those are the exact partitions you all ready have listed in your partition table; thus I don't think we will gain anything if you rewrite your current partition table with testdisk again. But since testdisk can read the Vista partition, before we do anything else to try and fix the Vista partition, how about do a directory listing of the Vista partition again, but use your right/left arrow keys to navigate through the Vista partition folders, and when you find the files you want to recover, select them and press "c" to copy them to the directory where you ran testdisk from. Once you have all your important files from the Vista partition saved safely to some other location, let me know and we can try to recover the Vista partition if you want. Or if you don't care about the Vista partition, you could format that partition and use it for your personal files or something like that.

---

### Post by fluzao on 2009-01-27
Thanks caljohnsmith,

> According the start/stop/size numbers for all the partitions that give you directory listings, those are the exact partitions you all ready have listed in your partition table; thus I don't think we will gain anything if you rewrite your current partition table with testdisk again.

I don't really know how to read those partition tables, but they look slightly different for me. Let me show you one example of my confusion:

```
D HPFS - NTFS           1020   0  1 30216 254 51  469049793 [VistaOS]

/dev/sda2            1020       30217   234524896+   7  HPFS/NTFS

```

Above you find the lines for the Vista partition on both testdisk and fdisk. I don't really know how to read this 30216 254 51 and how this compares with 30217. Is it just a rounding issue?

> 
Once you have all your important files from the Vista partition saved safely to some other location, let me know and we can try to recover the Vista partition if you want. Or if you don't care about the Vista partition, you could format that partition and use it for your personal files or something like that.

This is really wonderful. To be honest, I had already saved what was important in all partitions, but wanted to keep them just in case. Navigating with testdisk I managed to double check I had all the files I wanted.

Last night, after much thought, I decided I can get rid of both the [Recovery] and [VistaOS] partitions, sda1 and sda2 respectively. The only use for the Recovery is if I sell the computer one day, and googleing it is clear that the Recovery DVD will achieve the same results.

I think that makes our lives easier. As far as I understand, and please correct me, we still have to:

1. fix the partitions in this new set up, without the old sda1 and sda2;
2. fix the XP, as I think it is missing the boot related files;
3. fix GRUB and live happy ever after with the two OS.

---

### Post by caljohnsmith on 2009-01-27
> **fluzao said:**
> Thanks caljohnsmith,

I don't really know how to read those partition tables, but they look slightly different for me. Let me show you one example of my confusion:

```
D HPFS - NTFS           [COLOR="Blue"]1020[/COLOR]   0  1 [COLOR="Blue"]30216[/COLOR] 254 51  [COLOR="Blue"]469049793[/COLOR] [VistaOS]

/dev/sda2            1020       30217   234524896+   7  HPFS/NTFS

```

Above you find the lines for the Vista partition on both testdisk and fdisk. I don't really know how to read this 30216 254 51 and how this compares with 30217. Is it just a rounding issue?

The numbers to be interested in are highlighted above in blue; according to testdisk, your Vista partition starts on cylinder 1020, ends on cylinder 30216, and the size in sectors is 469049793. Please note that testdisk conforms to the LBA (Logical Block Addressing) standard, so that means start/stop cylinder values begin counting from "0" and not "1"; on the other hand, fdisk gives the start/stop values of the partitions in cylinders counting from "1". Therefore, comparing the start/stop values of partitions with testdisk with fdisk will usually vary by 1. Also, I've found from experience there can be a small +/-1 cylinder rounding error between the start/stop values that testdisk/fdisk reports. The last number of interest is "469049793", and that's the size of the partition *in sectors*. Note that the size of a partition is calculated as:
```
partition size in sectors = stop sector - start sector + 1 sector
```
The "+1 sector" is to include the sector the partition starts on, because if for example the partition starts at say sector 3 and ends on sector 5, it takes up sectors 3, 4, and 5 (3 sectors total), so size = 5-3+1=3. But the confusing part is fdisk always reports the size *in blocks of 1024 bytes *instead of sectors (which are 512 bytes); thus to compare the testdisk size with the fdisk size, you have to multiply the fdisk size by 2:
```
testdisk size = fdisk size * 2 = 234524896 * 2 = 469049792 sectors
```
So note the sizes are different by only one sector, and that's accounted for because fdisk showed the size as "234524896[COLOR="Red"]+[/COLOR]", so the plus means there was rounding error. 
> **fluzao said:**
> 
This is really wonderful. To be honest, I had already saved what was important in all partitions, but wanted to keep them just in case. Navigating with testdisk I managed to double check I had all the files I wanted.

Last night, after much thought, I decided I can get rid of both the [Recovery] and [VistaOS] partitions, sda1 and sda2 respectively. The only use for the Recovery is if I sell the computer one day, and googleing it is clear that the Recovery DVD will achieve the same results.

I think that makes our lives easier. As far as I understand, and please correct me, we still have to:

1. fix the partitions in this new set up, without the old sda1 and sda2;
2. fix the XP, as I think it is missing the boot related files;
3. fix GRUB and live happy ever after with the two OS.
I think you're right, from your post #5, it looks like the sda3 XP partition is missing its boot files, so they are probably in your Vista partition (don't worry about recovering them though). Before we fix XP, how about deciding what you want to do with sda1 and sda2, because that will affect how we need to configure XP's boot.ini file to boot XP again. You could for instance delete sda1 and sda2 and create one partition with that space for your personal files or something like that. Just please don't be tempted to resize the sda3 XP partition from the beginning to use that space, because moving Windows' beginning sector almost always breaks Windows in a way that is really difficult to fix (and I don't have any experience fixing Windows in a situation like that, I just have heard it can be done). So once you get your partitions figured out and the dust clears, please post:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by fluzao on 2009-01-27
I want to delete sda1 and sda2 and create one partition with that space for storing files.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6906069f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    16386047     8192000    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sda2        16386048   485435840   234524896+   7  HPFS/NTFS
/dev/sda3       485436105   528522434    21543165    7  HPFS/NTFS
/dev/sda4       528522435   976771071   224124318+   f  W95 Ext'd (LBA)
/dev/sda5       528522561   544153672     7815556   83  Linux
/dev/sda6       544153743   579303894    17575076   83  Linux
/dev/sda7       579303963   592605698     6650868   82  Linux swap / Solaris
/dev/sda8       592621568   976771071   192074752    7  HPFS/NTFS

```

Can I use GParted to delete sda1 and sda2 and create a new partition or you think I need specific instructions for that?

Another question: which file system should I use in this new partition? I want it to be accessible from both XP and Ubuntu. I know that XP can access ext3 partitions using FS-Drive and that Ubuntu can now see NTFS partitions. As a practical matter, should I prefer one over the other? XP will probably be the system I use most.

---

### Post by caljohnsmith on 2009-01-27
> **fluzao said:**
> 
Can I use GParted to delete sda1 and sda2 and create a new partition or you think I need specific instructions for that?

Sure, using gparted sounds like a good plan.
> **fluzao said:**
> 
Another question: which file system should I use in this new partition? I want it to be accessible from both XP and Ubuntu. I know that XP can access ext3 partitions using FS-Drive and that Ubuntu can now see NTFS partitions. As a practical matter, should I prefer one over the other? XP will probably be the system I use most.
Since linux has good NTFS support now, I think I would just make the new partition NTFS, especially considering you are planning on spending most of your time in XP. Please post the output of "sudo fdisk -lu" once you have the new partition in place, and we can work from there.

---

### Post by fluzao on 2009-01-27
Ok, on GPArted, now, both sda1 and sda2 have yellow triangles with a ! in it. sda1 also has a locker.

GParted allows me to delete sda2, but it does not allow me to delete sda1. It says:

Unable to find mountpoint

Unable to read the contents of this filesystem! Because of this some operations may be unavailable.

I've tried to remove the boot label from sda1, but it didn't help. I did not apply the changes on GParted.

---

### Post by caljohnsmith on 2009-01-27
Are you running gparted from the Live CD? If not, try doing it from the Live CD just to simplify things. Also, if gparted won't let you delete sda1, can you instead reformat it with gparted? Once it is reformatted, I think gparted should let you delete it. If none of that works, let me know and we can manually delete your sda1 partition at the command line if necessary.

---

### Post by fluzao on 2009-01-27
Done using GParted Live CD. Now back to my Ubuntu 7.10 Live CD (it is the one I have in hand, although the version installed on sda5 is 8.10 64-bits).

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6906069f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   485436104   242718021    7  HPFS/NTFS
/dev/sda3       485436105   528522434    21543165    7  HPFS/NTFS
/dev/sda4       528522435   976771071   224124318+   f  W95 Ext'd (LBA)
/dev/sda5       528522561   544153672     7815556   83  Linux
/dev/sda6       544153743   579303894    17575076   83  Linux
/dev/sda7       579303963   592605698     6650868   82  Linux swap / Solaris
/dev/sda8       592621568   976771071   192074752    7  HPFS/NTFS

```

---

### Post by caljohnsmith on 2009-01-27
Great, looks like it went OK. How about downloading the attached "WinXP_boot_files2.zip" to your Ubuntu desktop, and please post the output of:
```
sudo sfdisk -A3 /dev/sda
sudo mkdir /mnt/sda3 /mnt/sda6
sudo mount /dev/sda6 /mnt/sda6
sudo mount /dev/sda3 /mnt/sda3
cd ~/Desktop
unzip WinXP_boot_files2.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt/sda3
gksudo gedit /mnt/sda6/boot/grub/menu.lst
```
And replace your two Windows entries with:
```
title Windows XP 
root (hd0,2)
chainloader +1
```
Next reboot, choose XP from the Grub menu, and let me know exactly what happens. We can work from there.

---

### Post by fluzao on 2009-01-27
Unfortunately I closed the command window before copying the output, but everything seemed to have worked fine.

The computer booted straight into XP, which seems to be working fine. You are a genius.

How should I proceed to have it booting to the GRUB menu?

---

### Post by caljohnsmith on 2009-01-27
Glad to hear you can boot into XP OK now; to restore your Grub menu, try:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Reboot, let me know if you get the Grub menu, and if so, whether you can boot Ubuntu and XP from the menu. We can work from there if necessary.

---

### Post by fluzao on 2009-01-27
Where exactly should I do it? Should I reset and do it using the Ubuntu Live CD?

---

### Post by caljohnsmith on 2009-01-27
> **fluzao said:**
> Where exactly should I do it? Should I reset and do it using the Ubuntu Live CD?
Yes, just boot your Live CD again and run those commands. :)

---

### Post by fluzao on 2009-01-27
:(

> grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 2: Bad file or directory type


---

### Post by caljohnsmith on 2009-01-27
Grub error 2? It looks like the problem is that you are using a 7.10 Live CD instead of an 8.10 Live CD, because Intrepid formats its ext3 partitions to use a newer standard than what 7.10 used; the Grub that came with 7.10 can't read the newer 8.10 ext3 partitions. We should be able to work around it though, so how about trying instead:
```
sudo mount /dev/sda6 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
exit

```
and please post the output. If all the commands are successful, go ahead and reboot and let me know what happens.

---

### Post by fluzao on 2009-01-27
```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error

ubuntu@ubuntu:~$ grub
Probing devices to guess BIOS drives. This may take a long time.

grub> root (hd0,5)

Error 21: Selected disk does not exist

```

---

### Post by caljohnsmith on 2009-01-27
Is your Ubuntu install 32-bit or 64-bit, and is the 7.10 Live CD that you are using the other architecture? If the architectures are different, you'll need to get a Live CD with the same architecture as your Ubuntu install, or if you use an 8.10 Live CD, it can be any architecture.

---

### Post by fluzao on 2009-01-27
> **caljohnsmith said:**
> Is your Ubuntu install 32-bit or 64-bit, and is the 7.10 Live CD that you are using the other architecture? If the architectures are different, you'll need to get a Live CD with the same architecture as your Ubuntu install, or if you use an 8.10 Live CD, it can be any architecture.

My Ubuntu is 8.10 64-bits. My LiveCD is 7.10 32-bits.

Will download the 8.10 Live CD now and get back to you.

---

### Post by fluzao on 2009-01-27
It is all working like a charm! Grub menu loading on boot. I am able to boot both on XP and Ubuntu.

Thank you very much, caljohnsmith.

Are there any extra tests do you thing I should do?

Finally, how do I put your deserved [Solved] in the thread? Just edit it?

---

### Post by caljohnsmith on 2009-01-27
> **fluzao said:**
> 
Are there any extra tests do you thing I should do?

Finally, how do I put your deserved [Solved] in the thread? Just edit it?
I think you should be all set, so no need for any more tests unless you run into more problems. Also, the last I heard the forum admins unfortunately had to disable the "marked as solved" feature for threads for the time being, so there's no way to do that for now. Anyway, cheers and have fun with XP and Ubuntu. :)

---


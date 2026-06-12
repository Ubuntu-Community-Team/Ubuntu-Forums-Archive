---
title: "Odd change after using gparted"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by dmj99 on 2009-02-05
Long story short . . . 

I have a triple boot system (XP, Vista, and Ubuntu).  There was some free space on my hard drive that I wanted to get rid of so I used the live gparted CD to move and resize my partitions.  Ubuntu was always on hd0,2 (the third partition on my single hard drive).

After using gparted, I had to repair my Vista installation (which I sort of expected I'd have to do--no big deal).  But I was also having trouble booting up Linux.  The funny thing is, when I booted from the live CD and entered in grub  "find /boot/grub/stage1", I got the result (hd1,2).  It had always been on hd0,2 before.  No other hard drive in my system except a USB stick.   

Anyone understand why using gparted would change my drive designations in this way?

---

### Post by OffAxis on 2009-02-05
the USB stick can register as a boot device.
What's your boot sequence like?

What happens when you take the USB stick out?

---

### Post by caljohnsmith on 2009-02-05
I think it would help to get more info about your setup and the present state of your partitions, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by dmj99 on 2009-02-05
Thank you both for your interest.  I am able to boot into all 3 operating systems.  Things seem to have worked themselves out somehow.  When I ask grub to find stage1, it finds it on (hd0,2 and hd1,0).  The hd1,0 is my USB boot stick. I used the Vista bootloader. Here is the results text (sorry but the # code doesn't seem to be working: 

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file 
                       /NST/nst_grub-922D93DF657C82144B60FC6F5C38739E.mbr is 
                       trying to chain load sector #404436375 on boot drive 
                       #1 BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #204812685 on boot drive #1
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 449869207 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Linux Mint 6 Felicia
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa52aa52a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   178,514,279   178,514,217   7 HPFS/NTFS
/dev/sda2         178,514,280   404,436,374   225,922,095   7 HPFS/NTFS
/dev/sda3         404,436,375   487,347,839    82,911,465  83 Linux
/dev/sda4         487,347,840   488,392,064     1,044,225  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 4051 MB, 4051697664 bytes
255 heads, 63 sectors/track, 492 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1f932310

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,903,979     7,903,917   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8684E6A784E698C7" LABEL="SATA_XP" TYPE="ntfs" 
/dev/sda2: UUID="2A60362F6036025D" LABEL="SATA_VISTA" TYPE="ntfs" 
/dev/sda3: UUID="8525b93c-d0b6-4362-ae5e-0923ccece441" TYPE="ext3" 
/dev/sda4: UUID="030ef0eb-503e-4a40-aac2-534961b2f855" TYPE="swap" 
/dev/sdb1: LABEL="FLASHDRIVE" UUID="4972-6495" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/don/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=don)
/dev/sdb1 on /media/FLASHDRIVE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
##      altoptions=(single-user) single
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

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,2)
kernel		/boot/last-good-boot/vmlinuz root=/dev/sda3 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=8525b93c-d0b6-4362-ae5e-0923ccece441 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=962c1e06-d580-430f-b8a0-c1b2dc9052a7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 216.4GB: boot/grub/menu.lst
 230.3GB: boot/grub/stage2
 232.0GB: boot/initrd.img-2.6.27-7-generic
 230.3GB: boot/vmlinuz-2.6.27-7-generic
 232.0GB: initrd.img
 230.3GB: vmlinuz

=========================== sdb1/boot/grub/menu.lst: ===========================

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
color cyan/blue white/blue

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
# kopt=root=UUID=335aff53-d589-4242-96f4-d0b5182667bc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=335aff53-d589-4242-96f4-d0b5182667bc

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

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd1,2)
kernel		/boot/last-good-boot/vmlinuz root=/dev/sda3 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1



=================== sdb1: Location of files loaded by Grub: ===================


   2.6GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2

The only thing I find a little funny is that I had to change the root command on the USB stick to (hd1,2) when it used to be (hd0,2)

---


---
title: "Grub"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by Arthur Millar on 2009-03-01
i have 2 sata drives
one is ubuntu the other is for vista so i can play games
i installed ubuntu first so i dont have vista in the grub menu 
how do i put it on the grub menu 
i have searched the net but most of the documentation is for partitions

---

### Post by ubername on 2009-03-01
> **Arthur Millar said:**
> i have 2 sata drives
one is ubuntu the other is for vista so i can play games
i installed ubuntu first so i dont have vista in the grub menu 
how do i put it on the grub menu 
i have searched the net but most of the documentation is for partitions

add something like

title		Microsoft Windows Vista
root		(hd1,0)
chainloader	+1

to your grub menu, (where hd1 is the number of your Vista drive and 0 is the partition on which Vista is loaded.

gksu gedit /boot/grub/menu.lst

---

### Post by Sef on 2009-03-01
Check out [Super GRUB Disk]("http://stmaarten.globat.com/%7Esupergrubdisk.org/").  It is easy to use.

---

### Post by Arthur Millar on 2009-03-01
> **ubername said:**
> add something like

title		Microsoft Windows Vista
root		(hd1,0)
chainloader	+1

to your grub menu, (where hd1 is the number of your Vista drive and 0 is the partition on which Vista is loaded.

gksu gedit /boot/grub/menu.lst

um this just hosed grub i booted from live cd and fixed 
tried a (sd1,0) as my drives are SATA  
this fixed grub and windows was on the list but it just spit out an error\
"error parsing number"

---

### Post by Arthur Millar on 2009-03-01
> **Sef said:**
> Check out [Super GRUB Disk]("http://stmaarten.globat.com/%7Esupergrubdisk.org/").  It is easy to use.

all the download links are dead 
can i find it in synaptic?

---

### Post by caljohnsmith on 2009-03-01
In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by presence1960 on 2009-03-01
> **Arthur Millar said:**
> i have 2 sata drives
one is ubuntu the other is for vista so i can play games
i installed ubuntu first so i dont have vista in the grub menu 
how do i put it on the grub menu 
i have searched the net but most of the documentation is for partitions

add this to the end of your menu.lst file

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

of course edit the dev location & the windows version name to your version. Also change the root  (hdx,y) to your drive and partition for windows. Since you have the OS's installed on separate physical drives you need the map stuff in there.

---

### Post by Arthur Millar on 2009-03-04
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
69 heads, 2 sectors/track, 1132246 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0fe30fe2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              2   156,249,809   156,249,808   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc9eec9ee

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   149,790,059   149,789,997  83 Linux
/dev/sdb2         149,790,060   156,248,189     6,458,130   5 Extended
/dev/sdb5         149,790,123   156,248,189     6,458,067  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8c2cb275

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   312,576,704   312,576,642   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="CC6072DE6072CEA8" TYPE="ntfs" 
/dev/sdb1: UUID="b54ae045-33a1-458d-9122-798dc26d6b02" TYPE="ext3" 
/dev/sdb5: UUID="51b56e7d-cfb8-45fa-a2f4-9fa7bfbfd8f5" TYPE="swap" 
/dev/sdc1: LABEL="160Storage" UUID="49A1-C7D2" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/arthur/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=arthur)


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
timeout		3

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
# kopt=root=UUID=b54ae045-33a1-458d-9122-798dc26d6b02 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b54ae045-33a1-458d-9122-798dc26d6b02

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		b54ae045-33a1-458d-9122-798dc26d6b02
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b54ae045-33a1-458d-9122-798dc26d6b02 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		b54ae045-33a1-458d-9122-798dc26d6b02
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b54ae045-33a1-458d-9122-798dc26d6b02 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b54ae045-33a1-458d-9122-798dc26d6b02
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b54ae045-33a1-458d-9122-798dc26d6b02 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b54ae045-33a1-458d-9122-798dc26d6b02
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b54ae045-33a1-458d-9122-798dc26d6b02 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b54ae045-33a1-458d-9122-798dc26d6b02
kernel		/boot/memtest86+.bin

title 		Microsoft Windows Vista
root 		(sd2,0)
chainloader +1

quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b54ae045-33a1-458d-9122-798dc26d6b02 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=51b56e7d-cfb8-45fa-a2f4-9fa7bfbfd8f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   9.8GB: boot/grub/menu.lst
   9.8GB: boot/grub/stage2
   9.9GB: boot/initrd.img-2.6.27-11-generic
   9.8GB: boot/initrd.img-2.6.27-7-generic
   9.9GB: boot/vmlinuz-2.6.27-11-generic
   9.9GB: boot/vmlinuz-2.6.27-7-generic
   9.9GB: initrd.img
   9.8GB: initrd.img.old
   9.9GB: vmlinuz
   9.9GB: vmlinuz.old
```
thanks caljohnsmith

---

### Post by Arthur Millar on 2009-03-06
bump

---

### Post by steve-shinn on 2009-03-06
Change
title 		Microsoft Windows Vista
root 		(sd2,0)
chainloader +1

To
title 		Microsoft Windows Vista
root 		(sd1,0)
chainloader +1

---

### Post by Arthur Millar on 2009-03-06
> **steve-shinn said:**
> Change
title 		Microsoft Windows Vista
root 		(sd2,0)
chainloader +1

To
title 		Microsoft Windows Vista
root 		(sd1,0)
chainloader +1

To
title 		Microsoft Windows Vista
root 		(sd1,0)
chainloader +1

sd0, sd1, sd2, non of these are working 
error parsing numbers


if set to hd0, hd1, hd2 hoses grub

---

### Post by Arthur Millar on 2009-03-07
i have tried sd0, sd1, and sd2
all i get is
error parsing numbers 
can someone please help me with this 
linux and windows are on separate drives
help

---


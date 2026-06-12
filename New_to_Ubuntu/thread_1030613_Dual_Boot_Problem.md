---
title: "Dual Boot Problem"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Bossfly on 2009-01-04
Hi.  Absolute nub here. I was running XP pro on two HDs and decided to replace one installation of XP Pro on my older HD with a Ubuntu trial.  The repartitioning and installation went relatively smoothly, but now I can't get the newer HD with XP Pro to boot.

I read a thread about modifying the grub menu.lst, and attempted to make the necessary modifications.  It's obvious that I'm not up to the task.  I can boot Ubuntu, but not Windows.  Could someone take a look and give me a few pointers?  Thanks in advance.  Here's where everything stands (Bios is set to boot from old HD first)

sudo fdisk -lu :

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b082ad0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   122881184    61440561    7  HPFS/NTFS
/dev/sda2       122881185   976768064   426943440    f  W95 Ext'd (LBA)
/dev/sda5       122881248   976768064   426943408+   7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders, total 117266688 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2a362a35

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   112390739    56195338+  83  Linux
/dev/sdb2       112390740   117258434     2433847+   5  Extended
/dev/sdb5       112390803   117258434     2433816   82  Linux swap / Solaris

Disk /dev/sdc: 2024 MB, 2024275968 bytes
64 heads, 32 sectors/track, 1930 cylinders, total 3953664 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32     3953151     1976560    6  FAT16

cat /boot/grub/menu.lst :

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
# kopt=root=UUID=5d792ba7-e974-4e1e-a2ed-8d78c7725cb4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5d792ba7-e974-4e1e-a2ed-8d78c7725cb4

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
# howmany=2

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
uuid		5d792ba7-e974-4e1e-a2ed-8d78c7725cb4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5d792ba7-e974-4e1e-a2ed-8d78c7725cb4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		5d792ba7-e974-4e1e-a2ed-8d78c7725cb4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5d792ba7-e974-4e1e-a2ed-8d78c7725cb4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5d792ba7-e974-4e1e-a2ed-8d78c7725cb4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5d792ba7-e974-4e1e-a2ed-8d78c7725cb4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5d792ba7-e974-4e1e-a2ed-8d78c7725cb4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5d792ba7-e974-4e1e-a2ed-8d78c7725cb4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		5d792ba7-e974-4e1e-a2ed-8d78c7725cb4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP Pro SP3
root		(hd1,0)

---

### Post by kestrel1 on 2009-01-04
at the end of your menu.lst file chang it so it would look like this:
title Windows XP Pro SP3
root (hd1,0)
savedefault
makeactive
chainloader +1

Use ```
gksudo gedit /boot/grub/menu.lst
```
To edit the file

---

### Post by Elfy on 2009-01-04
Edit - kestrel1 - win appears to be on sda not sdb

Try this - change the windows stanza to

> root (hd0,0)
makeactive
chainloader +1

To backup and open file for editing

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkup
sudo gedit /boot/grub/menu.lst
```

You will need your normal password for both commands - it won't appear in the terminal, that is normal.

---

### Post by kestrel1 on 2009-01-04
Yes sorry missed that one (hd0.0)

---

### Post by Bossfly on 2009-01-04
Thanks for the pointers.  I'm getting error 13 when I try to load XP, which I will have to look up after heading out for a bit.

I'll post when (if) I get this working.

---


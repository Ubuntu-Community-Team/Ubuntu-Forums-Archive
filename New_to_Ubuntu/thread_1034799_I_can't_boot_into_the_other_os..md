---
title: "I can't boot into the other os."
date: 2009-01-09
forum: New to Ubuntu
---

### Post by codpawn on 2009-01-09
I have 2 hard drives and first is 500gb which is connected to master and another is connected to slave and that is of 80gb and 1st partition  has installed Win XP which is of 30gbs, 2nd is swap and 3rd has ubuntu installed on it.
To prevent my Computer used by my room-mates I installed the  Ubuntu 8.10 on the 4gb Pen Drive, My aim was that the PC can be booted only when pen drive is connected. 

Now the problem starts-

1) I can boot only in pen drives Ubuntu when its connected when I try to boot in other os it shows-
```
 Error 12 No such partition 

Press any key to continue_ 
```

There are three os entries 
1 Ubuntu (on pen drive)
2 Win XP (on HD)
3 Ubuntu (on HD)

2) When Pen Drive is not connected to the PC the windows automatically boots up (Grub is not installed on HDs Ubuntu)

Following is my partition table 
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x005495b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917        4165     2000092+  82  Linux swap / Solaris
/dev/sda3            4166        5410    10000462+  83  Linux
/dev/sda4            5411       60801   444928207+   f  W95 Ext'd (LBA)
/dev/sda5            5411       10443    40427541    7  HPFS/NTFS
/dev/sda6           10444       23497   104856223+   7  HPFS/NTFS
/dev/sda7           23498       60801   299644348+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bf3565b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdc: 4016 MB, 4016046080 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008e8f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         488     3919828+  83  Linux
```

And This is my menu.lst
```
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
# kopt=root=UUID=9b8e4c5a-dc38-4c38-af6b-4c664da8d9e2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9b8e4c5a-dc38-4c38-af6b-4c664da8d9e2

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9b8e4c5a-dc38-4c38-af6b-4c664da8d9e2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9b8e4c5a-dc38-4c38-af6b-4c664da8d9e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9b8e4c5a-dc38-4c38-af6b-4c664da8d9e2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9b8e4c5a-dc38-4c38-af6b-4c664da8d9e2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9b8e4c5a-dc38-4c38-af6b-4c664da8d9e2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8420169a-bb66-46e1-b9d5-82e193170e9a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8420169a-bb66-46e1-b9d5-82e193170e9a ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.10, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

Please help me to fix this problem.

---

### Post by computermacgyver on 2009-01-09
Please help me understand exactly what is happening:
1) When the pen drive is *not* connected
a) Windows boots fine
b) the harddrive Ubuntu works???

2) When the pen drive is connected
a) the pen drive Ubuntu boots?

Which of these (1a, 1b, 2a) does not work?

---

### Post by codpawn on 2009-01-09
1a)Yes Windows boots fine when pen drive is not connected.
1b) Because of the re-installation of the XP I can't boot into the HDs Ubuntu 

2a)When Pen drive is connected pen drives Ubuntu boots up fine and when I click on the Win Xp entry it says 
```
 Error 12 No such partition 

Press any key to continue_
```

---

### Post by computermacgyver on 2009-01-09
All right. In regards to 2a (booting windows from the pen drive): I think the system sees the pen drive as hd0 in grub and the harddrive becomes hd1. Thus,  boot ubuntu from the pen drive and try to change the menu.lst on your pen drive from:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
chainloader	+1

```
to
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		([COLOR="Red"]hd1[/COLOR],0)
savedefault
chainloader	+1

```

Then execute:
```
grup-install /dev/(your pen drive device)
```
To find the pen drive device you may run mount -l and use the device for "/".

---

### Post by computermacgyver on 2009-01-09
To fix problem (1b) booting into the harddrive's ubuntu, we will have to have install grub on /dev/sda . I would have the Windows recovery cd handy just in case you want to revert to the windows boot loader (which I believe can be done with fdisk /mbr).

It looks like the menu.lst file you posted is already correct for your harddrive. When that harddrive boots it will be the first harddrive (hd0). So, (hd0,0) should be the windows partition. To install grub, grub-install as above, but use the mount point of your physical harddrive. (Make sure that you keep the current menu.lst file as posted in this case; you may have to change it back from the above change; sorry.)

To not complicate matters lets work first on having windows boot when the pen drive is attached and make sure that works before working on this second issue.

---


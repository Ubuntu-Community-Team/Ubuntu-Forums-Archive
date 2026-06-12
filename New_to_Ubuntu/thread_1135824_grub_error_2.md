---
title: "grub error 2"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by souraklis on 2009-04-24
Ok i dont have exerience in this operating system i ve installed ubuntu before two months and today i try to install the new kernel 8.10. During the installation i had problem with the partitions. I tried to manage the partitions of hard disk in which i ve installed before two months the erlder distribution. I delete the partitions i ve made and then i try to restart and boot to windows. Then i receiving the following Grub error:

"GRUB Loading stage1.5.
Grub loading, please wait...
Error 2"

and it s impossible to open the cd rom as i cant boot anywhere.
is there any solution from this i cant open cd rom,how can i do something in my c:P? :lolflag:

---

### Post by souraklis on 2009-04-24
anyone...

---

### Post by steinaro on 2009-04-24
From what I see when I google "grub error 2", error two means selected disk doesn't exist.

I have had to fix grub a few times when windows XP made updates and tried to take things over. Perhaps you have the wrong partition selected in grub. You may have to edit the file /boot/grub/menu.lst

---

### Post by souraklis on 2009-04-25
I achieve finally to open cd rom and boot from cd. And i installed the ubuntu version without problems. When i tried to boot to windows i receiving this :


"GRUB Loading stage1.5.
Grub loading, please wait...
Error 17"

I can boot normally in ubuntu.
Any help would be appreciable...

:guitar:

---

### Post by o.besner on 2009-04-25
The two commands you are looking for is ```
fixboot
``` and ```
fixmbr
``` if your bootloader has been altered. However, I'm not sure I understand you question.Both can be accessed from your windows xp cd recovery console.

But first you gonna do this first :

```
sudo gedit /boot/grub/menu.lst
```

and check out if your entry for windows is correct. Is it pointing to the good partition?

Remember this: Windows likes to be on top. That means, it likes to be the first OS installed on a system and likes to be the first partition of the disk (ex: sda1). If that's not the case, you might wanna fix that first.

---

### Post by souraklis on 2009-04-26
When i try to boot in windows i receiving this:

Error 13 invalid or unsupported executable format

I can boot normally in ubuntu. When i boot in ubuntu it shows me ubuntu (hd0,0) but in the /boot/grub/menu.lst it shows that the windows has root (hd0,0) and the linux (hd0,1).

---

### Post by souraklis on 2009-04-26
any solution?

---

### Post by Didius Falco on 2009-04-26
From a Ubuntu shell (Terminal) type ```
sudo fdisk -l
``` and post the output here.

---

### Post by Bodsda on 2009-04-26
Also, could you paste the output of the following command please

```

cat /boot/grub/menu.lst

```

---

### Post by souraklis on 2009-04-26
This when i type sudo fdisk -l


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f7e1f7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5031    40411476    7  HPFS/NTFS
/dev/sda2            5032       14593    76806765    f  W95 Ext'd (LBA)
/dev/sda5            5032       14593    76806733+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe44fe44f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37d9152c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

---

### Post by souraklis on 2009-04-26
cat /boot/grub/menu.lst

```
souraklis@souraklis-desktop:~$ cat /boot/grub/menu.lst
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
#title              Windows XP
#root               (hd1,0)
#savedefault
#makeactive
#map                (hd0) (hd1)
#map                (hd1) (hd0)
#chainloader        +1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#
ska p
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
# kopt=root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f6e2bb32-83bc-40ef-9c37-760533336c02

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
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1
souraklis@souraklis-desktop:~$ cat /boot/grub/menu.lst
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
#title              Windows XP
#root               (hd1,0)
#savedefault
#makeactive
#map                (hd0) (hd1)
#map                (hd1) (hd0)
#chainloader        +1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#
ska p
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
# kopt=root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f6e2bb32-83bc-40ef-9c37-760533336c02

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
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

```

---

### Post by Miljet on 2009-04-26
It looks like you are missing the "makeactive" command. It should go between the "savedefault" and "chainloader +1".

Like this:

```
title		Windows XP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

You can modify the menu.lst file by typing this in a terminal:

```
gksudo gedit /boot/grub/menu.lst 
```

---

### Post by Didius Falco on 2009-04-26
While your editing the menu.lst file, change the "root" to "rootnoverify" too:

This 

```
title                Microsoft Windows XP Professional
root                (hd0,0)
savedefault
chainloader    +1
```

should look like this:

```
title                Microsoft Windows XP Professional
rootnoverify                (hd0,0)
savedefault
makeactive
chainloader    +1

```

then reboot, load windows, reboot again and load Ubuntu, just to test them both out.

---

### Post by souraklis on 2009-04-27
OK this is what i ve changed in boot/grub/menu.lst

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
#title          Microsoft Windows XP Professional
#rootnoverify        (hd0,0)
#savedefault
#makeactive
#map                (hd0) (hd1)
#map                (hd1) (hd0)
#chainloader        +1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#
ska p
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
# kopt=root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f6e2bb32-83bc-40ef-9c37-760533336c02

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
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f6e2bb32-83bc-40ef-9c37-760533336c02
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

title		Microsoft Windows XP Professional
rootnoverify 	(hd0,0)
savedefault
makeactive
chainloader    +1

```

but i ve the same problem error 13 again.

---

### Post by souraklis on 2009-04-27
# is for comments????????

---

### Post by Didius Falco on 2009-04-27
Okay, it looks like you've installed Ubuntu on a second hard drive. Boot up with the Ubuntu Live cd, open a terminal window and type ```
grub
```This will give you a grub prompt. Type ```
find /boot/grub/stage1
```This will show you which hard drive(s) and partition(s) have the grub bootloader, in a format something like this:

(hd0,1)

There may be more than one of them. I'm betting in your case it will show something like 

(hd1,*x*)

with* x* being the partition it is on. You,ll use the result returned here in the next command. Type ```
 root (hdx,y)
``` with the correct numbers in place of the x,y part.

then type ```
setup (hd0)
``` This will give you a few lines of messages telling you that it found the 1.5 and 2 stages of grub.

Then type ```
quit 
``` and reboot without the Live CD. Try out both the Ubuntu and Windows boots and post the results, please.

---

### Post by souraklis on 2009-04-27
i ve installed ubuntu in different hard disk from windows . I had had two kernels and i decided two erased them and installed the new one 8.10. I made
a silly mistake I erased the partition from the hard disk where i installed ubuntu. The next event was that i finally installed 8.10 but when i tried to boot to windows i receiving this error 13.

Now I try wrote in the terminal the word grub and afterthat i type this find /boot/grub/stage1 and i receive this Error 15: File not found
:Pthank you for your help and sorry for my english:)

---

### Post by Didius Falco on 2009-04-27
Are you getting that error message before the Grub menu even shows up?

Boot into the Live CD again. Open a Terminal and type ```
blkid
``` and post the output here. I want to check that your UUID numbers are correct.

Do a ```
fdisk -l
``` again and post that as well. I just want to have a fresh look at all of it together.

I'm sorry it's taking so long to get it fixed, but I'm willing to keep plugging away at it if you are.

---

### Post by souraklis on 2009-04-28
i get the message after the grub menu when i try to boot to windows. i tried your commands and i received for blkid:

```
/dev/sda1: UUID="CA9C64A09C6488B1" TYPE="ntfs" 
/dev/sda5: UUID="12E6FBCC926ADC41" LABEL="Jacob" TYPE="ntfs" 
/dev/sdb1: UUID="f6e2bb32-83bc-40ef-9c37-760533336c02" TYPE="ext3" 
/dev/sdb5: UUID="af3eaa6f-8fde-426d-b7fd-129278ad1ae5" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc: SEC_TYPE="msdos" LABEL="KINGSTON" UUID="60BE-0627" TYPE="vfat" 

```
and for fdisk -1 
```
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

```

---

### Post by Herman on 2009-04-28
My guess is that the Windows XP boot sector has something wrong with it.
 
The FIXBOOT command from a Windows  [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") would normally be the recommended way to repair a Windows bootsector.

If you don't have a Windows XP 'Installation' CD, you can't access Windows Recovery Console.

[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") is a program you can install in Ubuntu, and TestDisk can easily fix the NTFS boot sector or restore the boot sector the backup. TestDisk has their own page with illustrations, here is a link, [TestDisk Step by Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step").

If you want to install TestDisk in Ubuntu, use a command like this,
                          ```
sudo apt-get install testdisk
                             
```
To run TestDisk, you start it with the testdisk command,
                          ```
sudo testdisk
```
Regards, Herman :)

---

### Post by souraklis on 2009-04-28
Do you know which one of this is propert for 8.10?
   
    * linux.png Linux, kernel 2.6.x i386/x86_64, tar.bz2
    * linux.png Linux, kernel 2.4.x i386/x86_64, tar.bz2
    * rpm.png Linux i386 RPM
    * rpm.png Linux SRPM
   
Thanks...

---

### Post by Didius Falco on 2009-04-28
You should hold off on putting a new kernel in until you get everything working.

Herman is one of the best sources of information around when it comes to Grub, dual-booting, fixing the MBR, etc.

I asked him to come and take a look at this thread because what I do know about fixing these kind of problems he taught me via his website.  Practically everything I know about these kind of problems, I learned from his website - but I don't yet know everything he knows.

Truly, follow his advice, and get your PC working properly again before you start trying to compile kernels.

If fixing your MBR gets you back into windows, reinstalling Grub to it is easy, and that should get you up and running again.

---

### Post by Herman on 2009-04-28
If I understand everything correctly, Ubuntu is booting okay but there are various error messages when trying to boot Windows.

GRUB doesn't actually boot Windows, but it boots the Windows boot loader, NTLDR instead using code in the Windows partition boot sector. Then Windows boot loader should boot Windows. That process is called 'chainloading'.

The 'boot sector' is not the same thing as a MBR. 
All hard disks have a MBR, it is the first sector of a hard disk and it is written when the disc is formatted.
The MBR contains the partition table, and some room is there for some 'boot code', or the 'IPL' of a boot loader. Basically that tells what place on the hard disk to look for the boot loader.
Your MBR is fine, it is pointing to GRUB in your Ubuntu partition.

From GRUB, your Ubuntu is booting okay, but it is only when you use GRUB to point to your Windows boot sector that an error occurs. 
So, I think there might be something wrong with your Windows boot sector, (the first sector of the Windows partition).

GRUB Error 13 when trying to boot Windows has always been caused by a bad Windows boot sector every time I know of. 

The other problem that seems possible would be if you are trying to boot the wrong partition. Your fdisk output shows that the first hard drive has a number 1 partition formatted with NTFS and it has a boot flag. Most of the time that would be the most likely location for a Windows operating system.
You also have another partition in your first hard disc that could be Windows, in partition 5, which is a logical partition. It has a label 'Jacob', so I'm guessing it's a data partition.
There was another NTFS partition in your third hard disc, 250 GB according to your earlier fdisk output, but according to your more recent blkid output, you only have a USB flash memory stick and no third hard disk anymore, I don't know what's going on there.

It's also possible you could have some kind of a hardware problem since you have mentioned so many different error messages all in one thread. It could be there is a hardware problem causing your computer to behave in an erratic manner. I'm not sure.

Regards, Herman :)

---

### Post by Didius Falco on 2009-04-28
Thanks for jumping in, Herman. I'm starting to take this one personally. #-o

---

### Post by souraklis on 2009-04-28
Firstly thank you for time wasting to my problem.
Secondly I ve to say to you that i ve got 3 hard disk. The first one is an external hard disk that s why you get confused in fdisk output(sometimes its off) one disk where i installed ubuntu (80gb) and one disk  with to partition one Jacob with data and the second one partition with windows. In the beggining before i installed ubuntu i ve received two messages(before dual boot menu) when i tried to boot to windows or to ubuntu(depends of the priority of hard disk in bios the first was error 17 and error 2). But when i installed ubuntu i finally got to dual boot menu and when i tried to enter windows i ve got this **error 13**.

---

### Post by Didius Falco on 2009-04-29
> **souraklis said:**
> Firstly thank you for time wasting to my problem.
Secondly I ve to say to you that i ve got 3 hard disk. The first one is an external hard disk that s why you get confused in fdisk output(sometimes its off) one disk where i installed ubuntu (80gb) and one disk  with to partition one Jacob with data and the second one partition with windows. In the beggining before i installed ubuntu i ve received two messages(before dual boot menu) when i tried to boot to windows or to ubuntu(depends of the priority of hard disk in bios the first was error 17 and error 2). But when i installed ubuntu i finally got to dual boot menu and when i tried to enter windows i ve got this **error 13**.

Okay, that explains some things. In order to fix this, you have to have the pc working in the same way consistently. Now, please post the answers to these questions.

1. What is on the external drive?

I *really* hope it isn't Windows...If it is just a data storage drive, unplug it and leave it unplugged. If it has Ubuntu or Windows on it, let us know, and leave it plugged in until this gets fixed.

2. Why are you changing the boot order in the Bios?

This could be causing a lot of the problems. Set your Bios to boot the hard drive that contains Windows first, and leave it that way until this gets resolved.

3. Did you install the TestDisk program Herman recommended?

If you haven't, do so, please.

4. Do you have a Windows bootable install cd?

---

### Post by souraklis on 2009-04-30
I tried The FIXBOOT command from a Windows recovery console and again nothing(error 11113 again). This will drive me crazy i ve started thinking of FORMAT. Is there any else that I can try with recovery console?

---

### Post by Didius Falco on 2009-04-30
Answer the questions and set up your pc as stated in my last post. Pay particular attention to the BIOS part.

Once you have a stable setup, things will become clearer. I think a big part of the problem is that you are getting advice on how to fix the problem, but you have changed the configuration of your pc in the meantime, so the advice is no longer valid.

---

### Post by souraklis on 2009-04-30
1)Data
2)It s something i did as i wanted to try things (i thought in the beggining that this was the fault).
3)i installed it but i failed because i got confused.(I dont know what exactly i ve to do after  installation)
4)yes i ve got i told you before

---

### Post by Didius Falco on 2009-04-30
Okay, now that you have a stable setup, are you seeing the Grub menu?

Can you boot into Ubuntu? If not, what error(s) are you getting?

Can you boot into windows? If not, what errors are you getting?

If you have the time right now, I'll stay online and see if we can get this taken care of now.

---

### Post by Didius Falco on 2009-04-30
One of the Ubuntu staff posted a link to this little script, and it's going to make things much easier to figure out.

Go to 

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

and download the Boot Info Script that is linked there to your desktop. Then open a Terminal window and type

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a file called **RESULTS.txt** on your desktop. Open that up and copy all the the contents. Paste the contents to a message here, then select what you just pasted and click the** #** button to mark it as code. That'll make it easier to read.

That script will tell us quite a bit that will help get you up and running properly again.

---

### Post by souraklis on 2009-05-02
Ok i found something new. I tried to formatted system. In partition where  i had windows ("C"). I deleted C and i tried to installed there but it shown me this: 1)partition1 [(New(Rav))]
               2)oartition2 (Jacob) [NTFS]

I tried afterthat to install in partition 1 but it said to me something like it wasn t proper kind of partition to install windows(try to make a new one).

---

### Post by Didius Falco on 2009-05-02
If it said the partition was RAW, that means you didn't format it, you just created it. To install Windows, go back into your partitioner and format that partition to NTFS.

---

### Post by souraklis on 2009-05-02
Ok i feel a very silly guy now. The situation has changed. I used installation cd for windows and in the recovery console i entered this command "fixmbr" and afterthat i changed in bios hard disk priority with c(in whick i ve got windows) in first place and the other disk(where i ve got ubuntu) in the other place. I finally succed to entered to win. But now i cant boot to ubuntu(redicullous situation). When i ve got the other priority of disks i ve received this message fot windows(after dual boot menu) MTLDL missing.Either two cases i cant entered ubuntu.:(

---

### Post by Didius Falco on 2009-05-02
Souraklis,

No one can help you unless you are willing to be helped.

A few posts ago, I asked you to set your BIOS to use the hard drive Windows is on first, your second permanent drive 2nd, and either set your removable drive 3rd or just leave it unattached until this is straightened out.

Do that, boot with your Live CD, download that small script (57k - it'll take you longer to read this than to download and use it) I linked above, run it and post the output.

If you do that, the odds are very good that I or someone else can get you up and running in short order.

If you keep changing things around, and ignoring the advice you get here, no here will be able, or for that matter even try, to help you.

If you want to try and work your own way through it, that's fine. That's how I fix (or mess up so badly that I end up wiping everything and starting over) most things myself.

---

### Post by souraklis on 2009-05-04
OK its true that for myself i couldn t achieve something.(and sorry for being responding after 1 day late). The results is that:

```
============================= Boot Info Summary: ==============================

 => Wind_______________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Fat16
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    FilDrive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe44fe44f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             48     7,831,551     7,831,504   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37d9152c

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A4CC0586CC055448" TYPE="ntfs" 
/dev/sda5: UUID="12E6FBCC926ADC41" LABEL="Jacob" TYPE="ntfs" 
/dev/sdb1: UUID="f6e2bb32-83bc-40ef-9c37-760533336c02" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="af3eaa6f-8fde-426d-b7fd-129278ad1ae5" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: LABEL="STATHOULIS" UUID="5802-AFF7" TYPE="vfat" 
/dev/sdd1: UUID="DE101934101914DD" LABEL="12" TYPE="ntfs" 

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
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/STATHOULIS type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdd1 on /media/12 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetectows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Fat16
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

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
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1f7e1f7d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,823,014    80,822,952   7 HPFS/NTFS
/dev/sda2          80,823,015   234,436,544   153,613,530   f W95 Ext d (LBA)
/dev/sda5          80,823,078   234,436,544   153,613,467   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe44fe44f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             48     7,831,551     7,831,504   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37d9152c

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A4CC0586CC055448" TYPE="ntfs" 
/dev/sda5: UUID="12E6FBCC926ADC41" LABEL="Jacob" TYPE="ntfs" 
/dev/sdb1: UUID="f6e2bb32-83bc-40ef-9c37-760533336c02" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="af3eaa6f-8fde-426d-b7fd-129278ad1ae5" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: LABEL="STATHOULIS" UUID="5802-AFF7" TYPE="vfat" 
/dev/sdd1: UUID="DE101934101914DD" LABEL="12" TYPE="ntfs" 

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
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/STATHOULIS type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdd1 on /media/12 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetecte system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1f7e1f7d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,823,014    80,822,952   7 HPFS/NTFS
/dev/sda2          80,823,015   234,436,544   153,613,530   f W95 Ext d (LBA)
/dev/sda5          80,823,078   234,436,544   153,613,467   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe44fe44f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             48     7,831,551     7,831,504   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37d9152c

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A4CC0586CC055448" TYPE="ntfs" 
/dev/sda5: UUID="12E6FBCC926ADC41" LABEL="Jacob" TYPE="ntfs" 
/dev/sdb1: UUID="f6e2bb32-83bc-40ef-9c37-760533336c02" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="af3eaa6f-8fde-426d-b7fd-129278ad1ae5" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: LABEL="STATHOULIS" UUID="5802-AFF7" TYPE="vfat" 
/dev/sdd1: UUID="DE101934101914DD" LABEL="12" TYPE="ntfs" 

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
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/STATHOULIS type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdd1 on /media/12 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetectows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Fat16
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

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
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1f7e1f7d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,823,014    80,822,952   7 HPFS/NTFS
/dev/sda2          80,823,015   234,436,544   153,613,530   f W95 Ext d (LBA)
/dev/sda5          80,823,078   234,436,544   153,613,467   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe44fe44f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             48     7,831,551     7,831,504   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37d9152c

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A4CC0586CC055448" TYPE="ntfs" 
/dev/sda5: UUID="12E6FBCC926ADC41" LABEL="Jacob" TYPE="ntfs" 
/dev/sdb1: UUID="f6e2bb32-83bc-40ef-9c37-760533336c02" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="af3eaa6f-8fde-426d-b7fd-129278ad1ae5" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: LABEL="STATHOULIS" UUID="5802-AFF7" TYPE="vfat" 
/dev/sdd1: UUID="DE101934101914DD" LABEL="12" TYPE="ntfs" 

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
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/STATHOULIS type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdd1 on /media/12 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

---

### Post by souraklis on 2009-05-04
The two situations i ve got is the following.
The first one is that when i put in the first place the hard disk of windows i enter normally without appearing to me dual boot menu. The second case is that when i ve put the second hard disk with ubuntu in first place it appearing to me the dual boot menu. When i entered in windows it shows me that:

MTLDL is missing.

And for ubuntu is shows me that after trying to boot for a minute:

```
GAve up waiting for boot device,common problems
-boot args(at/proc/cmd/cmdlive)
-check rootdelay=(did the system waiting long enough?)
-Missing modules (cat/proc/modules;/is/dev)
ALERT!/dev/disk/by-uuid/f6e2bb22-...-...-...
Busy box v1.10.2(ubuntu1:10.10.2-1ubuntu 7) built-mshell(ash)
Enter 'help' for a list of built in commands.
(initramfs)_
```

---

### Post by Didius Falco on 2009-05-04
I've saved the output and will have a good hard look at it tomorrow. Sorry to make you wait, but it is 2:10 AM here and I'm very tired.

I'll look it over after I've had a cup or 3 of coffee tommorrow, and post something back at that time.

Meanwhile, maybe someone else will jump in and look it over.

"Talk" to you then!

---

### Post by souraklis on 2009-05-04
ok definitely no problem and thank for help. If here in my country is 19:15 it means that you are from China or Japan or from place near there???

---

### Post by Didius Falco on 2009-05-04
I'm in Brisbane, Australia. I'm originally from the USA, but I moved here 11 years ago and have lived here ever since.

---

### Post by Didius Falco on 2009-05-05
Souraklis,

Sorry for the long delay. I think at this stage, since Windows is booting up okay by itself, all we need to do is reinstall Grub to the proper location and you should be set.

If Windows won't boot from the Grub menu after this, it'll be because we need to make some small adjustments to the menu.lst and possibly the fstab file.

Boot from the Live CD into the "make no changes" option.

After it is booted up, open a terminal and type ```
sudo grub
```Next, type:

```
find /boot/grub/stage1
```You'll use the returned value in the next command. I think it will be (hd1,0) based on your fdisk output - if it's different, use the value Grub returns.

```
root (hd1,0)
```This points the grub menu to the right place to finish booting.

Then type

```
setup (hd0)
```This puts the Grub bootloader into the MBR (main boot record) of drive 0 (it can be a little confusing at first - the numbering starts from zero, so what you and I would think of as drive 1, grub sees as drive 0.)

Finally, type ```
quit
```Reboot without the CD in the drive and try to boot into Ubuntu. If that works, try the Windows entry. If either of them do not work, rerun that script (directions above) and post the whole output of it here.

BTW, do you have more than one version of Windows installed?

Regards,

Didius

---

### Post by souraklis on 2009-05-06
This is the output:

```
[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,0)

grub> setup (hd0)

Error 12: Invalid device requested

```

---

### Post by Didius Falco on 2009-05-06
You skipped a step, my friend.

Boot back into the Live CD

Open a Terminal window

type```
sudo grub
```

This puts you in the grub mode

type 
```
root (hd0,1)
```

Then type
```
setup (hd0)
```

Lastly, type 
```
quit
```

This will take you out of the Grub program.

Reboot without the Live CD and you should see your Grub menu. Test out Ubuntu and Windows and let me know how it goes. :cool:

---

### Post by souraklis on 2009-05-06
Ok now after these commands I normally can boot to windows from the dual boot menu but when i tried to boot to ubuntu it loaded for 1-2 minutes and after i received this:



```


GAve up waiting for boot device,common problems
-boot args(at/proc/cmd/cmdlive)
-check rootdelay=(did the system waiting long enough?)
-Missing modules (cat/proc/modules;/is/dev)
ALERT!/dev/disk/by-uuid/f6e2bb22-...-...-...
Busy box v1.10.2(ubuntu1:10.10.2-1ubuntu 7) built-mshell(ash)
Enter 'help' for a list of built in commands.
(initramfs)_

```

---

### Post by Didius Falco on 2009-05-06
Okay, that's progress. I'll look over that output and see what I can spot...

---

### Post by souraklis on 2009-05-06
i tried again and now it didnt show me something but the system tried to boot and failed and the monitor closed(sleep mode).

---

### Post by Didius Falco on 2009-05-06
I think we are just one step away! The reason that you are getting that error when you try to start Ubuntu is because Grub is looking at the fstab file to find out where the kernel is supposed to be, but the info in the fstab file is not point to the right place.

Boot with the Live CD ( I know you are probably getting tired of doing that, but it sure is handy to fix things) and open your fstab file. You'll need root privileges to edit it, so open a terminal and type ```
sudo gedit 
```When the editor opens, navigates to the fstab file, which in your case is located on the second hard drive, in the first partition. You'll find it at **/etc/fstab**

After you open it, look for this UUID number: ```
f6e2bb32-83bc-40ef-9c37-760533336c02
```When you spot the line with that number, look at the very front of the line. For example, here is a line from one of mine:

```
# / was on /dev/sda13 during installation
UUID=b99e7427-253b-4f2c-b72f-b494e8955ddb /               ext4    relatime,errors=remount-ro 0       1
```That's where you'll see the UUID number. Also note the line starting with the **#** that tells where / (root) was located during the install. That is what has changed on your system - yours will probably say ```
# / was on /dev/sda1 during installation
```Your / is now on sdb1, not sda1, so that line in your fstab now looks something like this:

```
# / was on /dev/sda1 during installation
UUID=f6e2bb32-83bc-40ef-9c37-760533336c02 /               ext3    relatime,errors=remount-ro 0       1
```You need to change it to the following:

```
# / was on /dev/sdb1 during installation
/dev/sdb1  /               ext3    relatime,errors=remount-ro 0       1
 
```In short, you'll change the comment line (the one starting with the #) to reflect how it is now set up. This isn't vital, but that way if you ever have to look at that fstab again, all the information will match, and it won't be confusing.

On the next line, just delete all the UUID part, and replace it with what I've posted. Save the file, reboot, and test the Ubuntu boot again. It should be working now.

Regards,

Didius

---

### Post by souraklis on 2009-05-07
Basically i cant find ths fstab. I only find a doc /etc/fstab but in the filesystem

```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0
```

I am afraid that i dont have access to the second hard disk (if you mean the hard disk where i got ubuntu) i can open it but i can only see 4 things in a weird language.(this is the name of 4 files ä½.ä½).

---

### Post by Didius Falco on 2009-05-07
At this point, since you can't even access it, I'd suggest formatting it and reinstalling Ubuntu.

That will rewrite the Grub menu, complete with your Windows installs and everything should work - unless that drive is failing.

Sorry, souraklis, I've really tried, but I just don't know what else to do in this case.

Regards,

Didius

---

### Post by souraklis on 2009-05-07
Nevermind i also have tired. The only reason I didn t reinstall from the beggining ubuntu is to learn something. I have a question for you, if i install again ubuntu i ll have two kernels. How should i remove the elder kernel from my system??????????

---

### Post by Didius Falco on 2009-05-07
If you reinstall after formatting the drive, It will overwrite that kernel.

You may get a second, or even a third kernel, through updates, and you can always remove those, but I recommend keeping two of them, in case you run into problems with one.

If you get too many kernels and want to remove one or two, just post and we'll let you know how.

Regards,

Didius

---

### Post by souraklis on 2009-05-07
Absolutely thank you didius, i appreciate the help you provide to me. I ll format the disk and afterthat i reinstall ubuntu.:P

---

### Post by bgiannes on 2009-09-25
I'm in the same boat, 'grub error 2'

after sometime; working a solution this is what i've got; 


Note: my PC has an old bios that can only read up to ata-100 (137GM HD's), so i got a IDE card w/ ata-133 (larger then 137 support).  I have an ubuntu server install on a 200MB IDE hd (came from another PC)

now; when i boot to the 200MB grub runs then a get the error 2...

So; i got an older 40GB HD and did a fresh install of ubuntu server, (connected to the MoBo IDE controler) and connected the 200GB HD to the ata-133 card.

Now i can boot to the 40MB install (from grub w/o problems) and then mount the 200MB hd w/o problems!

but i can't boot directly to the 200GB hd, it seems to me that the bios can't see the 200GB HD, but the ubuntu install on the 40GB HD can.

so i think error 2 is a hardware problem, incompatibility issue.

---

### Post by Guinness2702 on 2009-10-25
Just a quick tip on how I eventually solved this problem on my own system.

Bottom line is, according to something I read elsewhere on the net is that linux/grub doesn't see the disks in the same order as BIOS (possibly because I have a mixture SATA and parallel drives).

(hd0) in grub was not my primary/boot drive, this was actually (hd1) as grub saw it.  My guess is that the reason I got this error was that I was trying to setup grub on (hd0), as did the ubuntu installer.  The Error 2 was actually coming from my previous installation of grub on the real primary/boot drive (hd1), which had not been changed and was still pointing at my now completely re-formatted and re-installed ubuntu partition, and for one reason or another the old grub installation could no longer read it.

The solution then?

Boot off the ubuntu installer CD, and run in 'try ubuntu' mode.  Then, from a terminal:-

$ sudo bash
# grub
grub> root (hd1,1)
grub> setup (hd1)

That's it, reboot!

(hd1,1) is where ubuntu was installed
(hd1) is what BIOS thinks is the first drive, and boots from.

YMMV (I also found that I needed to add map lines for (hd0)-(hd2) and vice versa in menu.lsg to get XP to boot - and I also fixed the MBR on my XP partition with ms-sys, before trying the map lines, as it may well have been replaced by the installer setting it up, but I don't know if I really needed to do that)

---


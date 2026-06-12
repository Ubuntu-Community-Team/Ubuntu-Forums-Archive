---
title: "I downloaded and installed latest Ubuntu Updates, then had a booting problem!"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by looi76 on 2009-01-30
Hi, I downloaded and installed the latest Ubuntu updates and then restart my computer as that was required. After I restarted it, in the GRUB List Ubuntu was changed to Debian!

[[IMG]http://img231.imageshack.us/img231/7754/30012009395xy7.th.jpg[/IMG]](http://img231.imageshack.us/my.php?image=30012009395xy7.jpg)

Here is the current **menu.lst**:

```
#gfxmenu /boot/grub/message.ububrown

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
timeout		15

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
# kopt=root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7a781a1b-632d-4e71-921d-fa92b23b0d9f

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

title		Debian GNU/Linux, kernel 2.6.27-11-generic
root		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic

title		Debian GNU/Linux, kernel 2.6.27-11-generic (recovery mode)
root		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Debian GNU/Linux, kernel 2.6.27-9-generic
root		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro quiet splash
initrd		/boot/initrd.img-2.6.27-9-generic

title		Debian GNU/Linux, kernel 2.6.27-9-generic (recovery mode)
root		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Debian GNU/Linux, kernel 2.6.27-7-generic
root		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic

title		Debian GNU/Linux, kernel 2.6.27-7-generic (recovery mode)
root		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Debian GNU/Linux, kernel memtest86+
root		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP/Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title		Microsoft Windows XP Professional
#root		(hd0,1)
#savedefault
#makeactive
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
#title		Windows Vista/Longhorn (loader)
#root		(hd0,2)
#savedefault
#makeactive
#chainloader	+2

```

I had a backup from a long time, here is it:

```
gfxmenu /boot/grub/message.ubugrey

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
default		4

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
# kopt=root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7a781a1b-632d-4e71-921d-fa92b23b0d9f

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
uuid		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		7a781a1b-632d-4e71-921d-fa92b23b0d9f
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		7a781a1b-632d-4e71-921d-fa92b23b0d9f
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Boot Manager
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title		Microsoft Windows XP Professional
#root		(hd0,1)
#savedefault
#makeactive
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
#title		Windows Vista/Longhorn (loader)
#root		(hd0,2)
#savedefault
#makeactive
#chainloader	+1

```

I know that I can use the backup to load Ubuntu, but I want to load Ubuntu with kernel 2.6.27-11-generic, what should I do?

---

### Post by Elfy on 2009-01-30
Have you tried to actually boot it?

The first line is only a title - it could say foddle doodle boodle - but will still boot the kernel you have in your install

---

### Post by looi76 on 2009-01-30
Ubuntu doesn't load, I get an error after click on it! Do you want a screenshot?

---

### Post by Elfy on 2009-01-30
Yea or write it down

Do any of the options in that list work for you?

---

### Post by looi76 on 2009-01-30
When I click on Debian GNU/Linux, kernel 2.6.27-11-generic
[[IMG]http://img403.imageshack.us/img403/3015/30012009396zt6.th.jpg[/IMG]](http://img403.imageshack.us/my.php?image=30012009396zt6.jpg)

When I click on Debian GNU/Linux, kernel 2.6.27-9-generic
[[IMG]http://img105.imageshack.us/img105/4637/30012009397sl4.th.jpg[/IMG]](http://img105.imageshack.us/my.php?image=30012009397sl4.jpg)

---

### Post by Elfy on 2009-01-30
mmm ok - well I think you'd get the same issue with your backup as the UUIDs are the same.

Boot the livecd, open a terminal and run

```
blkid
sudo fdisk -l
```

First will give you UUIDs for your drives, from the second you can see which is your root drive - the install - use the device name for your buntu install - somethign like /dev/sdxy - replace your drive in the next set

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/sdxy /mnt/tmp

```

If the UUID for the drive and that in menu.lst don't match then change menu.lst to suit

```
gksu gedit /mnt/tmp/boot/grub/menu.lst
```

If they do match - post back

---

### Post by looi76 on 2009-01-30
> **forestpixie said:**
> 

If the UUID for the drive and that in menu.lst don't match then change menu.lst to suit

```
gksu gedit /mnt/tmp/boot/grub/menu.lst
```

How can I know if the UUID for the drive and in the menu list match?

---

### Post by Elfy on 2009-01-30
blkid will report the UUID, for example for me

> /dev/sda2: UUID="9d44e64b-0c3f-4376-93f5-7e0a4bc9afac" TYPE="ext3" 

corresponding boot in menu.lst
> title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		9d44e64b-0c3f-4376-93f5-7e0a4bc9afac


Just check one against the other - if they are the same can you run

```
sudo fdisk -l
ls /boot
```

and we can try and sort a boot out for you

---

### Post by looi76 on 2009-01-30
They are the same:(

```
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="31CE9ECE21729F06" LABEL="Vista" TYPE="ntfs" 
/dev/sda2: UUID="D6141B49141B2BCD" LABEL="XP" TYPE="ntfs" 
/dev/sda4: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="**7a781a1b-632d-4e71-921d-fa92b23b0d9f**" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="bb6c5bfa-f5f4-4764-bd66-2953461de0f6" 
/dev/loop0: TYPE="squashfs" 
```

```
title		Debian GNU/Linux, kernel 2.6.27-11-generic
root		**7a781a1b-632d-4e71-921d-fa92b23b0d9f**
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic
```

---

### Post by Elfy on 2009-01-30
Ok run these and post them please

```
cat /mnt/tmp/boot/grub/menu.lst
sudo fdisk -l
ls /boot
```

---

### Post by looi76 on 2009-01-30
Here is the output:

```
ubuntu@ubuntu:~$ cat /mnt/tmp/boot/grub/menu.lst
#gfxmenu /boot/grub/message.ububrown

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
timeout		15

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
# kopt=root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7a781a1b-632d-4e71-921d-fa92b23b0d9f

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

title		Debian GNU/Linux, kernel 2.6.27-11-generic
root		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic

title		Debian GNU/Linux, kernel 2.6.27-11-generic (recovery mode)
root		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Debian GNU/Linux, kernel 2.6.27-9-generic
root		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro quiet splash
initrd		/boot/initrd.img-2.6.27-9-generic

title		Debian GNU/Linux, kernel 2.6.27-9-generic (recovery mode)
root		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Debian GNU/Linux, kernel 2.6.27-7-generic
root		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic

title		Debian GNU/Linux, kernel 2.6.27-7-generic (recovery mode)
root		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Debian GNU/Linux, kernel memtest86+
root		7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP/Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title		Microsoft Windows XP Professional
#root		(hd0,1)
#savedefault
#makeactive
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
#title		Windows Vista/Longhorn (loader)
#root		(hd0,2)
#savedefault
#makeactive
#chainloader	+2

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8b59c4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25920   208202368+   7  HPFS/NTFS
/dev/sda2           25921       33764    63006930    7  HPFS/NTFS
/dev/sda3           33765       37420    29366820    5  Extended
/dev/sda4           37421       38913    11992522+   7  HPFS/NTFS
/dev/sda5           33765       36376    20980858+  83  Linux
/dev/sda6           36377       37420     8385898+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ ls /boot
abi-2.6.27-7-generic     System.map-2.6.27-7-generic
config-2.6.27-7-generic  vmcoreinfo-2.6.27-7-generic
memtest86+.bin
ubuntu@ubuntu:~$ 

```

---

### Post by Elfy on 2009-01-30
sorry - try looking in the install 

```
ls /mnt/tmp/boot
```

---

### Post by looi76 on 2009-01-30
Here is the output:

```
ubuntu@ubuntu:~$ ls /mnt/tmp/boot
abi-2.6.27-11-generic         memtest86+.bin
abi-2.6.27-7-generic          System.map-2.6.27-11-generic
abi-2.6.27-9-generic          System.map-2.6.27-7-generic
config-2.6.27-11-generic      System.map-2.6.27-9-generic
config-2.6.27-7-generic       vmcoreinfo-2.6.27-11-generic
config-2.6.27-9-generic       vmcoreinfo-2.6.27-7-generic
grub                          vmcoreinfo-2.6.27-9-generic
initrd.img-2.6.27-11-generic  vmlinuz-2.6.27-11-generic
initrd.img-2.6.27-7-generic   vmlinuz-2.6.27-7-generic
initrd.img-2.6.27-9-generic   vmlinuz-2.6.27-9-generic
ubuntu@ubuntu:~$ 


```

---

### Post by Elfy on 2009-01-30
That's better - just wanted to make sure it was all there.

Open the file to edit it with
```
gksu gedit /mnt/tmp/boot/grub/menu.lst
```

Just above the first boot option put this

```
title		test
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic

title		test2
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic
```

Try them - they are each slightly different

---

### Post by looi76 on 2009-01-30
Result from **test**:

```
  Booting 'test'

root  (hd0,4)
 Filesystem type unknown, partition type 0x5
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro quiet splash

Error 17: Cannot mount selected partition

Press any key to continue...
```

Result from **test2**:

```
  Booting 'test2'

root  (hd0,4)
 Filesystem type unknown, partition type 0x5
kernel /boot/vmlinuz-2.6.27-11-generic root=/dev/sda5 ro quiet splash

Error 17: Cannot mount selected partition

Press any key to continue...
```

---

### Post by hyper_ch on 2009-01-30
what's the output of
```

sudo fdisk -l

``` ?

---

### Post by looi76 on 2009-01-30
Output of **sudo fdisk -l**:

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8b59c4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25920   208202368+   7  HPFS/NTFS
/dev/sda2           25921       33764    63006930    7  HPFS/NTFS
/dev/sda3           33765       37420    29366820    5  Extended
/dev/sda4           37421       38913    11992522+   7  HPFS/NTFS
/dev/sda5           33765       36376    20980858+  83  Linux
/dev/sda6           36377       37420     8385898+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

---

### Post by hyper_ch on 2009-01-30
no clue :(

---

### Post by looi76 on 2009-01-30
Sorry, but I didn't mention that I didn't download all the updates for ubuntu. There were 74 files to download but I only downloaded and installed at 23 files, doesn't that have to do with anything?

---

### Post by hyper_ch on 2009-01-30
shouldn't... there should be no reason why it says now debian.

---

### Post by cjv8888 on 2009-01-30
First download the [bootinfo script]("http://sourceforge.net/projects/bootinfoscript/") to your desktop then

please post the result.txt after running the script below which may give a bit more information:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by Elfy on 2009-01-30
All very odd - you could try to reinstall grub with the livecd

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start

It's all there on sda5 which is hd0,4

When you did the mount command right at the beginning I assume that you did use /dev/sda5? Where I said sudo mount -t ext3 /dev/sdxy /mnt/tmp

You did sudo mount -t ext3 /dev/sda5 /mnt/tmp - can you confirm that.

---

### Post by PreviousN on 2009-01-30
You may also try *not* using UUIDs. Simply replace the boot parameter to /dev/sda5. The benefit of using UUIDs is that if you move the drive around *inside* your computer, it can still boot. 

So it would look like:
```

title		Ubuntu 8.10 Kernel 2.6.27-9-generic		
     root (hd0,5)
     kernel /boot/vmlinuz-2.6.27-9-generic root=/dev/sda5 ro quiet splash 
     initrd /boot/initrd.img-2.6.27-9-generic

```

I *think* that the second line is correct, also meaning that I *think* it should be (hd0,5), not 4. The number after the comma means the partition of the drive. In your output earlier it was clearly stated that you were using sda5 for linx...Though I could be wrong...

Check this guide to read more on grub: [http://wiki.linuxquestions.org/wiki/GRUB#Manual_configuration](http://wiki.linuxquestions.org/wiki/GRUB#Manual_configuration)

The easiest fix for this is likely reinstalling grub. If I were in your situation I would follow forestpixie's advice of reconfiguring grub, instead of editing the broken one into oblivion.

---

### Post by Elfy on 2009-01-30
hd0,5 would be sda6 the swap partition

grub starts at 0

---

### Post by looi76 on 2009-01-30
I entered the first entery from my backup menu.lst into the current menu.lst and it **WORKED!** :p

```
title Ubuntu 8.10, kernel 2.6.27-9-generic
uuid 7a781a1b-632d-4e71-921d-fa92b23b0d9f
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=7a781a1b-632d-4e71-921d-fa92b23b0d9f ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic
quiet

```

Now, Ubuntu works with kernel 2.6.27-9-generic. How can I make it run with kernel 2.6.27-11-generic?

---

### Post by PreviousN on 2009-01-30
Thanks for the clarification. I just saw that.

---

### Post by hyper_ch on 2009-01-30
just replace -9 with -11 and create a new entry :) and try

---

### Post by looi76 on 2009-01-30
GREAT :D It worked. Thanks forestpixie, hyper_ch, PreviousN and cjv8888 for helping me...

---

### Post by Elfy on 2009-01-30
I think I have it - try changing root to uuid in the original menu.lst - not the backup see if that works

---

### Post by PreviousN on 2009-01-30
Since you've solved the problem, why not mark the thread as solved. This makes it useful for others with the same problem in the future. To mark your thread solved, go to Thead Tools and select Mark this thread as solved

---

### Post by Elfy on 2009-01-30
> **PreviousN said:**
> Since you've solved the problem, why not mark the thread as solved. This makes it useful for others with the same problem in the future. To mark your thread solved, go to Thead Tools and select Mark this thread as solved

The tool has gone as have thanks  - [http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---


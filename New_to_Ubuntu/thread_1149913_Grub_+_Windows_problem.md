---
title: "Grub + Windows problem"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by andy_blah on 2009-05-05
I can't seem to boot to Window$ XP after I have installed it. I re-installed GRUB on the MBR after Window$'s messy install. 

Here is what it says:
```
Error 12: Invalid device requested
```

Here is the output of fdisk -l:
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x071fa7ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2            1306        1436     1052257+  82  Linux swap / Solaris
/dev/sda3            1437        3526    16787925    f  W95 Ext'd (LBA)
/dev/sda4   *        3527        4865    10755517+  83  Linux
/dev/sda5            1437        3526    16787893+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d0e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2            8422        9729    10506510   83  Linux
/dev/sdb3               1        8421    67641651   83  Linux
/dev/sdb4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

And this is what I have in GRUB's menu.lst:

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
# kopt=root=UUID=2a5db891-6d40-456c-828c-7a6134fce419 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2a5db891-6d40-456c-828c-7a6134fce419

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		2a5db891-6d40-456c-828c-7a6134fce419
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2a5db891-6d40-456c-828c-7a6134fce419 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		2a5db891-6d40-456c-828c-7a6134fce419
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2a5db891-6d40-456c-828c-7a6134fce419 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		2a5db891-6d40-456c-828c-7a6134fce419
kernel		/boot/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST

title 		Windows XP
rootnoverify 	(hd0,4)
makeactive
chainloader 	+1
```

(note: I had to add the entry to Windows in the list because GRUB didn't do it after I re-installed it in the MBR)

sda5 is Window$'s partition

---

### Post by arapa on 2009-05-05
What if you turn on the boot flag on the Windows partion instead of 'makeactive' in menu.lst?

Also- here's someone else with that error that seemed to get it fixed...

[http://ubuntuforums.org/showthread.php?t=1123109&page=2](http://ubuntuforums.org/showthread.php?t=1123109&page=2)

---

### Post by blazemore on 2009-05-05
Your PC might be set to boot from the 2nd hard-drive
Try changing the Windows drive in grub to
```
title 		Windows XP
rootnoverify 	(hd1,4)
makeactive
chainloader 	+1
```

---

### Post by caljohnsmith on 2009-05-05
Windows XP will not allow you to install it to a logical partition (like sda5 where yours is installed) unless there is a primary NTFS/FAT partition available on the master drive where Windows can put its boot files, and currently your HDD has no primary NTFS/FAT partitions; therefore Windows is probably missing its boot files to start with. Also, to boot Windows directly from a logical partition requires special steps. If you would like help doing that, it would help to first get more information about your setup, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and what it might take to boot your Windows install from Grub.

John

---

### Post by andy_blah on 2009-05-06
> **caljohnsmith said:**
> Windows XP will not allow you to install it to a logical partition (like sda5 where yours is installed) unless there is a primary NTFS/FAT partition available on the master drive where Windows can put its boot files, and currently your HDD has no primary NTFS/FAT partitions; therefore Windows is probably missing its boot files to start with. 

Prior to [this]("http://ubuntuforums.org/showthread.php?t=1142397") thread, I did have a primary NTFS partition, only that it had some problems, so after installing Window$, it decided to erase that partition (without my confirmation), formatted it to FAT32, and after that it probably placed the boot files on that partition (it is pretty stupid for a installer to do such a thing), and after I've deleted the FAT partition, it stopped working properly. Now, since I didn't do much in Window$, I will just re-install it on a already made partition in GParted and re-install GRUB into the MBR

Thank you all for the help :)

---


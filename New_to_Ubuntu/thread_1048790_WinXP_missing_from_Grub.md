---
title: "WinXP missing from Grub"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by EliteTempleton on 2009-01-23
I just reloaded this laptop(a friends) to dual boot Ubuntu & XP.
I loaded XP first. After loading Ubuntu, XP was missing/not listed in Grub.

I got close by following [this]("http://ubuntuforums.org/archive/index.php/t-942982.html") thread, to fixing it. 

Windows XP is now listed, but it gives me an error when selected about not being able to find the disc. 

I'm fairly sure it's because I don't know how to get the entry to point to the right spot(hard drive location...), which is fairly obvious upon review of my menu.lst as I only copied the entry from the above thread and placed it in the right spot(I think, must be because XP shows up now).

I think that about covers it, here is what my menu.lst looks like, what do I need to change? 
=====================================


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
timeout		9

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
#      password --md5 $1$gLhU0/$aM78kHK16j93P4b2znUoe/
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
# kopt=root=UUID=7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6

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
uuid		7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6
kernel		/boot/memtest86+.bin
quiet

title 		Windows XP
root 		(hd1,0)
map 		(hd0) (hd1)
map 		(hd1) (hd0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by kansasnoob on 2009-01-23
We also need to see the output of:

```
sudo fdisk -l
```

NOTE: That's a lower case L.

---

### Post by EliteTempleton on 2009-01-23
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        5136    41254888+   f  W95 Ext'd (LBA)
/dev/sda5            1313        3224    15358108+   7  HPFS/NTFS
/dev/sda6            3225        5136    15358108+  83  Linux
/dev/sda7               1         365     2931768   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by halitech on 2009-01-23
I believe this```
title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```
should be```
title Windows XP
root (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```

although I'll admit, not sure on the map options

---

### Post by kansasnoob on 2009-01-23
> **EliteTempleton said:**
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        5136    41254888+   f  W95 Ext'd (LBA)
/dev/sda5            1313        3224    15358108+   7  HPFS/NTFS
/dev/sda6            3225        5136    15358108+  83  Linux
/dev/sda7               1         365     2931768   82  Linux swap / Solaris

Partition table entries are not in disk order

Yikes! Is Windows really in an extended partition? That may be a problem, although I think caljohnsmith knows how to get it to boot if that's true.

Would you please install gparted (either from synaptic) or:

```
sudo apt-get install gparted
```

It'll then show up in System > Administration > Partition Editor.

Then post a screenshot of gparted so I can verify whether or not Win is actually in an extended partition.

---

### Post by caljohnsmith on 2009-01-23
Your only NTFS partition is sda5, which is a logical partition. Windows won't let you install itself to a logical partition unless there is a primary NTFS/FAT partition available where you can put its boot files. To boot Windows entire from a logical partition takes a little work usually. In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot Windows from Grub.

---

### Post by louieb on 2009-01-23
Looks like XP is in sda5. Thats bad news. XP does not like being in a logical partition. It wants its boot-loader files in a primary partition.  
Don't think its going to work but to chainload a boot loader in sda5 the entry would look like this.
```

title        Windows 95/98/NT/2000/XP
root        (hd0,4)
chainloader    +1

```Also look likes only half the disk is allocate to your partitions. Leaving you unable to use half of the drives space. Since this is a fresh install. Think I learn a little about partitions and try the install again.

[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm") 
[HowTo: Partitioning Basics - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?&t=282018") 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") 

Have fun and good luck.

---

### Post by EliteTempleton on 2009-01-23
> **halitech said:**
> I believe this```
title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```
should be```
title Windows XP
root (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```

although I'll admit, not sure on the map options

K, I changed this and the error changed, I wrote it down this time:

Error 22: No such partition


Note: Now working on what you asked for caljohnsmith

---

### Post by kansasnoob on 2009-01-23
> **caljohnsmith said:**
> Your only NTFS partition is sda5, which is a logical partition. Windows won't let you install itself to a logical partition unless there is a primary NTFS/FAT partition available where you can put its boot files. To boot Windows entire from a logical partition takes a little work usually. In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot Windows from Grub.

Always glad to see you!

---

### Post by EliteTempleton on 2009-01-23
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10000000

Partition  Boot        Start          End         Size  Id System

/dev/sda2    *            63   82,509,839   82,509,777   f W95 Ext'd (LBA)
/dev/sda5         21,077,343   51,793,559   30,716,217   7 HPFS/NTFS
/dev/sda6         51,793,623   82,509,839   30,716,217  83 Linux
/dev/sda7                189    5,863,724    5,863,536  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="28381A303819FE0E" TYPE="ntfs" 
/dev/sda6: UUID="7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6" TYPE="ext3" 
/dev/sda7: UUID="f2cad8f1-18d2-461c-9900-dbd5213b5c2f" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jade/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jade)

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		9

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
#      password --md5 $1$gLhU0notimportantb2znUoe/
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
# kopt=root=UUID=7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6

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
uuid		7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6
kernel		/boot/memtest86+.bin
quiet

title 		Windows XP
root 		(hd0,0)
map 		(hd0) (hd1)
map 		(hd1) (hd0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=7362d4fe-ba45-4d8d-9bc4-4fd381de7dd6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=f2cad8f1-18d2-461c-9900-dbd5213b5c2f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location  of files loaded by Grub: ===================


  34.8GB: boot/grub/menu.lst
  34.8GB: boot/grub/stage2
  34.7GB: boot/initrd.img-2.6.27-7-generic
  34.5GB: boot/initrd.img-2.6.27-9-generic
  34.6GB: boot/vmlinuz-2.6.27-7-generic
  34.6GB: boot/vmlinuz-2.6.27-9-generic
  34.5GB: initrd.img
  34.7GB: initrd.img.old
  34.6GB: vmlinuz
  34.6GB: vmlinuz.old

=============================== StdErr Messages: ===============================

No errors were reported.
```

Do you still want a gparted screenshot?

---

### Post by caljohnsmith on 2009-01-23
As I suspected, you are missing your XP boot files. How about following [this tutorial]("http://ubuntuforums.org/showpost.php?p=5082723") for how to restore your XP boot files and also boot XP from a logical partition; when you get to the part about configuring your boot.ini file, you should use "partition(1)" in the boot.ini file. Also make sure to do the testdisk procedure in step 5, because your Win XP boot sector does not have the correct starting sector position of the sda5 partition. Let me know how that goes or if you run into problems.

---

### Post by EliteTempleton on 2009-01-24
k, followed the directions...

1.) Mounted the drive(I just used the right click & mount option...)

2.) Extracted the files to the root of the XP Partition. 

3.) Made no edits as it was already set to partition(1). But thanks for letting me know I so I did not have to wonder. ;)

4.) A bit confused here, first I changed my menu.lst by commenting out the makeactive part:
```
title 		Windows XP
root 		(hd0,0)
map 		(hd0) (hd1)
map 		(hd1) (hd0)
###  makeactive
chainloader +1
```

Then when I read the detail part and it said to use

title XP
rootnoverify (hd0,4)
chainloader +1

So, I edited the menu.lst again to:

```
title 		Windows XP
rootnoverify (hd0,0)
### root 		(hd0,0)
map 		(hd0) (hd1)
map 		(hd1) (hd0)
###  makeactive
chainloader +1
```

5.) Ran the testdisk rebuild tool and final page looked like this:

```
Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63

     Partition                  Start        End    Size in sectors

 5 L HPFS - NTFS           1312   1  1  3223 254 63   30716217



Boot sector

Status: OK



Backup boot sector

Status: OK



Sectors are identical.



A valid NTFS Boot sector must be present in order to access

any data; even if the partition is not bootable.
```

Rebooted and selected XP from the list. Got this error:

```
Error 13: Invalid or unsupported executable format
```

Being confused about the menu.lst file I tried editing it to this, and rebooting:

```
title 		Windows XP
### rootnoverify (hd0,0)
root 		(hd0,0)
map 		(hd0) (hd1)
map 		(hd1) (hd0)
###  makeactive
chainloader +1
```

Resulting in a different error, but same as earlier in this thread:

```
Error 22: No such partition
```

---

### Post by EliteTempleton on 2009-01-24
If it helps, the contents of the XP root now looks like this:

```
dell
Documents and Settings
Program Files
System Volume Information
WINDOWS
AUTOEXEC.BAT
boot.ini
CONFIG.SYS
IO.SYS
MSDOS.SYS
newfile.enc
newkey
NTDETECT.COM
NTLDR
pagefile.sys
```

---

### Post by caljohnsmith on 2009-01-24
Since your XP install is on sda5, you should use the Grub entry from that tutorial:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
(hd0,4) is sda5 for your setup. How about trying that and let me know how far you get.

---

### Post by EliteTempleton on 2009-01-24
I'm glad I know that a new or different error means progress or this would just be really frustrating... 

New error:

```
Starting up...

A disk read error has occurred

Press Ctrl+Alt+Del to restart
```

---

### Post by caljohnsmith on 2009-01-24
How about doing:
```
sudo hexdump -s 28 -n 4 -e '"%d\n"' /dev/sda5
```
Does that return 63 or 21,077,343?

[QUOTE=kansasnoob]Always glad to see you![/QUOTE]
Nice to see you around too. Seems like the traffic in the forums has dropped off since they started having problems with the servers. Always good to bump into regulars like you and louieb.

---

### Post by EliteTempleton on 2009-01-24
21077343

---

### Post by caljohnsmith on 2009-01-24
Hmmmm... For that command to return 21,077,343 means that you must have done the "Rebuild BS" successfully in testdisk, so there might be other issues. How about booting your Windows Install CD, go to the "recovery console" and do:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. Then try booting Windows again and let me know if anything changes.

---

### Post by EliteTempleton on 2009-01-24
Check disk found and fixed one or more errors.

Rebooted and got same result when I picked Windows XP from GRUB menu.

Trying chkdsk /r again...

---

### Post by EliteTempleton on 2009-01-24
No errors found on the second try of chkdsk.

But still same message

```
Starting up...

A disk read error has occurred
Press Ctrl+Alt+Del to restart
```

---

### Post by caljohnsmith on 2009-01-25
How about using testdisk again, but this time choose "Repair MFT" rather than "Rebuild BS" on your sda5 Windows partition. Then reboot, and let me know if that changes anything. If it doesn't, I'm out of ideas of how you might realistically get your Windows install booting. So if the testdisk procedure doesn't help, I would suggest backing up all your important documents from your Windows and Ubuntu partitions, wipe the drive clean and start over. Or if you want to keep your present Ubuntu partition, you could do that, but you would need to delete your Windows partition and swap partition, shrink the sda2 extended partition from the beginning to make room for Windows, and then you could create a **primary** NTFS partition for Windows at the beginning of the drive. You also have a lot of unused space after the Ubuntu partition where you could put your swap partition, or at least make a data partition to use that space. The main thing is to give Windows a primary partition rather than a logical one, and that will make installing/booting Windows much easier. Let me know how that goes or if you run into problems.

---

### Post by EliteTempleton on 2009-01-25
No change in error message. 
Thanks for all the help trying to get it going. 
Time to quit beating the dead horse and just start over. 
This time I am just going to load XP and then install Ubuntu as a program, I forget the term for doing it, but I'm sure you know what I mean.

---

### Post by caljohnsmith on 2009-01-25
> **EliteTempleton said:**
> No change in error message. 
Thanks for all the help trying to get it going. 
Time to quit beating the dead horse and just start over. 
This time I am just going to load XP and then install Ubuntu as a program, I forget the term for doing it, but I'm sure you know what I mean.
The only thing that really was causing problems was having Windows on a logical partition, so if you install Windows to a primary partition, that should be enough to solve that problem. In other words, if you want to do a dual boot with Ubuntu again, it is usually easy to do if you first give Windows a primary partition and then install Ubuntu afterwards, so I don't think you'll have any problem again. But if you want to install Ubuntu inside of Windows as a Wubi install like you mentioned, that's certainly an option too. Good luck and let me know how it goes.

---

### Post by EliteTempleton on 2009-01-25
Thats how I did it the first time, installed XP and then Ubuntu, not sure what went wrong. But the WUBI is working well.

Though it would not let XP boot to setup so I had to format the entire drive with Ubuntu, then it would let XP Setup boot, alas another entire drive format was in order. 

I probably would have tried a real dual boot again, but she needs the computer completed by tomorrow because her online collage classes start.

---


---
title: "Windows XP refuses to dual boot"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Satum on 2009-01-10
Hello everyone, I'm having problems dual booting into Windows XP after having installed Ubuntu Intrepid. Grub at first did not have an entry for my Windows partition and having added the necessary commands after trawling the forums, I still can't get a boot. The Grub errors range from Error 12 Invalid Device to NTLDR missing depending on the root that I use.

Here is the output from fdisk -l
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe81de81d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       25618   205768552+   f  W95 Ext'd (LBA)
/dev/sda2           25619       37776    97659135   83  Linux
/dev/sda3   *       37777       60801   184948312+   7  HPFS/NTFS
/dev/sda5               2       25496   204788556    7  HPFS/NTFS
/dev/sda6           25497       25618      979933+  82  Linux swap / Solaris
And my modified /boot/brub/menu.lst
> 
## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27-9-generic
uuid        12acf0ee-fc5d-4ae5-9995-c48768900812
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=12acf0ee-fc5d-4ae5-9995-c48768900812 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid        12acf0ee-fc5d-4ae5-9995-c48768900812
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=12acf0ee-fc5d-4ae5-9995-c48768900812 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, memtest86+
uuid        12acf0ee-fc5d-4ae5-9995-c48768900812
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1All that is after ### END DEBIAN AUTOMAGIC KERNELS LIST was added manually and therefore may be incorrect, but I have tried to boot into Windows with the root as hd0,1 to 5.

Any help will be greatly appreciated seeing as I am an Absolute Beginer when it comes to Linux, but I'm looking forward to learning fast.

---

### Post by pastalavista on 2009-01-10
I would recommend that you download, burn and boot from a [SuperGrub Disk]("http://www.supergrubdisk.org/index.php"). It will sort your partitions and fix your grub with one click.

---

### Post by caljohnsmith on 2009-01-10
How about trying:
```
title Microsoft Windows XP Professional
root [COLOR="Blue"](hd0,2)[/COLOR]
savedefault
makeactive
chainloader +1 
```
If for some reason that doesn't work, then to get a better picture of your setup, how about doing:
```
cd ~/Desktop && wget 'http://internap.dl.sourceforge.net/sourceforge/bootinfoscript/boot_info_script.sh' && sudo bash boot_info_script.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.

---

### Post by cdtech on 2009-01-10
I believe you had the correct configuration when you received the "NTLDR missing" error. You may want to give "testdisk" a try after you reinstall your "NTLDR". See this site for more information on this subject:
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

---

### Post by Satum on 2009-01-10
> **caljohnsmith said:**
> How about trying:
```
title Microsoft Windows XP Professional
root [COLOR="Blue"](hd0,2)[/COLOR]
savedefault
makeactive
chainloader +1 
```


After rebooting with the suggested code, I get the NTLDR missing error.
Here is the requested document:

```
============================= Boot Info Summary: ==============================

 => Drive sdb does not have a valid partition table.
 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe81de81d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065   411553169   205768552+   f  W95 Ext'd (LBA)
/dev/sda2       411553170   606871439    97659135   83  Linux
/dev/sda3   *   606871440   976768064   184948312+   7  HPFS/NTFS
/dev/sda5           16128   409593239   204788556    7  HPFS/NTFS
/dev/sda6       409593303   411553169      979933+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="12acf0ee-fc5d-4ae5-9995-c48768900812" TYPE="ext3" 
/dev/sda3: UUID="6678DE5078DE1E9D" TYPE="ntfs" 
/dev/sda5: UUID="E4B83BDBB83BAAC6" TYPE="ntfs" 
/dev/sda6: UUID="46b68c20-4e84-4e41-b9c9-219f497c32d0" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/oliver/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=oliver)

=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=12acf0ee-fc5d-4ae5-9995-c48768900812 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=12acf0ee-fc5d-4ae5-9995-c48768900812

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
uuid		12acf0ee-fc5d-4ae5-9995-c48768900812
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=12acf0ee-fc5d-4ae5-9995-c48768900812 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		12acf0ee-fc5d-4ae5-9995-c48768900812
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=12acf0ee-fc5d-4ae5-9995-c48768900812 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		12acf0ee-fc5d-4ae5-9995-c48768900812
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



# This entry automatically added by the Debian installer for a non-linux OS

title Microsoft Windows XP Professional
root (hd0,2)
savedefault
makeactive
chainloader +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=12acf0ee-fc5d-4ae5-9995-c48768900812 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=46b68c20-4e84-4e41-b9c9-219f497c32d0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda2/boot: ==================================

total 25524
drwxr-xr-x  3 root root    4096 2009-01-07 16:39 .
drwxr-xr-x 21 root root    4096 2009-01-07 17:37 ..
-rw-r--r--  1 root root  503560 2008-11-04 21:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-21 00:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 21:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-21 00:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-10 14:29 grub
-rw-r--r--  1 root root 8668892 2009-01-07 16:38 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8670349 2009-01-07 16:39 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 22:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 21:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-21 00:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 21:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-21 00:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 21:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-21 00:30 vmlinuz-2.6.27-9-generic

=============================== sda2/boot/grub: ===============================

total 232
drwxr-xr-x 2 root root   4096 2009-01-10 14:29 .
drwxr-xr-x 3 root root   4096 2009-01-07 16:39 ..
-rw-r--r-- 1 root root    197 2009-01-07 15:16 default
-rw-r--r-- 1 root root     15 2009-01-07 15:16 device.map
-rw-r--r-- 1 root root   8108 2009-01-07 15:16 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-07 15:16 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-07 15:16 installed-version
-rw-r--r-- 1 root root   8712 2009-01-07 15:16 jfs_stage1_5
-rw-r--r-- 1 root root   4484 2009-01-10 14:29 menu.lst
-rw-r--r-- 1 root root   4449 2009-01-10 14:10 menu.lst~
-rw-r--r-- 1 root root   4950 2009-01-09 20:19 menu.lst_backup
-rw-r--r-- 1 root root   7352 2009-01-07 15:16 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-07 15:16 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-07 15:16 stage1
-rw-r--r-- 1 root root 121460 2009-01-07 15:16 stage2
-rw-r--r-- 1 root root   9556 2009-01-07 15:16 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
```


[QUOTE=pastalavista]I would recommend that you download, burn and boot from a SuperGrub Disk. It will sort your partitions and fix your grub with one click. [/QUOTE]
I have already created a bootable SuperGrub Usb drive and followed suggestions on  the forum, but to no avail.

---

### Post by caljohnsmith on 2009-01-10
OK, it looks like there are at least a few issues that are preventing you from booting Windows right now; for one thing, the script was not able to find your Windows boot files in any of the partitions, so it looks like you will need to replace those. The other issue is that your Windows is on sda5, which is a logical partition, so you have to take a few extra steps to boot Windows from a logical partition. So to replace your necessary Windows XP boot files, how about downloading the attached "WinXP_boot_files3.zip" to your Ubuntu desktop; I configured the boot.ini file in that zipped package so that it should work with your partition arrangement. Then do:
```
sudo mount /dev/sda5 /mnt
cd ~/Desktop
unzip WinXP_boot_files3.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Next open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And use the following entry for Windows:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
Please note that it is important to *not* include the "makeactive" line in the above entry since Windows is on a logical partition, and Grub cannot make a logical partition "active", i.e. set the boot flag on it. And finally reboot, choose Windows from your Grub menu, and let me know exactly what happens. We can work from there. :)

---

### Post by Satum on 2009-01-10
Ok, sorry for the slow reply.

I've got a new error, Windows refuses to boot because > <Windows root>\system32\hal.dll is corrupt or missing 

Thanks for your help

---

### Post by caljohnsmith on 2009-01-10
How about posting:
```
sudo mount /dev/sda5 /mnt
ls -l /mnt/[Ww][Ii][Nn][Dd][Oo][Ww][Ss]/[Ss]ystem32/[Hh][Aa][Ll].[Dd][Ll][Ll]
```
If that last command shows your hal.dll file, then it isn't missing, and I most likely configured your boot.ini file wrong. Please let me know what the output is and we can work from there.

---

### Post by Satum on 2009-01-10
Output of the command you gave me
> 
-rwxrwxrwx 1 root root 131712 2007-04-15 23:22 /mnt/WINDOWS/system32/hal.dll

It seems that hal.dll is there. Hope you cans still help.

---

### Post by caljohnsmith on 2009-01-10
I must have configured your boot.ini file wrong then, and if so, sorry about that. How about trying:
```
sudo mount /dev/sda5 /mnt
gksudo gedit /mnt/boot.ini
```
And then change the two occurrences of "partition(3)" to try different numbers, for instance try "2" first:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)[COLOR="Blue"]partition(2)[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)[COLOR="Blue"]partition(2)[/COLOR]\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn
```
Reboot, try booting Windows, and if you get the same missing hal.dll error, try different values for the partition number in the boot.ini file, including "1". Please let me know how that goes.

---

### Post by Satum on 2009-01-14
Thanks caljohnsmith, seeing as the forums were down yesterday for maintenance I tinkered with the boot files that you gave me and found the right configuration, I can now dual boot Windows and Ubuntu

For future reference here is my menu.lst
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1 
```

And the correct Partition in boot.ini was ```
partition(3)
```
And the relevant Windows boot documents are attached to the post.

---

### Post by caljohnsmith on 2009-01-14
Isn't that exactly what we tried back in post #6? The boot.ini file you downloaded used "partition(3)", so what did you change? Glad to hear Windows is booting OK now though.

---


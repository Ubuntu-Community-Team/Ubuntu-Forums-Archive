---
title: "Grub Problem: Can't boot Windows XP"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by bumblestiltskin on 2008-12-17
Hey Forum,

I can't get Windows XP to boot. 

I am running Ubuntu 8.10 in an attempted dual boot configuration with ~30gb to Ubuntu and ~5gb to Windows. I also have an external 500gb USB drive (mentioned to avoid confusion -- shows in the fdisk output).

I think there is a problem with Grub knowing where (and/or how) my Windows partition is setup.

I have tried variations of editing the root drive for the Windows partition.

Using root "(hd0,4)" I get an error 12.

Using root "(hd1,0)" I get the message "Starting Up..." and then the system hangs requiring a power down to restart.

The way I installed Ubuntu and Windows was this:

I initially had a the whole drive setup up for Windows using the standard XP installer.

I then used G-Parted to split the partitions: ~5gb setup for windows and the remainder empty for Ubuntu.

I installed Windows to the 5gb partition using the XP installer.

I installed Ubuntu 8.10 using the graphical installer set to use free space.

I have included the output from the following commands:

sudo fdisk -lu
cat /boot/grub/menu.lst

Here's to hoping I don't need to start over with partitioning and reinstall!



**[Output of sudo fdisk -lu]:**

Disk /dev/sda: 38.5 GB, 38502535680 bytes
255 heads, 63 sectors/track, 4681 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1640163f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3855    30965256   83  Linux
/dev/sda2   *        3856        4680     6626812+   f  W95 Ext'd (LBA)
/dev/sda5            4028        4680     5245191    7  HPFS/NTFS
/dev/sda6            3856        4027     1381527   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS



[B][Output of cat /boot/grub/menu.lst]
[/B]

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
# kopt=root=UUID=b383cfb8-6aff-4c49-a94f-ee2a538d87c7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b383cfb8-6aff-4c49-a94f-ee2a538d87c7

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
uuid		b383cfb8-6aff-4c49-a94f-ee2a538d87c7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b383cfb8-6aff-4c49-a94f-ee2a538d87c7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		b383cfb8-6aff-4c49-a94f-ee2a538d87c7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b383cfb8-6aff-4c49-a94f-ee2a538d87c7 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b383cfb8-6aff-4c49-a94f-ee2a538d87c7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b383cfb8-6aff-4c49-a94f-ee2a538d87c7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b383cfb8-6aff-4c49-a94f-ee2a538d87c7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b383cfb8-6aff-4c49-a94f-ee2a538d87c7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b383cfb8-6aff-4c49-a94f-ee2a538d87c7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP Home
root (hd1,0)
savedefault
makeactive
chainloader +1

---

### Post by halitech on 2008-12-17
For a first time poster, let me say thank you for including everything we need to help out before we even asked for it :)

I think the issue is with the hd1,0 section in the windows loader, I think it should be reversed looking at your fdisk output, like this
```

title Microsoft Windows XP Home
root (hd0,1)
savedefault
makeactive
chainloader +1
```
grub counts from 0 so the first hard drive would be sda (0) and its on partition 2 (1)

now I might be wrong but I'm pretty sure it goes drive then partition in the numbers.

---

### Post by bumblestiltskin on 2008-12-17
> **halitech said:**
> For a first time poster, let me say thank you for including everything we need to help out before we even asked for it :)


Thanks. I tried to do a little research ahead of time and see if I could figure out the problem myself. Unfortunately, I'm hit a dead end, so here I am.

> 
I think the issue is with the hd1,0 section in the windows loader, I think it should be reversed looking at your fdisk output, like this
```

title Microsoft Windows XP Home
root (hd0,1)
savedefault
makeactive
chainloader +1
```

grub counts from 0 so the first hard drive would be sda (0) and its on partition 2 (1)

I just tried editing the drive to "root (hd0,1) and ended up with the following error at boot:

Error 12: Invalid Device Requested


With my limited understanding of Grub, I thought my windows partition "sda5" would be "(hd0,4)" in Grub (counting from zero). I've tried that already and get the same error as above.

It seems like it should work because fdisk - l list the NTFS partition as:

/dev/sda5 4028 4680 5245191 7 HPFS/NTFS

The setting of it to (hd1,0) in the menu.lst was just a shot in the dark, hoping the partitioning might have gone a little screwy.

Gladly willing to try anything else.

---

### Post by caljohnsmith on 2008-12-17
So is Windows in sda5? If that's true, you are trying to boot Windows from a logical partition, which takes a bit of work. In order to get a clearer picture of your setup, how about downloading the attached "boot_info9.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info9.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what it might take to get Windows booting from the sda5 logical partition.

---

### Post by halitech on 2008-12-17
well, I was looking at this
```
/dev/sda2 * 3856 4680 6626812+ f W95 Ext'd (LBA)
```
the * indicates it is a bootable drive

---

### Post by bumblestiltskin on 2008-12-17
> **caljohnsmith said:**
> So is Windows in sda5? If that's true, you are trying to boot Windows from a logical partition, which takes a bit of work. In order to get a clearer picture of your setup, how about downloading the attached "boot_info9.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info9.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what it might take to get Windows booting from the sda5 logical partition.

Yes, Windows should be on sda5. This is where I get a little lost on partitioning. I understand that there are primary and logical partitions. The way I understand it is a primary partition is like its own entity and the logical is sort of like a child of the primary. And I think that's about as much as I understand.

Reading through posts here and elsewhere, I read mention of moving a partition from one place to another, but felt really unsure about how to accomplish such a thing.

Anyway, here is the output the script:

```
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #1 for its boot files.

sda1:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sda2:
    File system:  
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda5:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda5 starts at sector 63
    Operating System: XP
    Boot files/directories present: 

sda6:
    File system:  swap
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 


Disk /dev/sda: 38.5 GB, 38502535680 bytes
255 heads, 63 sectors/track, 4681 cylinders, total 75200265 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1640163f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    61930574    30965256   83  Linux
/dev/sda2   *    61930575    75184199     6626812+   f  W95 Ext'd (LBA)
/dev/sda5        64693818    75184199     5245191    7  HPFS/NTFS
/dev/sda6        61930701    64693754     1381527   82  Linux swap / Solaris

Partition table entries are not in disk order
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 61930512, Id=83
/dev/sda2 : start= 61930575, size= 13253625, Id= f, bootable
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 64693818, size= 10490382, Id= 7
/dev/sda6 : start= 61930701, size=  2763054, Id=82

sda1/boot/grub/menu.lst

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
# kopt=root=UUID=b383cfb8-6aff-4c49-a94f-ee2a538d87c7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b383cfb8-6aff-4c49-a94f-ee2a538d87c7

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
uuid		b383cfb8-6aff-4c49-a94f-ee2a538d87c7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b383cfb8-6aff-4c49-a94f-ee2a538d87c7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		b383cfb8-6aff-4c49-a94f-ee2a538d87c7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b383cfb8-6aff-4c49-a94f-ee2a538d87c7 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b383cfb8-6aff-4c49-a94f-ee2a538d87c7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b383cfb8-6aff-4c49-a94f-ee2a538d87c7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b383cfb8-6aff-4c49-a94f-ee2a538d87c7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b383cfb8-6aff-4c49-a94f-ee2a538d87c7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b383cfb8-6aff-4c49-a94f-ee2a538d87c7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP Home
root (hd0,1)
savedefault
makeactive
chainloader +1

sda1/boot

total 23780
drwxr-xr-x  3 root root    4096 2008-12-16 08:10 .
drwxr-xr-x 19 root root    4096 2008-12-13 02:08 ..
-rw-r--r--  1 root root  507665 2008-11-04 13:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 15:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 13:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 15:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-17 15:58 grub
-rw-r--r--  1 root root 8190686 2008-12-12 22:11 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8191110 2008-12-16 08:10 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 13:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 13:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 15:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 13:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 15:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 13:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 15:46 vmlinuz-2.6.27-9-generic

sda1/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-17 15:58 .
drwxr-xr-x 3 root root   4096 2008-12-16 08:10 ..
-rw-r--r-- 1 root root    197 2008-12-12 12:32 default
-rw-r--r-- 1 root root     15 2008-12-12 12:32 device.map
-rw-r--r-- 1 root root   8108 2008-12-12 12:32 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-12 12:32 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-12 12:32 installed-version
-rw-r--r-- 1 root root   8712 2008-12-12 12:32 jfs_stage1_5
-rw-r--r-- 1 root root   4876 2008-12-17 15:58 menu.lst
-rw-r--r-- 1 root root   4876 2008-12-13 01:15 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-12 12:32 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-12 12:32 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-12 12:32 stage1
-rw-r--r-- 1 root root 121460 2008-12-12 12:32 stage2
-rw-r--r-- 1 root root   9556 2008-12-12 12:32 xfs_stage1_5

StdErr Messages 

ls: cannot access /dev/hd?: No such file or directory
ls: cannot access /dev/hd??*: No such file or directory
mount: you must specify the filesystem type
/dev/sda2: unknown volume type
umount: sda2: not mounted
/dev/sda6 looks like swapspace - not mounted
mount: you must specify the filesystem type
umount: sda6: not mounted
```

---

### Post by caljohnsmith on 2008-12-17
OK, as I suspected, your Windows partition is unfortunately missing its three necessary boot files according to that script you ran; I've attached the files you need to this post and also configured the boot.ini file so it should work with your particular setup. How about downloading the attached "WinXP_boot_files2.zip" to your desktop, and then do:
```
sudo mount /dev/sda5 /mnt
cd ~/Desktop
unzip WinXP_boot_files2.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Next open up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom, change your Windows entry to be:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
And lastly, you definitely need to fix your Windows boot sector, because it currently shows that the XP partition starts at sector 63 when actually your XP partition starts at sector 64693818. So first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows sda5 partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot, select Windows from your Grub menu, and let me know exactly what happens. We can work from there. :)

---

### Post by bumblestiltskin on 2008-12-17
> **caljohnsmith said:**
> ...if testdisk gives you a warning that the "sectors are not identical", then choose "write".

I get the message: "Extrapolated boot sector and current boot sector are different." Would I choose "write"?

---

### Post by caljohnsmith on 2008-12-17
My mistake, I typed out the directions too fast and my brain was obviously 404. I corrected the mistake, please try again. :)

---

### Post by bumblestiltskin on 2008-12-17
> **caljohnsmith said:**
> My mistake, I typed out the directions too fast and my brain was obviously 404. I corrected the mistake, please try again. :)

^^I think you're referring to the sda6 vs. sda5, which I figured was the case.


In Testdisk I get this message:

"Extrapolated boot sector and current boot sector are different." 

Would I choose "write"?

---

### Post by caljohnsmith on 2008-12-17
Yes, choose to write the new boot sector.

---

### Post by bumblestiltskin on 2008-12-17
SUCCESS! SUCCESS! SUCCESS!

Had a bit of a DOH! moment in the process. I was helping my son with his homework and failed to save the changes the menu.lst file. After repasting the correct info and SAVING, it boots like a dream.

Thanks so much! I don't need Windows for much anymore, but I do need it for some things. This will let me make Ubuntu my main desktop and only use Windows for the about three programs when I absolutely have to have them.

:p:p:p:p:p:p

---

### Post by gb5757870 on 2008-12-28
Hi,

I'm having very similar problems. My Bootinfo.txt is below, do you think I also need to replace those missing Windows files?

-----------------------------------
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #4 for its boot files.

sda2:
    File system:  vfat
    Boot sector  type:  XP
    Boot sector  info:  
    Operating System: 
    Boot files/directories present:  /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda3:
    File system:  swap
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda4:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sda5:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda5 starts at sector 63
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTDETECT.COM


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e4c2e4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       16065    61432559    30708247+   f  W95 Ext'd (LBA)
/dev/sda2        61432560   256750829    97659135    b  W95 FAT32
/dev/sda3       256750830   258742889      996030   82  Linux swap / Solaris
/dev/sda4       258742890   312576704    26916907+  83  Linux
/dev/sda5           16128    40976144    20480008+   7  HPFS/NTFS
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=    16065, size= 61416495, Id= f, bootable
/dev/sda2 : start= 61432560, size=195318270, Id= b
/dev/sda3 : start=256750830, size=  1992060, Id=82
/dev/sda4 : start=258742890, size= 53833815, Id=83
/dev/sda5 : start=    16128, size= 40960017, Id= 7

sda2/boot.ini

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\="Unidentified operating system on drive D." 


sda4/boot/grub/menu.lst

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
default		10

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
# kopt=root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


sda4/boot

total 90108
drwxr-xr-x  3 root root    4096 2008-12-25 14:03 .
drwxr-xr-x 21 root root    4096 2008-12-03 19:20 ..
-rw-r--r--  1 root root  422607 2008-04-11 04:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  422667 2008-05-02 05:59 abi-2.6.24-17-generic
-rw-r--r--  1 root root  422667 2008-08-21 16:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-10-22 16:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  422838 2008-11-25 11:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   79964 2008-04-11 04:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   80071 2008-05-02 05:59 config-2.6.24-17-generic
-rw-r--r--  1 root root   80049 2008-08-21 16:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-10-22 16:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   80062 2008-11-25 11:47 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 2008-12-03 19:20 grub
-rw-r--r--  1 root root 7458522 2008-04-27 21:54 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7885123 2008-04-28 18:19 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7460107 2008-06-01 18:09 initrd.img-2.6.24-17-generic
-rw-r--r--  1 root root 7459977 2008-06-01 18:08 initrd.img-2.6.24-17-generic.bak
-rw-r--r--  1 root root 7498407 2008-08-26 21:55 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7497490 2008-08-17 12:15 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7499445 2008-11-09 15:56 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7499395 2008-11-02 12:10 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7499466 2008-12-25 14:03 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7498703 2008-12-03 19:20 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 22:06 memtest86+.bin
-rw-r--r--  1 root root  899892 2008-04-11 04:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root  905012 2008-05-02 05:59 System.map-2.6.24-17-generic
-rw-r--r--  1 root root  905170 2008-08-21 16:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-10-22 16:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  905617 2008-11-25 11:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1904248 2008-04-11 04:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1921944 2008-05-02 05:59 vmlinuz-2.6.24-17-generic
-rw-r--r--  1 root root 1921464 2008-08-21 16:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1920760 2008-10-22 16:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1921176 2008-11-25 11:47 vmlinuz-2.6.24-22-generic

sda4/boot/grub

total 212
drwxr-xr-x 2 root root   4096 2008-12-03 19:20 .
drwxr-xr-x 3 root root   4096 2008-12-25 14:03 ..
-rw-r--r-- 1 root root    197 2008-04-28 18:19 default
-rw-r--r-- 1 root root     15 2008-04-28 18:19 device.map
-rw-r--r-- 1 root root   8056 2008-04-28 18:19 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-04-28 18:19 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-04-28 18:19 installed-version
-rw-r--r-- 1 root root   8608 2008-04-28 18:19 jfs_stage1_5
-rw-r--r-- 1 root root   6311 2008-12-03 19:20 menu.lst
-rw-r--r-- 1 root root   5879 2008-12-03 19:20 menu.lst~
-rw-r--r-- 1 root root   7324 2008-04-28 18:19 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-04-28 18:19 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-04-28 18:19 stage1
-rw-r--r-- 1 root root 108356 2008-04-28 18:19 stage2
-rw-r--r-- 1 root root   9276 2008-04-28 18:19 xfs_stage1_5

sda5/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


StdErr Messages 

ls: cannot access /dev/hd?: No such file or directory
ls: cannot access /dev/hd??*: No such file or directory
/dev/sda3 looks like swapspace - not mounted
mount: you must specify the filesystem type
umount: sda3: not mounted

---

### Post by caljohnsmith on 2008-12-28
Gb5757870, it looks like you should be able to boot Windows in your current configuration if you do a simple change to your Grub's menu.lst. How about opening your menu.lst first:
```
gksudo gedit /boot/grub/menu.lst
```
And then at the bottom, change your Windows entry to be:
```
title Microsoft Windows XP Home Edition
root [COLOR="Blue"](hd0,1)[/COLOR]
savedefault
makeactive
chainloader +1
```
Then reboot, and let me know exactly what happens when you try to boot Windows from your Grub menu. We can work from there.

---

### Post by gb5757870 on 2008-12-28
> **caljohnsmith said:**
> Gb5757870, it looks like you should be able to boot Windows in your current configuration if you do a simple change to your Grub's menu.lst. How about opening your menu.lst first:
```
gksudo gedit /boot/grub/menu.lst
```
And then at the bottom, change your Windows entry to be:
```
title Microsoft Windows XP Home Edition
root [COLOR="Blue"](hd0,1)[/COLOR]
savedefault
makeactive
chainloader +1
```
Then reboot, and let me know exactly what happens when you try to boot Windows from your Grub menu. We can work from there.

Well strangely, after changing to what you recommended, the message changed to "Starting Up...." in the top left corner and nothing happens beyond that.

UPDATE: The quick background to this whole issue is that my plan was re-install XP as about time I did and also replace current Hardy with Intrepid. As a test, I actually restored another image of XP over the same partition but same problem. Further, I have also tried doing a complete re-install of XP from the CD and pretty much same error (I say pretty much 'cos initially doesn't boot to anything, but restored grub through live CD)

---

### Post by caljohnsmith on 2008-12-29
> **gb5757870 said:**
> Well strangely, after changing to what you recommended, the message changed to "Starting Up...." in the top left corner and nothing happens beyond that.

UPDATE: The quick background to this whole issue is that my plan was re-install XP as about time I did and also replace current Hardy with Intrepid. As a test, I actually restored another image of XP over the same partition but same problem. Further, I have also tried doing a complete re-install of XP from the CD and pretty much same error (I say pretty much 'cos initially doesn't boot to anything, but restored grub through live CD)
OK, so when you did a complete reinstall of XP, the installation completed successfully, and yet Windows wouldn't boot after that? Do you get any error messages? Am I right to assume your Windows was previously working though at some point before all this happened? If that's true, what happened with your setup between the time Windows was working and now that it won't boot? Now that you've reinstalled Windows, it would help if I could see the output of the boot_info_script.txt again if you don't mind posting it.

---

### Post by gb5757870 on 2008-12-29
> **caljohnsmith said:**
> OK, so when you did a complete reinstall of XP, the installation completed successfully, and yet Windows wouldn't boot after that? Do you get any error messages? Am I right to assume your Windows was previously working though at some point before all this happened? If that's true, what happened with your setup between the time Windows was working and now that it won't boot? Now that you've reinstalled Windows, it would help if I could see the output of the boot_info_script.txt again if you don't mind posting it.

Sorry I didn't provide an accurate timeline of what happened. I hadn't used XP for a while and I wanted to do a re-install of XP and replace Hardy with Intrepid. So I booted to the XP CD and selected to install a new copy of XP and since then have had these problems. I did the exact same procedure (re-installed XP first, then installed Intrepid) on my laptop and worked with no problems.


-----------------------------------

_Bootinfo.txt_
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #4 for its boot files.
No known boot loader is installed in the MBR of /dev/sdb

sda1:
    File system:  
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda2:
    File system:  vfat
    Boot sector  type:  XP
    Boot sector  info:  
    Operating System: 
    Boot files/directories present:  /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda3:
    File system:  swap
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda4:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sda5:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda5 starts at sector 63
    Operating System: 
    Boot files/directories present: 

sdb1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sdb1 starts at sector 63
    Operating System: 
    Boot files/directories present: 


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e4c2e4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065    61432559    30708247+   f  W95 Ext'd (LBA)
/dev/sda2   *    61432560   256750829    97659135    b  W95 FAT32
/dev/sda3       256750830   258742889      996030   82  Linux swap / Solaris
/dev/sda4       258742890   312576704    26916907+  83  Linux
/dev/sda5           16128    61432559    30708216    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
15 heads, 63 sectors/track, 1033622 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x069764b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001    7  HPFS/NTFS
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=    16065, size= 61416495, Id= f
/dev/sda2 : start= 61432560, size=195318270, Id= b, bootable
/dev/sda3 : start=256750830, size=  1992060, Id=82
/dev/sda4 : start=258742890, size= 53833815, Id=83
/dev/sda5 : start=    16128, size= 61416432, Id= 7
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=976768002, Id= 7, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

sda2/boot.ini

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect

C:\="Unidentified operating system on drive D." 


sda4/boot/grub/menu.lst

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
default		10

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
# kopt=root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=02b2c960-eec1-4630-95c9-7145eb951c58 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


sda4/boot

total 90108
drwxr-xr-x  3 root root    4096 2008-12-25 14:03 .
drwxr-xr-x 21 root root    4096 2008-12-03 19:20 ..
-rw-r--r--  1 root root  422607 2008-04-11 04:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  422667 2008-05-02 05:59 abi-2.6.24-17-generic
-rw-r--r--  1 root root  422667 2008-08-21 16:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-10-22 16:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  422838 2008-11-25 11:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   79964 2008-04-11 04:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   80071 2008-05-02 05:59 config-2.6.24-17-generic
-rw-r--r--  1 root root   80049 2008-08-21 16:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-10-22 16:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   80062 2008-11-25 11:47 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 2008-12-29 16:20 grub
-rw-r--r--  1 root root 7458522 2008-04-27 21:54 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7885123 2008-04-28 18:19 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7460107 2008-06-01 18:09 initrd.img-2.6.24-17-generic
-rw-r--r--  1 root root 7459977 2008-06-01 18:08 initrd.img-2.6.24-17-generic.bak
-rw-r--r--  1 root root 7498407 2008-08-26 21:55 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7497490 2008-08-17 12:15 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7499445 2008-11-09 15:56 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7499395 2008-11-02 12:10 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7499466 2008-12-25 14:03 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7498703 2008-12-03 19:20 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 22:06 memtest86+.bin
-rw-r--r--  1 root root  899892 2008-04-11 04:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root  905012 2008-05-02 05:59 System.map-2.6.24-17-generic
-rw-r--r--  1 root root  905170 2008-08-21 16:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-10-22 16:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  905617 2008-11-25 11:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1904248 2008-04-11 04:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1921944 2008-05-02 05:59 vmlinuz-2.6.24-17-generic
-rw-r--r--  1 root root 1921464 2008-08-21 16:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1920760 2008-10-22 16:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1921176 2008-11-25 11:47 vmlinuz-2.6.24-22-generic

sda4/boot/grub

total 220
drwxr-xr-x 2 root root   4096 2008-12-29 16:20 .
drwxr-xr-x 3 root root   4096 2008-12-25 14:03 ..
-rw-r--r-- 1 root root    197 2008-04-28 18:19 default
-rw-r--r-- 1 root root     15 2008-04-28 18:19 device.map
-rw-r--r-- 1 root root   8056 2008-04-28 18:19 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-04-28 18:19 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-04-28 18:19 installed-version
-rw-r--r-- 1 root root   8608 2008-04-28 18:19 jfs_stage1_5
-rw-r--r-- 1 root root   6311 2008-12-03 19:20 menu (copy).lst
-rw-r--r-- 1 root root   6311 2008-12-29 16:20 menu.lst
-rw-r--r-- 1 root root   6311 2008-12-28 23:22 menu.lst~
-rw-r--r-- 1 root root   7324 2008-04-28 18:19 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-04-28 18:19 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-04-28 18:19 stage1
-rw-r--r-- 1 root root 108356 2008-04-28 18:19 stage2
-rw-r--r-- 1 root root   9276 2008-04-28 18:19 xfs_stage1_5

StdErr Messages 

ls: cannot access /dev/hd?: No such file or directory
ls: cannot access /dev/hd??*: No such file or directory
mount: you must specify the filesystem type
/dev/sda1: unknown volume type
umount: sda1: not mounted
/dev/sda3 looks like swapspace - not mounted
mount: you must specify the filesystem type
umount: sda3: not mounted

---

### Post by caljohnsmith on 2008-12-29
OK, thanks for clarifying that about your XP install. I notice though that XP is installed on sda5, which is a logical partition, while XP's boot files are in the sda2 FAT primary partition. I doubt it will make a lot of difference, but have you tried to install Windows to just the sda2 primary partition? If you decide to try that, I would reformat sda2 to be NTFS instead of FAT. But anyway, it sounds like you have a Windows problem and not a Grub problem at this point, so if you can't get Windows to boot immediately after you install it (before you reinstall Grub to the MBR), then that is not something that tweaking Grub can fix. Good luck and let me know how it goes.

---

### Post by gb5757870 on 2008-12-30
Thanks. I wasn't sure it was grub related but thought the whole thing rather bizarre and thought maybe it was 'cos of grub. sda2 is a fat32 partition so that it can be shared/written to by either XP or Ubuntu. Made it such so that  That's historical as now is easier write to ntfs in Linux. 

So now I'm installing Intrepid anyway and keeping my shared FAT32 partition but if the problem remains, I'm gonna just blow the whole thing away and start from the beginning. If that doesn't work, I'll just replace the whole thing with OS2

---

### Post by gb5757870 on 2008-12-31
caljohnsmith, I think you were on the money when you pointed out the the boot files were on the partition while the XP files on a different partition. In the end I blew away every partition (after backing up)and installed XP from scratch which worked first time.

That was kinda weird, as essentially what happened was when initially tried to re-install XP and it appears on all subsequent attempts, the install software kept marking the fat partition as bootable when in fact it wasnt....or something like that.

Thanks again for yer help

GB

---

### Post by caljohnsmith on 2008-12-31
> **gb5757870 said:**
> caljohnsmith, I think you were on the money when you pointed out the the boot files were on the partition while the XP files on a different partition. In the end I blew away every partition (after backing up)and installed XP from scratch which worked first time.

That was kinda weird, as essentially what happened was when initially tried to re-install XP and it appears on all subsequent attempts, the install software kept marking the fat partition as bootable when in fact it wasnt....or something like that.

Thanks again for yer help

GB
Glad to hear you finally got it working OK. About Windows marking your FAT partition bootable, what happens is when you install Windows to a logical partition, Windows has to put its boot files in a primary partition in order to boot because the Windows boot loader can't boot a logical partition directly. So actually it was normal that Windows marked your FAT partition as the bootable partition, since that was the primary partition where Windows stuck its boot files. Anyway, cheers and have fun with your OSes. :)

---


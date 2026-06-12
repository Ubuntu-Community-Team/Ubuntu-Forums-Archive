---
title: "Adding XP to grub"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by corruptzoidberg on 2008-12-31
Hey all,

I just installed Kubuntu to a partition to my 160GB hard drive on my laptop. Now I cannot select to boot into XP. I tried adding it to grub myself but had no luck. Here's my sudo fdisk -l list. 

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+   6  FAT16
/dev/sda2              15       15148   121563855    f  W95 Ext'd (LBA)
/dev/sda3   *       15149       15540     3148740   db  CP/M / CTOS / ...
/dev/sda4           15541       19457    31463302+  83  Linux
/dev/sda5              15       15148   121563823+   7  HPFS/NTFS
```

Can anyone help me? Thank you

EDIT - Forgot to mention that xp is on the partition with 120GB

---

### Post by Paqman on 2008-12-31
Can you post the contents of /boot/grub/menu.lst?

So, Windows was working fine from that partition before? Even buried within the extended partition?

---

### Post by mikewhatever on 2008-12-31
Is XP on sda5 NTFS? It seems to be an extended partition, did you have other Windows installations on that HDD?

---

### Post by corruptzoidberg on 2008-12-31
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ac2e0b61-50d9-48c9-9697-484d18e660b0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac2e0b61-50d9-48c9-9697-484d18e660b0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ac2e0b61-50d9-48c9-9697-484d18e660b0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac2e0b61-50d9-48c9-9697-484d18e660b0 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ac2e0b61-50d9-48c9-9697-484d18e660b0
kernel		/boot/memtest86+.bin
quiet
```

Is that what you're after?

OK this is a bit hard to explain hehe. Before the kubuntu installation I had Vista on my C drive (40GB) and XP on my E drive (120GB). There was another partition my Dell laptop came with, I believe it was the D drive with a few recovery files on it.

I'm not sure what an sda5 NTFS is. :s 

Thank you for the replies

---

### Post by mikewhatever on 2008-12-31
You posted a little part of the menu.lst which isn't useful. Is there an entry for Windows there? Can you check what's on sda5 from Kubuntu.

The deal with Windows is that it can't boot from a non-primary partition. Since yours seems to be on an extended one, it must have had its boot loader files on c:\. The question is, where is C:\ now, what did you do with Vista?

---

### Post by corruptzoidberg on 2008-12-31
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
# kopt=root=UUID=ac2e0b61-50d9-48c9-9697-484d18e660b0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ac2e0b61-50d9-48c9-9697-484d18e660b0

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
uuid		ac2e0b61-50d9-48c9-9697-484d18e660b0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac2e0b61-50d9-48c9-9697-484d18e660b0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ac2e0b61-50d9-48c9-9697-484d18e660b0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac2e0b61-50d9-48c9-9697-484d18e660b0 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ac2e0b61-50d9-48c9-9697-484d18e660b0
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

```

Thats the whole file. Kubuntu is now sitting where Vista used to be.

---

### Post by Lone_Joker on 2008-12-31
> **corruptzoidberg said:**
> 
Thats the whole file. Kubuntu is now sitting where Vista used to be.
Ehh.. if it is where Vista used to be that means you got rid of Vista. I'm not sure if that's what you meant to do but, whatever. 

Also I think you want to add something like this, I'm not sure though. You might want to wait for someone else to confirm this.
```
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

You might have to change (hd0,0) to something else though.

---

### Post by Paqman on 2008-12-31
> **Lone_Joker said:**
> 
You might have to change (hd0,0) to something else though.

Sda5 would be (hd0,4)

---

### Post by corruptzoidberg on 2008-12-31
OK I added that and replaced hd0,0 with hd0,4 but got the error:

Error 12: Invalid device requested :s

---

### Post by Paqman on 2008-12-31
> **corruptzoidberg said:**
> OK I added that and replaced hd0,0 with hd0,4 but got the error:

Error 12: Invalid device requested :s

[To be expected]("http://users.bigpond.net.au/hermanzone/p15.htm#12_"), i'm afraid.

---

### Post by corruptzoidberg on 2008-12-31
haha I thought it might of come to that. I think tomorrow I'm just going to wipe everything clean and do it properly. 

Thanks for the help everyone. I can still see the files I had in XP through the dolphin file manager so nothings lost. :D

---

### Post by caljohnsmith on 2009-01-01
> **corruptzoidberg said:**
> haha I thought it might of come to that. I think tomorrow I'm just going to wipe everything clean and do it properly. 

Thanks for the help everyone. I can still see the files I had in XP through the dolphin file manager so nothings lost. :D
I doubt it is necessary to reinstall everything just to get XP to boot, so if you want a little help, how about opening a Konsole and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.

---

### Post by corruptzoidberg on 2009-01-01
```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for its boot files.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      224909      112423+   6  FAT16
/dev/sda2          224910   243352619   121563855    f  W95 Ext'd (LBA)
/dev/sda3   *   243352620   249650099     3148740   db  CP/M / CTOS / ...
/dev/sda4       249650100   312576704    31463302+  83  Linux
/dev/sda5          224973   243352619   121563823+   7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0A1E" TYPE="vfat" 
/dev/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sda4: UUID="ac2e0b61-50d9-48c9-9697-484d18e660b0" TYPE="ext3" 
/dev/sda5: UUID="220836B508368835" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw,relatime,errors=remount-ro)
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

=========================== sda4/boot/grub/menu.lst: ===========================

hiddenmenu
default 0
timeout 3

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
# kopt=root=UUID=ac2e0b61-50d9-48c9-9697-484d18e660b0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ac2e0b61-50d9-48c9-9697-484d18e660b0

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

title Ubuntu 8.10, kernel 2.6.27-9-generic
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=ac2e0b61-50d9-48c9-9697-484d18e660b0 ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=ac2e0b61-50d9-48c9-9697-484d18e660b0 ro  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=ac2e0b61-50d9-48c9-9697-484d18e660b0 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=ac2e0b61-50d9-48c9-9697-484d18e660b0 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=ac2e0b61-50d9-48c9-9697-484d18e660b0 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda4/boot: ==================================

total 23764
drwxr-xr-x  3 root root    4096 2009-01-01 03:51 .
drwxr-xr-x 20 root root    4096 2009-01-01 03:50 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-01 04:36 grub
-rw-r--r--  1 root root 8181429 2009-01-01 03:49 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8181061 2009-01-01 03:51 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sda4/boot/grub: ===============================

total 228
drwxr-xr-x 2 root root   4096 2009-01-01 04:36 .
drwxr-xr-x 3 root root   4096 2009-01-01 03:51 ..
-rw-r--r-- 1 root root    197 2009-01-01 01:29 default
-rw-r--r-- 1 root root     15 2009-01-01 01:29 device.map
-rw-r--r-- 1 root root   8108 2009-01-01 01:29 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-01 01:29 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-01 01:29 installed-version
-rw-r--r-- 1 root root   8712 2009-01-01 01:29 jfs_stage1_5
-rw-r--r-- 1 root root   3141 2009-01-01 15:30 menu.lst
-rw-r--r-- 1 root root   4896 2009-01-01 04:36 menu.lst~
-rw-r--r-- 1 root root   4370 2009-01-01 03:34 menu.lst_original
-rw-r--r-- 1 root root   7352 2009-01-01 01:29 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-01 01:29 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-01 01:29 stage1
-rw-r--r-- 1 root root 121460 2009-01-01 01:29 stage2
-rw-r--r-- 1 root root   9556 2009-01-01 01:29 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

```

Thank you for the quick reply. I was just about to wipe everything out. :D

---

### Post by caljohnsmith on 2009-01-01
OK, thanks for posting that output, it helps clarify your setup; it looks like what happened is that you installed Windows XP to a logical partition (sda5), and that means Windows would have put its boot files on some primary NTFS/FAT partition. But neither of your two FAT partitions (sda1 or sda3) have your Windows boot files according to the script, so I suspect you might have deleted them at some point since you might not have known what they were for. But anyway, it is fixable at least. The other problem is that your Windows XP boot sector incorrectly shows the starting point of the sda5 partition is at sector 63, when really your Windows sda5 partition starts at sector 224973 according to fdisk. So to correct that problem first, how about making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the sda5 Windows partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write".

To save you the hassle of digging the necessary XP boot files off your XP Install CD, I've attached the three necessary boot files that you need to this post and also configured the "boot.ini" file so that it should work with your setup. How about downloading the attached "WinXP_boot_files4.zip" to your Ubuntu desktop and do:
```

sudo mount /dev/sda5 /mnt
cd ~/Desktop
unzip WinXP_boot_files4.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
And lastly, open up your menu.lst:
```
kdesu kate /boot/grub/menu.lst
```
And add at the very bottom:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
Reboot, select Windows XP from your Grub menu, and let me know exactly what happens. We can work from there. :)

---

### Post by corruptzoidberg on 2009-01-01
Yay it works. Thank you for the step by step guide. :popcorn:

---

### Post by caljohnsmith on 2009-01-01
Glad to hear that did the trick so you didn't have to reinstall after all; cheers and Happy New Year. :)

---

### Post by mikewhatever on 2009-01-01
Really impressive. =D>

---

### Post by Paqman on 2009-01-02
> **mikewhatever said:**
> Really impressive. =D>

Ditto. Nice one caljohnsmith! 8-)

---


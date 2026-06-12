---
title: "[SOLVED] New windows+ubuntu installation Grub problem"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Dr.Fritz on 2008-12-27
Hello guys, i 've installed windows xp and after that ubuntu several times in friend's computers and i have also experimented with mine with some distros as well. BTW my linux(ubuntu actually) experience is almost 6 months..

anyways.. my brothers computer has 2 sata drives and an old ide(which i thing is the problem) 

in the hdd priorities i put sata first in BIOS and partitioned a sata drive(75gb total) 44gb for windows 30gb for ubuntu and 1gb for the swap 
i installed windows and after that ubuntu and i was expecting that ubuntu(as usual) would detect windows, but what happened is when i boot the pc i dont see any grub screen at all and windows loads..
 
so i booted the livecd again and tried to do the usual grub configuration (that is in many howtos for ubuntu installed first and winxp overwriting the mbr) 
i set it up restart my pc and nothing changed

any (easy) way i can fix this?
thanks :)

---

### Post by anewguy on 2008-12-27
Please post back the output of:

fdisk -l (that's lower case "L" not a one)

Dave :)

---

### Post by Dr.Fritz on 2008-12-27
thanks for your reply :) here goes the output:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8339a08d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f5d9f5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3853    30949191   83  Linux
/dev/sdb2            3854        3980     1020127+  82  Linux swap / Solaris
/dev/sdb3            3981        9729    46178842+   7  HPFS/NTFS

Disk /dev/sdc: 30.6 GB, 30616363008 bytes
255 heads, 63 sectors/track, 3722 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01a41600

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3722    29896933+   7  HPFS/NTFS

```

---

### Post by anewguy on 2008-12-27
I see a few things to question:

(1) It appears as if your main drive is 500gb.  did you have Windows installed and booting from this driver as well?


(2) When Windows comes up and you go into Windows Explorer, what do you show for disk drives?  Looks like you should show 3.  Tell me the size of each drive by drive letter.

(3) Linux is installed to your 2nd hard drive.  Is this your boot drive?

Also - what is the boot order?  Drive 1 first, I assume?

Thanks
Dave :)

---

### Post by Dr.Fritz on 2008-12-27
1: well, actually my main drive should be the second one where the o/s are , and the 500gb one is just storage,but i think that if i put the second one appear as first in the BIOS no o/s boots at all, what is the "correct" order i should put them? (if there is any)

2: exactly, 3 drives:
   C: 28,5 GB (IDE one)
   D: 44 GB (windows installed on this one)
   E: 465 GB (data)

3: actually i dont know.. the BIOS device priority is as shown in fstab (maybe i should change it, i played around with it a bit and this way i can at least boot into windows) in grub when i enter find /boot/grub/stage1 the output is root hd(1,0)

hope i answered everything properly :) thanks alot again

---

### Post by bumanie on 2008-12-27
Please post the ouput of > cat /boot/grub/menu.lst and > sudo grub > find /boot/grub/stage1
sudo grub won't give an output, it gets you to the grub shell

---

### Post by caljohnsmith on 2008-12-27
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your booting problem might be.

---

### Post by Dr.Fritz on 2008-12-27
Results.txt :
```
============================= Boot Info Summary: ==============================

Grub is installed in the MBR of /dev/sda and looks on boot drive #2 in 
partition #1 for its boot files.
Windows is installed in the MBR of /dev/sdb
Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed to the boot sector of /dev/sdb1 and 
                       looks at sector 30396223 of the same hard drive for 
                       the stage2 file (a stage2 file is at this location on 
                       /dev/sdb) and on partition #1 for menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       swap

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 63938700.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8339a08d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976768064   488384001    7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9f5d9f5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    61898444    30949191   83  Linux
/dev/sdb2        61898445    63938699     1020127+  82  Linux swap / Solaris
/dev/sdb3        63938700   156296384    46178842+   7  HPFS/NTFS

sfdisk -V /dev/sdb:

/dev/sda: OK
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 30.6 GB, 30616363008 bytes
255 heads, 63 sectors/track, 3722 cylinders, total 59797584 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01a41600

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    59793929    29896933+   7  HPFS/NTFS

sfdisk -V /dev/sdc:

/dev/sda: OK
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK
/dev/sdc: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="14A0BAA30A8F5601" LABEL="data" TYPE="ntfs" 
/dev/sdb1: UUID="70d72429-05ef-4119-bb2a-8555ffb7432b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: TYPE="swap" UUID="93607b2a-13d3-49ff-9a18-3537e19209cf" 
/dev/sdb3: UUID="F650EE8A50EE50C3" TYPE="ntfs" 
/dev/sdc1: UUID="292D046F0D55FFAF" LABEL="Data2" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

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
# kopt=root=UUID=70d72429-05ef-4119-bb2a-8555ffb7432b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=70d72429-05ef-4119-bb2a-8555ffb7432b

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
uuid		70d72429-05ef-4119-bb2a-8555ffb7432b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=70d72429-05ef-4119-bb2a-8555ffb7432b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		70d72429-05ef-4119-bb2a-8555ffb7432b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=70d72429-05ef-4119-bb2a-8555ffb7432b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		70d72429-05ef-4119-bb2a-8555ffb7432b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=70d72429-05ef-4119-bb2a-8555ffb7432b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=93607b2a-13d3-49ff-9a18-3537e19209cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 14364
drwxr-xr-x  3 root root     4096 2008-12-27 03:17 .
drwxr-xr-x 22 root root     4096 2008-12-27 03:17 ..
-rw-r--r--  1 root root   503560 2008-11-04 20:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root    85316 2008-11-04 20:53 config-2.6.27-7-generic
drwxr-xr-x  3 root root     4096 2008-12-27 03:17 grub
-rw-r--r--  1 root root 10237960 2008-12-27 03:17 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root   124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root  1352144 2008-11-04 20:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root     1130 2008-11-04 20:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root  2339712 2008-10-24 07:55 vmlinuz-2.6.27-7-generic

=============================== sdb1/boot/grub: ===============================

total 220
drwxr-xr-x 3 root root   4096 2008-12-27 03:17 .
drwxr-xr-x 3 root root   4096 2008-12-27 03:17 ..
-rw-r--r-- 1 root root    197 2008-12-27 03:17 default
-rw-r--r-- 1 root root     45 2008-12-27 03:17 device.map
-rw-r--r-- 1 root root   8108 2008-12-27 03:17 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-27 03:17 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-27 03:17 installed-version
-rw-r--r-- 1 root root   8712 2008-12-27 03:17 jfs_stage1_5
-rw-r--r-- 1 root root   4655 2008-12-27 03:17 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-27 03:17 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-27 03:17 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-11-06 21:24 splashimages
-rw-r--r-- 1 root root    512 2008-12-27 03:17 stage1
-rw-r--r-- 1 root root 121460 2008-12-27 03:17 stage2
-rw-r--r-- 1 root root   9556 2008-12-27 03:17 xfs_stage1_5

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=============================== StdErr Messages: ===============================

No errors were reported.
```
@bumanie : sudo gedit /boot/grub/menu.lst gives me a blank file (obviously theres nothing there)
and find /boot/grub/stage1 gives (hd1,0) as i said before

Thanks alot for your help guys!

---

### Post by caljohnsmith on 2008-12-27
I see at least a few issues: first, even though your Windows is on sdb3, its boot files are instead located on sdc1. Also, you have Grub installed to the MBR of your sda drive, when it would be more ideal if you can install Grub to your Linux sdb drive since you can change your BIOS to boot that drive. So how about starting with:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
```
Then reboot, set your BIOS to boot your Ubuntu sdb drive, and you should get the Grub menu and be able to boot into Ubuntu. But booting Windows from your Grub menu only has a small chance of working, because the Windows could be on either of the two remaining boot drives, and your Windows boot.ini file may not be pointing to the correct drive either. But how about seeing if you can get Ubuntu booting first, or let me know if you run into problems. We can work from there. :)

---

### Post by bumanie on 2008-12-27
sudo gedit /boot/grub/menu.lst Sorry missed that you were running off a live cd that's why there was no output for that command - my apologies.

---

### Post by Dr.Fritz on 2008-12-27
hello caljonsmith i did what you suggested me to do and yes i can boot into ubuntu, and cant boot into windows (windows xp appear in grub menu though).

oh and sorry for the late reply i wasnt near a computer.

@bumanie no problem at all ( thanks for help in the first place) :)

---

### Post by caljohnsmith on 2008-12-27
OK, glad to hear you can boot Ubuntu at least; to get Windows booting OK, how about doing the following:
```
sudo mkdir /media/sdb3 /media/sdc1
sudo mount /dev/sdb3 /media/sdb3
sudo mount /dev/sdc1 /media/sdc1
sudo mv /media/sdc1/ntldr /media/sdc1/boot.ini /media/sdc1/NTDETECT.COM /media/sdb3
gksudo gedit /media/sdb3/boot.ini
```
And then change the boot.ini as highlighted in red below:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk[COLOR="Red"](0)[/COLOR]partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk[COLOR="Red"](0)[/COLOR]partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```
And then open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to:
```
title		Microsoft Windows XP Professional
root		(hd0,2)
chainloader	+1
```
Reboot, and let me know exactly what happens when you choose XP from your Grub menu; we can work from there.

---

### Post by Dr.Fritz on 2008-12-28
hello, i had a problem with X(blank white screen..) so i did a reinstall of ubuntu. 
Now, most of the commands return errors such as File doesnt exist etc..  moreover there is no boot.ini file in my windows drive :confused:

i was just thinking that a fresh install of windows would be simpler?(at least for me) or is there anywhere a ready boot.ini file we could use?

your help is really appreciated :) thanks alot :)

---

### Post by caljohnsmith on 2008-12-28
OK, how about running the script from post #7 again and post the output. We can work from there.

---

### Post by Dr.Fritz on 2008-12-28
sure, i should have thought it myself :P
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for its boot files.
 => Grub is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc2: _________________________________________________________________________

    File system:       swap

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc3 starts 
                       at sector 63938700.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 30.6 GB, 30616363008 bytes
255 heads, 63 sectors/track, 3722 cylinders, total 59797584 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01a41600

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    59793929    29896933+   7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8339a08d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001    7  HPFS/NTFS

sfdisk -V /dev/sdb:

/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9f5d9f5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    61898444    30949191   83  Linux
/dev/sdc2        61898445    63938699     1020127+  82  Linux swap / Solaris
/dev/sdc3        63938700   156296384    46178842+   7  HPFS/NTFS

sfdisk -V /dev/sdc:

/dev/sdc: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="292D046F0D55FFAF" LABEL="Data2" TYPE="ntfs" 
/dev/sdb1: UUID="14A0BAA30A8F5601" LABEL="data" TYPE="ntfs" 
/dev/sdc1: UUID="951dac7e-3442-456a-af93-7e0a09be7258" TYPE="ext3" 
/dev/sdc2: TYPE="swap" UUID="93607b2a-13d3-49ff-9a18-3537e19209cf" 
/dev/sdc3: UUID="F650EE8A50EE50C3" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/ektorandy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ektorandy)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=951dac7e-3442-456a-af93-7e0a09be7258 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=951dac7e-3442-456a-af93-7e0a09be7258

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
uuid		951dac7e-3442-456a-af93-7e0a09be7258
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=951dac7e-3442-456a-af93-7e0a09be7258 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		951dac7e-3442-456a-af93-7e0a09be7258
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=951dac7e-3442-456a-af93-7e0a09be7258 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		951dac7e-3442-456a-af93-7e0a09be7258
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=951dac7e-3442-456a-af93-7e0a09be7258 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		951dac7e-3442-456a-af93-7e0a09be7258
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=951dac7e-3442-456a-af93-7e0a09be7258 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		951dac7e-3442-456a-af93-7e0a09be7258
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=951dac7e-3442-456a-af93-7e0a09be7258 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=93607b2a-13d3-49ff-9a18-3537e19209cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdc1/boot: ==================================

total 25524
drwxr-xr-x  3 root root    4096 2008-12-28 13:55 .
drwxr-xr-x 20 root root    4096 2008-12-28 13:54 ..
-rw-r--r--  1 root root  503560 2008-11-04 22:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-21 01:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 22:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-21 01:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-28 13:54 grub
-rw-r--r--  1 root root 8668606 2008-12-28 13:54 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8669230 2008-12-28 13:55 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 23:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 22:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-21 01:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 22:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-21 01:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 22:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-21 01:30 vmlinuz-2.6.27-9-generic

=============================== sdc1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2008-12-28 13:54 .
drwxr-xr-x 3 root root   4096 2008-12-28 13:55 ..
-rw-r--r-- 1 root root    197 2008-12-28 13:32 default
-rw-r--r-- 1 root root     45 2008-12-28 13:32 device.map
-rw-r--r-- 1 root root   8108 2008-12-28 13:32 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-28 13:32 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-28 13:32 installed-version
-rw-r--r-- 1 root root   8712 2008-12-28 13:32 jfs_stage1_5
-rw-r--r-- 1 root root   5137 2008-12-28 13:54 menu.lst
-rw-r--r-- 1 root root   5053 2008-12-28 13:54 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-28 13:32 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-28 13:32 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-28 13:32 stage1
-rw-r--r-- 1 root root 121460 2008-12-28 13:32 stage2
-rw-r--r-- 1 root root   9556 2008-12-28 13:32 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2008-12-28
It looks like your drive letters might be changing. How about doing:
```
sudo mkdir /media/sdc3 /media/sda1
sudo mount /dev/sdc3 /media/sdc3
sudo mount /dev/sda1 /media/sda1
sudo mv /media/sda1/ntldr /media/sda1/boot.ini /media/sda1/NTDETECT.COM /media/sdc3
gksudo gedit /media/sdc3/boot.ini
```
And then continue with the directions in post #12 to modify your boot.ini file, and also to change your menu.lst. Let me know how it goes.

---

### Post by Dr.Fritz on 2008-12-28
Awesome! Grub is fixed and i can boot to windows perfectly ! :guitar:
thank you very very much :)

---

### Post by caljohnsmith on 2008-12-28
Glad to hear that worked OK; cheers and have fun with Windows and Ubuntu. :)

---


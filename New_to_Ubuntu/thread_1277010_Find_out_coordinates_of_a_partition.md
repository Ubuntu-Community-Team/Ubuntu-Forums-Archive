---
title: "Find out coordinates of a partition"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by homermarin on 2009-09-27
Good night,
I'd like to know how can I know to which "coordinates" a specific partition corresponds. This, in order to fix the booting so GRUB can recognize windows XP.
By coordinates I mean the famous "hd(x,y)"

thank u

---

### Post by presence1960 on 2009-09-27
(hdx,y)- the x = device and y = partition. Numbering for both starts at 0. But the x designation is determined by the order of hard disk boot in BIOS (because that is the actual order of the disks when you boot) not how fdisk reports the order. Example here is my fdisk output:
```
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85858585

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ea94ba9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13054   104856223+   7  HPFS/NTFS
/dev/sdb2           13055       60801   383527777+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02020202

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sdc2            5223        8094    23069340    5  Extended
/dev/sdc5            5223        5744     4192933+  82  Linux swap / Solaris
/dev/sdc6            5745        8094    18876343+  83  Linux
raz@raz-desktop:~$ 
```
sda1 is a ext 3 data partition
sdb1 is a NTFS data partition
sdb2 is for backups and images of my OSs and partitions
sdc1 is windows XP
sdc5 is swap
sdc6 is Ubuntu 9.04

My boot order in BIOS is sdc, sda, sdb. Since sdc is booting first it is (hd0) even though fdisk reports it as third (sdc). here is my OS part of  menu.lst. Note my windows entry at the bottom, it is (hd0,0) not (hd2,0). **It is the order of disk booting in BIOS that determines the x designation.**
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
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
rootnoverify	(hd0,0)
chainloader	+1
```

---

### Post by homermarin on 2009-09-27
thank u very much but according to that
1) what would the coordinates for my windows xp be?
2)why does a partition appear twice?

> 
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xbda56607

Disposit. Inicio Comienzo Fin Bloques Id Sistema
/dev/sda1 * 1 2553 20506941 83 Linux
/dev/sda2 2621 3824 9668608 7 HPFS/NTFS
/dev/sda3 3825 9728 47423880 f W95 Ext'd (LBA)
/dev/sda4 2554 2620 538177+ 82 Linux swap / Solaris
/dev/sda5 3825 9728 47423848+ 7 HPFS/NTFS

Las entradas de la tabla de particiones no están en el orden del disco

---

### Post by presence1960 on 2009-09-27
> **homermarin said:**
> thank u very much but according to that
1) what would the coordinates for my windows xp be?
2)why does a partition appear twice?
windows is probably on sda2 which would be (hd0,1) The second NTFS partition (sda5) is either another windows install or a data partition for windows.

If you want to be certain about what is on your machine do this:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by homermarin on 2009-09-28
thank u very much
here's what the script gives me

```


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

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

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros, 156301488 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xbda56607

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    41,013,944    41,013,882  83 Linux
/dev/sda2    *     42,094,592    61,431,807    19,337,216   7 HPFS/NTFS
/dev/sda3          61,432,560   156,280,319    94,847,760   f W95 Ext d (LBA)
/dev/sda5          61,432,623   156,280,319    94,847,697   7 HPFS/NTFS
/dev/sda4          41,013,945    42,090,299     1,076,355  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="d93ebddd-8d4f-4e25-952a-f723a7ab9464" TYPE="ext3" 
/dev/sda2: UUID="DAA85799A85772CD" LABEL="WinXP" TYPE="ntfs" 
/dev/sda4: UUID="c5815063-8cc7-4f35-97e3-50b374ebfcf3" TYPE="swap" 
/dev/sda5: UUID="2C9493C494938F48" LABEL="Datos" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/juan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=juan)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default		1

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=d93ebddd-8d4f-4e25-952a-f723a7ab9464 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d93ebddd-8d4f-4e25-952a-f723a7ab9464

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
uuid		d93ebddd-8d4f-4e25-952a-f723a7ab9464
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d93ebddd-8d4f-4e25-952a-f723a7ab9464 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d93ebddd-8d4f-4e25-952a-f723a7ab9464
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d93ebddd-8d4f-4e25-952a-f723a7ab9464 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d93ebddd-8d4f-4e25-952a-f723a7ab9464
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title              Microsoft Windows XP
root		  (hd0,1)
makeactive
chainloader	+1

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d93ebddd-8d4f-4e25-952a-f723a7ab9464 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=c5815063-8cc7-4f35-97e3-50b374ebfcf3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  14.7GB: boot/grub/menu.lst
  14.8GB: boot/grub/stage2
  14.8GB: boot/initrd.img-2.6.28-11-generic
  14.8GB: boot/initrd.img-2.6.28-15-generic
  14.8GB: boot/vmlinuz-2.6.28-11-generic
  14.7GB: boot/vmlinuz-2.6.28-15-generic
  14.8GB: initrd.img
  14.8GB: initrd.img.old
  14.7GB: vmlinuz
  14.8GB: vmlinuz.old





```

---

### Post by presence1960 on 2009-09-28
windows is on sda2. Does it boot from the grub menu. I ask because it has no boot files/dir- see this:

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    [COLOR="Red"]Boot files/dirs:[/COLOR]  

And there is no entry for boot.ini on the output you posted. So you see what I am saying I will post my entries you are lacking:

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
   [COLOR="Red"] Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM[/COLOR]

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

---

### Post by homermarin on 2009-09-28
yes, here's the story mate
I used to have both win7 and xp (win7 installed first than xp)
xp was in my E drive
so I erased my C drive where win7 was, to install ubuntu in it instead
ubuntu installed correctly but then I noticed GRUB wasn't loading my win xp
I believe the boot manager for win7 or vista is something called "bootmgr"
and I'm guessing that's why there are no boot files in E: drive
I have wondered if any of these solutions might be useful
a) reinstalling mbr
b) reinstalling grub (mmm probably not)
c) copying boot files from another winxp system, which I wouldnt know exactly what files to copy and where they'd be located

I don't know what else to do, thank u for all the help you've given us

---

### Post by Bucky Ball on 2009-09-28
Make a copy of your menu list with:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```Open the menu.lst file 

```
sudo nano /boot/grub/menu.lst
```

... and make these changes:


```
title         Vista
root          (hd0,1)
savedefault
makeactive
chainloader   +1
``````
title         Windows XP
root          (hd0,4)
savedefault
makeactive
chainloader   +1
```You may need to map the drives but see if that works first.

---

### Post by homermarin on 2009-09-28
yes, that's how I had it before hd(0,4) (with no savedefault) and it gave me "error 12"
as u can see those two NTFS are the same they both say "id 7"

currently all I have is 
1 partition with ubuntu ext3
1 partition for ubuntu swap
1 partition with winxp
1 partition which I used as data drive for windows (NTFS)
and that is it
when I was installing, it said I had one partition of about 8M created, I guess by windows installation, which could be  sda2. But they both (sda2 and sda5) have the same Id, is that important?
none of the methods I thought could be useful?



```
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xbda56607

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        2553    20506941   83  Linux
/dev/sda2            2621        3824     9668608    7  HPFS/NTFS
/dev/sda3            3825        9728    47423880    f  W95 Ext'd (LBA)
/dev/sda4            2554        2620      538177+  82  Linux swap / Solaris
/dev/sda5            3825        9728    47423848+   7  HPFS/NTFS

Las entradas de la tabla de particiones no están en el orden del disco
```


/dev/sda2 2621    3824_       9668608     **7**   HPFS/NTFS
/dev/sda3 **3825 9728** **474238**80  f  W95 Ext'd (LBA)
/dev/sda5 **3825 9728** **474238**48+ **7** HPFS/NTFS

---

### Post by Bucky Ball on 2009-09-28
This should tell you what you need to know regarding grub error 12:

[http://members.iinet.net.au/~herman546/p15.html#12_]("http://members.iinet.net.au/%7Eherman546/p15.html#12_")

---

### Post by homermarin on 2009-09-28
thank u all very much for the last time
I solved it by doing this
I looked for windows boot disk on google
I downloaded the xpquick I found in [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)
I copied those files to the root of xp partition
then I edited from my ubuntu the file boot.ini 
that comes just like this
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP" /fastdetect
```

I changed the "1" for 3 restarted, didn't work
later back to 1
I even tried 5 
but none work
at last I tried 2 and it was the lucky number

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP" /fastdetect
```

the unit letter still is E: and I'm back on XP
hope this eventually helps someone else

---

### Post by Bucky Ball on 2009-09-28
Good work!

To be of most help please mark thread as 'Solved'.

---


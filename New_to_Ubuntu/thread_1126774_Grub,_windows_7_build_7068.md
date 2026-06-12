---
title: "Grub, windows 7 build 7068"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by plasmarox on 2009-04-15
Hi all :D

Ive just installed windows 7 build 7068 (actually i upgraded to 7077 from 7068, but spotify didnt work so i downgraded back to 7068 again), and obviously ive lost GRUB to the MBR...

Note that i have:

partion 1 - primary - windows 7
partion 2 - primary - windows XP
partition 3 - extended
partition 4 - logical - Ubuntu
partition 5 - logical - swap(obviously :D)

What i'd REALLY like to know is how to install just GRUB (maybe ti a new partition to make it OS independant) so i can triple boot every thing correctly.

Cheers :D

hope this isnt a challenge.

EDIT:

also, id like to make windows 7  read EXT3  partitions. I've installed EXT2IFS, which apparently reads ext3 as well as ext2, but it says the drive is unformatted, would it like to format it?(NO!!!)

Cheers, plasmarox

---

### Post by cariboo on 2009-04-16
Have a look at this [thread=224351]howto[/thread] is has always worked for me.

There are no Windows utilities to read ext4 partitions yet.

Jim

---

### Post by plasmarox on 2009-04-16
Thanks for the link :)

Are you sure you dont mean ext3? =S

---

### Post by tarps87 on 2009-04-16
> **plasmarox said:**
> Thanks for the link :)

Are you sure you dont mean ext3? =S

It depends, what version of Ubuntu are you using? Ubuntu 9.04 (beta) supports ext4 and I think it is set as the default.

---

### Post by plasmarox on 2009-04-16
nope, ext3. Never knew there was an ext4 until now :)

---

### Post by tarps87 on 2009-04-16
I was going to suggest EXT2IFS but reading your first post you have already tried this. You will need to restart for it to take effect. You can try using it with vista compatibility mode and using admin privileges. Haven't tried it with windows 7 though. This thread may help:
[http://ubuntuforums.org/archive/index.php/t-1031540.html](http://ubuntuforums.org/archive/index.php/t-1031540.html)

Ext4 has been around for a while, it was release a stable last year.[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by cariboo on 2009-04-16
I only tried the utilities in Windows 7 on ext4 partitions, as that's all I have. I didn't realize they didn't work with ext3 also. I now run XPPro, VIsta and Windows 7 in vms, so I don't need to access any Linux partitions using an addon utility. I've found many programs that don't work with Windows 7, maybe when the RC comes out in May, it will be more compatible.

Jim

---

### Post by plasmarox on 2009-04-16
I think i must be stupid, or bad at explaing stuff :(

what i have is:

ubuntu: with grub bootloader, entries ubuntu and windows XP
windows 7 (on MBR), entries windows 7.

All i want to do is install grub to a new partition and boot everything!

Please, someone help, im pulling my hair out here!

EDIT:
partition 1 - GRUB (not installed)
partion 2 - primary - windows 7
partion 3 - primary - windows XP
partition 4 - extended
partition 5 - logical - Ubuntu
partition 6 - logical - swap(obviously )
New partitions:

---

### Post by meierfra. on 2009-04-16
Did you try the link from post 2?   Did you run into any problems with that tutorial?


> partition 1 - GRUB (not installed)
You shouldn't  need a separate partition for grub. But of course, it can be arranged if that's what you would like.

> windows 7 (on MBR), entries windows 7.
Your windows 7 boot menu has no entry for XP?  That's unusual.

> All i want to do is install grub to a new partition and boot everything!
It takes some work, but is possible. To  be  more precise, grub is not actually able to boot Win 7 or XP. But grub can chain loader the  XP and Win 7 boot loaders, which then will do the actual booting.

To get a better picture of your setup, I suggest to boot into  Ubuntu or the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags).

---

### Post by plasmarox on 2009-04-16
Yes - i'd prefer grub on it's own partition, so it's OS independent :)

i think the reason windows 7 has no XP entry is because i upgraded to 7077, then downgraded (custom install) to 7068 again.

Yes, annoying as it is...

Also, having used my handy super grub disk, windows XP doesnt boot - it says bootmgr is missing. Not sure... It displays if i open the drive in windows 7.

---

### Post by plasmarox on 2009-04-16
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file 
                       /NST/nst_grub-4C0F79F1DB4712F701C33A30098A177C.mbr is 
                       trying to chain load sector #95474295 on boot drive #1 
                       BootPart in the file 
                       /NST/nst_grub-E4DC30E49441E784530737D219CBF542.mbr is 
                       trying to chain load sector #95474295 on boot drive #1
    Operating System:  Windows XP
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 96755455 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x15d8a0c4

Partition  Boot         Start           End          Size  Id System

/dev/sda1              96,390    46,813,409    46,717,020   7 HPFS/NTFS
/dev/sda2    *     46,813,410    95,458,229    48,644,820   7 HPFS/NTFS
/dev/sda3          95,458,230   117,210,239    21,752,010   5 Extended
/dev/sda5          95,474,295   115,957,169    20,482,875  83 Linux
/dev/sda6         115,957,233   117,210,239     1,253,007  82 Linux swap / Solaris
/dev/sda4                  63        96,389        96,327  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0E40B28240B26FD7" LABEL="Windows 7" TYPE="ntfs" 
/dev/sda2: UUID="A628F63E28F60CD5" LABEL="Windows XP" TYPE="ntfs" 
/dev/sda4: LABEL="Grub" UUID="d48e409b-c1ae-4696-9def-0abbb8573e38" TYPE="ext2" 
/dev/sda5: LABEL="Ubuntu" UUID="0dc37565-f3c2-4b25-8c01-e726e8ad5424" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="513b074d-047d-41a2-91c4-06801466b135" 
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


============================== sda2/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File

#

# This is the NeoGrub configuration file, and should be located at D:\NST\menu.lst

# Please see the EasyBCD Documentation for information on how to create/modify entries:

# http://neosmart.net/wiki/display/EBCD



find --set-root --ignore-floppies /boot/grub/menu.lst

configfile /boot/grub/menu.lst



# All your boot are belong to NeoSmart!
=========================== sda5/boot/grub/menu.lst: ===========================

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
timeout		3

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
# kopt=root=UUID=0dc37565-f3c2-4b25-8c01-e726e8ad5424 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0dc37565-f3c2-4b25-8c01-e726e8ad5424

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
uuid		0dc37565-f3c2-4b25-8c01-e726e8ad5424
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0dc37565-f3c2-4b25-8c01-e726e8ad5424 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		0dc37565-f3c2-4b25-8c01-e726e8ad5424
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0dc37565-f3c2-4b25-8c01-e726e8ad5424 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		0dc37565-f3c2-4b25-8c01-e726e8ad5424
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


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0dc37565-f3c2-4b25-8c01-e726e8ad5424 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=513b074d-047d-41a2-91c4-06801466b135 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  49.5GB: boot/grub/menu.lst
  49.5GB: boot/grub/stage2
  50.8GB: boot/initrd.img-2.6.27-11-generic
  49.7GB: boot/initrd.img-2.6.27-7-generic
  49.6GB: boot/initrd.img-2.6.27-9-generic
  55.4GB: boot/vmlinuz-2.6.27-11-generic
  49.6GB: boot/vmlinuz-2.6.27-7-generic
  52.7GB: boot/vmlinuz-2.6.27-9-generic
  50.8GB: initrd.img
  49.6GB: initrd.img.old
  55.4GB: vmlinuz
  52.7GB: vmlinuz.old
```

---

### Post by meierfra. on 2009-04-16
I see that your did tried to boot Ubuntu via EasyBCD.  Did that work?

> All i want to do is install grub to a new partition and boot everything! 


OK. The first step of course is to create a new partition. I suggest to used gparted to shrink your XP partition (/dev/sda2) by say 200 MB (shrink it from the right, don't move the  start point). Then  use  the 200MB to create a primary Fat32 partition.  (You can use ext2 instead and  you can also make it a lot smaller like 4MB.  But a 200MB  Fat32  partition will be lot  more flexible, in case  you ever decide to change you boot set up.)

Then follow this tutorial to turn your new partition into a Grub partition [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)


You  will also have to  move the boot files for Win 7 to the Win 7 partition (they currently are on the XP partition), edit the Win 7 boot loader,  and  fix the boot sector of the XP partition. I'll prefer to do one thing at a time. So I'll provide the details after you successfully  setup the dedicated Grub partition.

---

### Post by plasmarox on 2009-04-17
I have already made a new partition (i foolishly reduced the win7 start point :$, which took an hour), which will be the first partition. I think it is ~50mb. OK, next step please :D

EDIT:

Yes, i did give easy BCD a go - it manages to chainload my ubuntu, but this seems such a dirty way of doing it :)

---

### Post by plasmarox on 2009-04-17
i have to admit, i quite like this:

> # All your boot are belong to NeoSmart!
=========================== sda5/boot/grub/menu.lst: ===========================



---

### Post by meierfra. on 2009-04-17
> K, next step please
???? I already gave you the next step. Follow the tutorial in Hermanzone to turn your 50MB partition into a  dedicated grub partition.

I'll write up the remaining steps soon. I don't have much time right now.

---

### Post by Jammy4041 on 2009-04-17
This is from the EXT2IFS trouble shooting page:

> [B]I have installed the Ext2 IFS software and was able to create a drive letter for a desired volume of Linux. But when I try to access that volume I get an error message "The disk in drive X: is not formatted. Do you want to format it now?" (Of course I don't want to!) Or the content of the volume appears, but when I attempt to write something I get an error message "Access denied".

[/B]The ext2fs.sys driver did not mount that volume for some reason, or it mounted it read-only.

Please run the mountdiag diagnosis tool, which you can download here: mountdiag.exe (updated, 07-19-2008.)

Please run it at the command prompt and give it the letter of the drive you want to examine, for example:
mountdiag G:
The tool will give you a hint on how to resolve the problem. (Note: The mountdiag tool reads data only; it does not attempt to modify anything.)I did this and I remember the tool saying tat the block size exceeded 64 bytes or something like that, and basically, all I could do was reformat the drive, ensuring that it used a 64 byte block size. Try as I might, I couldn't find anything else that would allow me to access ubuntu from windows that did acctually work with this newer, larger block size.
A pain indeed! So I thought it was too much bother as I almost only use ubuntu now anyway; I can afford to sacrifice a few minutes to reboot.

FS Driver did work for me a while back, so I can only assume that the default block size has changed. 

As for wanting to have an OS-independent GRUB, I have an independent GRUB partition, to triple-boot Windows/Ubuntu and Fedora. I've gone for a Reisar FS partition, because its very small and effecient. And as it turned out, I'd followed HermanZone's making a dedicated GRUB partition.

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")

I have something like this:

Boot --> Load GRUB 

then:

[LIST]
[*]Chainloads the Windows 7 boot menu; allowing for me to choose Windows 7 or Windows XP
[*]Boot Ubuntu 9.04 Directly
[*]Boot Fedora 10 Directly
[*]Memory Test
[/LIST]
 Really, I should also have links in there for the Recovery modes and stuff, but I shall be putting them in soon. 

Having an OS-independent GRUB is nice as it means I can easily experiment with other distributions and even BSD flavours, and all I have to do is add another entry to my "master grub menu".

---

### Post by meierfra. on 2009-04-17
[B]After you successfully created  the  dedicated grub partition  and are able to boot into Ubuntu and Win 7:
[/B]

[COLOR=blue] Boot into Win 7.[/COLOR]


[B]Step 1 Edit the Win 7 boot loader
[/B]
Go to "Start". Type "cmd" and press "Ctrl+Shift+Enter". This will open a Win 7 commandline as an administrator. Type



```
  
bcdedit /set {bootmgr} device boot

```


**Step 2 Fix the XP bootsector.**

There are various ways to accomplish this. I will give you two options:

Option 1:

Insert your Win 7 CD in the CDRom drive and wait for a few second. At the command line:


```

E:\boot\bootsect  /nt52 D: /force

```

Here "E" needs to be replaced by the drive letter of your CDrom drive and "D" by the drive letter of your XP partition. (Just look in "My Computer" to determine the drive letters. Even if you know the drive letters, I suggest to double check. Win 7 and XP probably use different drive letters assigns. You need to use the drive letters used by Win 7)

Option 2:

Boot from your XP CD.
Press "r" to enter the repair console.
Use



```
map
```

to determine the drive letter of your XP partition. Type


```

fixboot C:

```

Here "C" needs to be replaced by the drive letter of your XP partition.

If neither Options 1 nor Option2 works for you, let me know and I can show you how to fix the boot sector from Ubuntu.


[COLOR=blue] Boot into Ubuntu.[/COLOR] and open a terminal (Applications->Accessories->Terminal) 


** Step 3 Add Win 7 to "menu.lst" **

Open menu.lst via


```
gksudo gedit /boot/grub/menu.lst
```

Your current entry for Win 7, will actually boot XP. So you might want to edit the title. Also you should create a similar entry for Win 7. (if you need help with that post the output of "sudo fdisk -lu")



** Step 4  Move the boot files from XP to Win 7 **

Type 

```
 sudo fdisk -lu
```

and determine the device name of the XP partition and the device name of the Win 7 parition.
In the following I assume that  XP is on /dev/sda2 and Win 7 is on /dev/sda1. 

```
 sudo mkdir /mnt/{XP,Win}
sudo mount /dev/sda2 /mnt/XP
sudo mount /dev/sda1 /mnt/Win
sudo mv /mnt/XP/{Boot,bootmgr} /mnt/Win

```
Of course you need to  replace  /dev/sda2 by the device name of the XP partition and /dev/sda1 by the device name of the Win 7 partition. 
Sometimes the directory  Boot  is called BOOT instead. Use  "ls -l /mnt/XP" the determine the correct spelling. 


Reboot and hopefully you will be able to boot into all your OSs from the Grub menu.

---

### Post by plasmarox on 2009-04-22
Thank you for your help - i decided to scrap my XP and ubuntu, as im going to to a clean install for januty anyway, and the its not jsut the bootsector for XP - its the whole bootloader :(

So i used my XP recovery CD, installed windows 7, and will install januty as it comes out and i will hopefully be able to boot everything :)

Thank you anyways

---

### Post by meierfra. on 2009-04-23
> the its not jsut the bootsector for XP - its the whole bootloader 

????  I'm not sure what you are  saying.

> i will hopefully be able to boot everything

If you want to be able to boot everything directly from Grub, you still have to separate the XP and Win 7 boot loaders.

---


---
title: "Help! I am drowning in Grub/MRB problems"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by yogo on 2009-01-27
My hard drive has had 8.04 installed and has been the only OS, yesterday I installed Windows 7 after partitioning and resizing my Ubuntu.

First today I tried to use Easybcd to add Grub to my Windows MBR. I do believe it did this successfully as I did see my menu.1st. However I received a grub error 17. This was from my Windows install. I tried it a couple of different ways and always came back with the same error.

So the last few hours I have been booting a live cd and reinstalling grub from it. This I have down before with other pc's. However I am running into the same error 17 so that is why I think easybcd was successful.

I have read everywhere and now my mind is spinning

Steps I have done from terminal.

1 Sudo grub
2 find /boot/grub/stage1
3 root (hd0)
4 Setup (hd0)
5 quit

reboot and error 17. As to steps 2 and 3, I have changed this up with (hd0,1) (hd0,2) (hd1,0) (hd0.0) and every other possible combination that I thought may work. 

I guess for now I would like to do it with easybcd if possible, otherwise grub.

I also have used the Super Grub disk and that too has the same error 17 when trying to let it repair grub. Finally I had it remove Grub from my MBR and now I can boot Windows. 
 
Here is how my hd looks

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2162    17366233+   7  HPFS/NTFS
/dev/hda2            2163        9565    59464597+  83  Linux
/dev/hda3            9566        9729     1317330    5  Extended
/dev/hda5            9566        9729     1317298+  82  Linux swap / Solaris

Disk /dev/sdd: 1005 MB, 1005060096 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         122      979933+   b  W95 FAT32


I am completely lost and confused!

Any help is greatly appreciated.

---

### Post by marshall.robert on 2009-01-27
Havnt read the whole thing (to lazy, lol) but i have to mount the drive and then cd to where its mounted and then do the grub stuff otherwise it fails.

Hope that helps :D

---

### Post by caljohnsmith on 2009-01-27
Do you get the Grub menu on start up, but when you choose an OS, is that when you get the Grub error 17? Or do you get the error 17 before seeing the Grub menu? In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by LowSky on 2009-01-27
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/](http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/)

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by estyles on 2009-01-27
> **yogo said:**
> 
1 Sudo grub
2 find /boot/grub/stage1
3 root (hd0)
4 Setup (hd0)
5 quit


Your problem is in line 3.  Line 2 should return (hd0,1).

Then you should do "root (hd0,1)", then "setup (hd0)".  If line 2 returns something other than (hd0,1), then use that instead.

---

### Post by yogo on 2009-01-27
> **marshall.robert said:**
> Havnt read the whole thing (to lazy, lol) but i have to mount the drive and then cd to where its mounted and then do the grub stuff otherwise it fails.

Hope that helps :D


I have never had to do it that way in the past, offhand, what are the commands for mounting from terminal?

TIA

---

### Post by yogo on 2009-01-27
> **estyles said:**
> Your problem is in line 3.  Line 2 should return (hd0,1).

Then you should do "root (hd0,1)", then "setup (hd0)".  If line 2 returns something other than (hd0,1), then use that instead.


I have done it that way exactly, I changed it up a few different ways. That was the first way I tried it but got the error 17.

Thanks

---

### Post by yogo on 2009-01-27
@ caljohnsmith

I got the menu.lst  first, the error 17 came after.

Right now I am in Windows, I will try that is I can not get it fixed from here. Man I am tired of booting a live cd.:(

---

### Post by marshall.robert on 2009-01-27
> **yogo said:**
> I have never had to do it that way in the past, offhand, what are the commands for mounting from terminal?

TIA

```
mount /dev/hda<n> /mnt
``` where <n> is the partition number of you Ubuntu installation.

its then ```
cd /mnt
``` to browse to the dir where you mounted.

---

### Post by yogo on 2009-01-27
> **caljohnsmith said:**
> Do you get the Grub menu on start up, but when you choose an OS, is that when you get the Grub error 17? Or do you get the error 17 before seeing the Grub menu? In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.


```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/hda
 => No boot loader is installed in the MBR of /dev/hdc
 => No boot loader is installed in the MBR of /dev/hdd
 => Lilo is installed in the MBR of /dev/sdd

hda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_lilo.mbr is trying to 
                       chain load sector #34732530 on boot drive #1
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /BOOTMGR

hda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of hda2 and 
                       looks at sector 36658754 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/hda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Boot file info:     
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 63.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive hda: _____________________________________________________________________

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot        Start          End         Size  Id System

/dev/hda1    *            63   34,732,529   34,732,467   7 HPFS/NTFS
/dev/hda2         34,732,530  153,661,724  118,929,195  83 Linux
/dev/hda3        153,661,725  156,296,384    2,634,660   5 Extended
/dev/hda5        153,661,788  156,296,384    2,634,597  82 Linux swap / Solaris


Drive hdc: _____________________________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 3 MB, 3540992 bytes
255 heads, 63 sectors/track, 0 cylinders, total 1729 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot        Start          End         Size  Id System

Invalid MBR Signature found


Drive hdd: _____________________________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdd: 732 MB, 732293120 bytes
255 heads, 63 sectors/track, 22 cylinders, total 357565 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot        Start          End         Size  Id System

Invalid MBR Signature found


Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 1005 MB, 1005060096 bytes
255 heads, 63 sectors/track, 122 cylinders, total 1963008 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot        Start          End         Size  Id System

/dev/sdd1                 63    1,959,929    1,959,867   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/hda1: TYPE="ntfs" 
/dev/hda2: UUID="d56777a6-8115-41dd-8ba6-b658fb06f787" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="b3c4d660-c668-487a-a92d-4282422ac9a4" TYPE="swap" 
/dev/sdd1: LABEL="           FAT32   Ÿw|¬"ÀtVŽ»" UUID="4844-05A2" TYPE="vfat" 

=============================== "mount" output: ===============================

unionfs on / type unionfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdc on /media/cdrecorder type iso9660 (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8)
/dev/sdd1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=999,gid=999,umask=077,iocharset=utf8)

=========================== hda2/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=d56777a6-8115-41dd-8ba6-b658fb06f787 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 8.04.1, kernel 2.6.24-23-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=d56777a6-8115-41dd-8ba6-b658fb06f787 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=d56777a6-8115-41dd-8ba6-b658fb06f787 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=d56777a6-8115-41dd-8ba6-b658fb06f787 ro quiet splash
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=d56777a6-8115-41dd-8ba6-b658fb06f787 ro single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=d56777a6-8115-41dd-8ba6-b658fb06f787 ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=d56777a6-8115-41dd-8ba6-b658fb06f787 ro single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 8.04.1, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=d56777a6-8115-41dd-8ba6-b658fb06f787 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=d56777a6-8115-41dd-8ba6-b658fb06f787 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== hda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d56777a6-8115-41dd-8ba6-b658fb06f787 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b3c4d660-c668-487a-a92d-4282422ac9a4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== hda2: Location  of files loaded by Grub: ===================


  18.8GB: boot/grub/menu.lst
  18.7GB: boot/grub/stage2
  18.7GB: boot/initrd.img-2.6.24-16-generic
  18.7GB: boot/initrd.img-2.6.24-16-generic.bak
  18.7GB: boot/initrd.img-2.6.24-21-generic
  18.8GB: boot/initrd.img-2.6.24-21-generic.bak
  18.8GB: boot/initrd.img-2.6.24-22-generic
  18.8GB: boot/initrd.img-2.6.24-22-generic.bak
  18.8GB: boot/initrd.img-2.6.24-23-generic
  18.8GB: boot/initrd.img-2.6.24-23-generic.bak
  18.7GB: boot/vmlinuz-2.6.24-16-generic
  18.7GB: boot/vmlinuz-2.6.24-21-generic
  18.8GB: boot/vmlinuz-2.6.24-22-generic
  18.7GB: boot/vmlinuz-2.6.24-23-generic
  18.8GB: initrd.img
  18.8GB: initrd.img.old
  18.7GB: vmlinuz
  18.8GB: vmlinuz.old

=======Devices which don't seem to have a corresponding hard drive==============

=============================== StdErr Messages: ===============================

No errors were reported.

```

The Lilo was just recently added from Easybcd after failing so many times trying to add grub.

I am now in live CD. Let's see if it can be fixed from here.

Thanks

I am going to try mounting to see if that makes a difference, in the past I have never had to mount the hd to reinstall grub.

---

### Post by stchman on 2009-01-27
Problem is that a Windows OS will overwrite GRUB in favor of itself.  You will need to reinstall GRUB.  Here is a HOWTO.

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

Hope this helps.

---

### Post by caljohnsmith on 2009-01-27
It looks like the main problem is with your menu.lst; how about doing:
```
sudo umount /mnt && sudo mount /dev/hda2 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change all the Ubuntu entries to use (hd0,1) similar to:
```
title        Ubuntu 8.04.1, kernel 2.6.24-23-generic
root        [COLOR="Blue"](hd0,1)[/COLOR]
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=d56777a6-8115-41dd-8ba6-b658fb06f787 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

```
Also change the "groot" line:
```
# groot=[COLOR="Blue"](hd0,1)[/COLOR]
```
Save, reboot, and I think you should be able to boot Ubuntu if you can get the Grub menu again. Let me know how it goes or if you run into problems.

---

### Post by yogo on 2009-01-27
> **caljohnsmith said:**
> It looks like the main problem is with your menu.lst; how about doing:
```
sudo umount /mnt && sudo mount /dev/hda2 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```And change all the Ubuntu entries to use (hd0,1) similar to:
```
title        Ubuntu 8.04.1, kernel 2.6.24-23-generic
root        [COLOR=Blue](hd0,1)[/COLOR]
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=d56777a6-8115-41dd-8ba6-b658fb06f787 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

```Also change the "groot" line:
```
# groot=[COLOR=Blue](hd0,1)[/COLOR]
```Save, reboot, and I think you should be able to boot Ubuntu if you can get the Grub menu again. Let me know how it goes or if you run into problems.



I have made all the changes and I do think this will work. Lots of thank you's in advance. As for groot it is commented out, should I remove #?

TIA

---

### Post by caljohnsmith on 2009-01-27
Please leave the groot commented out; even though it is commented so it isn't read on start up, the "update-grub" command uses that info to determine which partition your Ubuntu is on. So basically correcting the groot line will prevent future problems when you get a kernel upgrade. :)

---

### Post by yogo on 2009-01-27
> **caljohnsmith said:**
> Please leave the groot commented out; even though it is commented so it isn't read on start up, the "update-grub" command uses that info to determine which partition your Ubuntu is on. So basically correcting the groot line will prevent future problems when you get a kernel upgrade. :)

That did it! Thank you, I knew that was going to work. All of my messing around with the MRB, uninstalling and reinstalling grub. My menu.lst was pointing to the wrong partition.

Thanks a lot for pointing that out. 

Solved as we can not mark with thread tools.

Thanks to all those who offered help.

---

### Post by caljohnsmith on 2009-01-27
Glad that did the trick; cheers and enjoy your Ubuntu install. :)

---


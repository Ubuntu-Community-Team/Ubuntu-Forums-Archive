---
title: "Grub rescue???"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by MibunoOokami on 2011-02-24
This thread is somewhat related to [this one]("http://ubuntuforums.org/showthread.php?t=1693590") particularly my last post. Since I didn't get any response as to how to save my files that had permission restrictions, I decided to be a smart@$$ and put ubuntu 10.10 onto an external hard drive thinking I would be able to then go in and access my files from 9.10 (thought if I do it on my pc hdd and something goes wrong all files would be lost). Unfortunately at the end of the installation when I did the reboot, I got an error message ```
ERROR: No such device ff93f56e-7de54879-a034-f921c27bdf72

GRUB RESCUE>
```I did a brief search on this forum but the thing with the advice given was the assumption that the grub had been deleted. I don't think my pc grub would have been deleted when I was installing on an external drive. Also I had been using my pc with dual OS and I really need to get it working again and really need to save the files that were on 9.10
Any help much appreciated. As mentioned I am not new to Ubuntu, however I am new to complex things such as this.

edit: Thought it necessary to also say that whilst I do/did have windows vista on my pc it came preloaded and I never got any install cds etc to go with it if I remember correctly some threads suggested booting with windows cd to help fix grub which is why I added this note

---

### Post by Rubi1200 on 2011-02-25
Hi,
we need to get a better overview of the current setup.

To that end, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by MibunoOokami on 2011-02-25
> **Rubi1200 said:**
> 
 1. Download the boot info script. There is a link in my signature.
 
 
 Thank you I tried to download but keep getting a server timed out message  tried with windows pc also but with same result. Perhaps is there an  alternative download site?

edit: kept trying the download page it finally loaded but it won't download keeps saying download will start shortly but never does, tried direct link and a variety of mirrors pages say done but nothing downloads. Again using the live cd and using a windows pc.

---

### Post by Rubi1200 on 2011-02-25
Hmm...keep trying the download link.

I will also upload a copy here in a zip file for you to try and access.

---

### Post by MibunoOokami on 2011-02-25
Kept trying but getting nowhere I'm thinking perhaps my internet connection is too slow as I'm not sure that website is actually fully loading. So I just used the zipped file you provided thank you and below should be the results.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    22,388,735    22,386,688  27 Hidden HPFS/NTFS
/dev/sda2    *     22,388,736   128,003,970   105,615,235   7 HPFS/NTFS
/dev/sda3         128,005,981   768,147,974   640,141,994   5 Extended
/dev/sda5         128,005,983   757,866,374   629,860,392  83 Linux
/dev/sda6         757,866,438   768,147,974    10,281,537  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        388A35028A34BDE6                       ntfs       Recovery                      
/dev/sda2        D0AC5FB4AC5F9436                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        f17d068f-b1cd-4864-87bf-dcc87924a63f   ext3                                     
/dev/sda6        32ff26f8-f948-4e09-b297-6eda46b51d37   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f17d068f-b1cd-4864-87bf-dcc87924a63f

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

title        Ubuntu 9.10, kernel 2.6.31-22-generic
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, kernel 2.6.31-21-generic
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
uuid        f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=09e0b212-7601-48f9-8f8e-82ce7f237f26 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=09e0b212-7601-48f9-8f8e-82ce7f237f26 ro single 
initrd        /boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=09e0b212-7601-48f9-8f8e-82ce7f237f26 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=09e0b212-7601-48f9-8f8e-82ce7f237f26 ro single 
initrd        /boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.04.2, memtest86+ (on /dev/sda5)
root        (hd0,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=32ff26f8-f948-4e09-b297-6eda46b51d37 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  76.0GB: boot/grub/menu.lst
  76.0GB: boot/grub/stage2
  76.0GB: boot/initrd.img-2.6.28-16-generic
  76.1GB: boot/initrd.img-2.6.31-14-generic
  76.0GB: boot/initrd.img-2.6.31-15-generic
  76.0GB: boot/initrd.img-2.6.31-16-generic
  81.5GB: boot/initrd.img-2.6.31-17-generic
  77.5GB: boot/initrd.img-2.6.31-19-generic
  76.0GB: boot/initrd.img-2.6.31-20-generic
  76.1GB: boot/initrd.img-2.6.31-21-generic
  76.1GB: boot/initrd.img-2.6.31-22-generic
  76.0GB: boot/vmlinuz-2.6.28-16-generic
  76.1GB: boot/vmlinuz-2.6.31-14-generic
  76.1GB: boot/vmlinuz-2.6.31-15-generic
  76.1GB: boot/vmlinuz-2.6.31-16-generic
  76.1GB: boot/vmlinuz-2.6.31-17-generic
  76.1GB: boot/vmlinuz-2.6.31-19-generic
  76.0GB: boot/vmlinuz-2.6.31-20-generic
  76.0GB: boot/vmlinuz-2.6.31-21-generic
  76.0GB: boot/vmlinuz-2.6.31-22-generic
  76.1GB: initrd.img
  76.1GB: initrd.img.old
  76.0GB: vmlinuz
  76.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 28 e8 8a 25 00 fe  |..........(..%..|
000001d0  ff ff 05 fe ff ff 2a e8  8a 25 80 e2 9c 00 00 00  |......*..%......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by MibunoOokami on 2011-02-26
Can anyone tell me where to go or what to do from here please?

---

### Post by Rubi1200 on 2011-02-27
Is there some reason you have the older version of GRUB installed?

Ubuntu from 9.10 onwards uses GRUB2.

I suggest you use a LiveCD to purge and reinstall GRUB:
[FONT=monospace]
[/FONT]```
sudo mkdir /mnt/temp
sudo mount /dev/sda5 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```
These commands will bring you to a root prompt (be very careful; easiest to avoid mistakes by just copy/paste)
```
apt-get update
apt-get purge grub grub-pc grub-common
apt-get install grub-common grub-pc
update-grub 
```
Once these commands have run and there are no errors, run these:
```
exit
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
```
Reboot the computer.

If you encounter errors along the way, stop and report them here before proceeding.

---

### Post by MibunoOokami on 2011-02-27
I'm not sure why there is an older version of grub or even that there was a new one. All my updates/upgrades had been done using update manager but during the past few months I had been unable to do any upgrades or updates then when I was able to the button wasn't there to upgrade so I joined here and started first thread which lead me here. I will follow your instructions and report back, but I would like to know, following those commands won't destroy any files on 9.10 will they? I will cut and paste to stay on the safe side thanks again for your help

---

### Post by Rubi1200 on 2011-02-27
Yes, copy/paste for all the commands is safest.

No files will be destroyed (or shouldn't be!) since all you are doing is restoring the bootloader in the MBR.

Wait, stop! You say 9.10? But according to the information from the script you have 10.04.2; Please explain.

---

### Post by MibunoOokami on 2011-02-27
> **Rubi1200 said:**
> 
Wait, stop! You say 9.10? But according to the information from the script you have 10.04.2; Please explain.

Basically I wanted to upgrade from 9.10 but the button wouldn't appear, a suggestion was to change my source list from 'karmic' to 'lucid' then do sudo update and upgrade which I did then after a restart I couldn't log in. That's when I decided to burn a live CD and do an install but wanted to save files to be on the safe side but they are all protected by permission restrictions which is when I decided to try be smart and put 10.10 onto an external drive to try override the permissions and that is how I ended up with the grub rescue message. It is probably better explained in my other thread which is linked in my first post in this thread. I will wait for your reply again before I follow your instructions just to be on the safe side.

---

### Post by Rubi1200 on 2011-02-27
When you are on the LiveCD, can you mount and access your files on the Ubuntu install?

---

### Post by MibunoOokami on 2011-02-27
> **Rubi1200 said:**
> When you are on the LiveCD, can you mount and access your files on the Ubuntu install?

Yes I can see and look at and access everything, just can't save or C&P.

---

### Post by Rubi1200 on 2011-02-27
Okay, this is what I would do in your situation.

Make sure you have an external medium such as another drive or USB stick where you can save your important data.

Then, from the LiveCD, run this command in the terminal:

```
gksudo nautilus
```
This should give you root access to the partition where Ubuntu is installed (you need to navigate there first) and you can then copy the files to a safe place.

Please be very careful; you have root access and one wrong move and you could mess things up.

Once you are sure your data is safe, we can move forward but please don't run the other commands to restore GRUB just yet.

---

### Post by MibunoOokami on 2011-02-27
Hmm tried that command but still keep getting messages such as 'Error opening file: Permission denied' and 'error while copying. The folder cannot be handled because you do not have permissions to read it'

---

### Post by Rubi1200 on 2011-02-27
I am going to ask some other users to take a look at the thread and offer some perspectives. 

You may need to chroot into the file system and run some commands to update, but I would rather make sure you can save your data first.

Hang in there please.

---

### Post by MibunoOokami on 2011-02-27
No problem, I will await your (or others') replies

---

### Post by coffeecat on 2011-02-27
Hi, I'm one of the other "perspectives".

Tbh, I'm having difficulty getting my head around this situation, but I'd like to ask some questions to clarify one aspect. First though, a couple of comments.

You have grub 2 in the mbr pointing to sda5 which has Ubuntu 10.04.2 installed but without grub2's grub.cfg. Instead it has legacy grub's menu.lst but with entries for Ubuntu 9.10 on sda5 (the UUID corresponds) but also Ubuntu 8.04 also seemingly on sda5, but with a different UUID. I'm sure there's a logical explanation for that, but it's eluding me at the moment. :? My inclination would be to install (that is, install from the repository) grub2 on that partition by chrooting from the live CD, but first...

You said you installed 10.10 to an external HD. And then when you tried the reboot, you got the error message:

```
ERROR: No such device ff93f56e-7de54879-a034-f921c27bdf72

GRUB RESCUE>
```Was that with or without the external drive attached? If without, what happens when you try to boot with the external drive attached? I suspect that the ff93f56e-7de54879-a034-f921c27bdf72 partition is partition #5 on the external drive and that the external drive became sda and the internal something else, and also that grub2 in the mbr is trying to find partition #5 on the external HD.

It looks as though you ran the boot script without the external drive attached. For completeness  it might be useful to attach (and switch on) the external drive, boot up the live CD and run the boot script again.

In the meantime, I'll see if I can find a link for installing grub2 via a chroot from the live CD.

---

### Post by MibunoOokami on 2011-02-27
> **coffeecat said:**
> Hi, I'm one of the other "perspectives".

Tbh, I'm having difficulty getting my head around this situation, but I'd like to ask some questions to clarify one aspect. First though, a couple of comments.

You have grub 2 in the mbr pointing to sda5 which has Ubuntu 10.04.2 installed but without grub2's grub.cfg. Instead it has legacy grub's menu.lst but with entries for Ubuntu 9.10 on sda5 (the UUID corresponds) but also Ubuntu 8.04 also seemingly on sda5, but with a different UUID. I'm sure there's a logical explanation for that, but it's eluding me at the moment. :? My inclination would be to install (that is, install from the repository) grub2 on that partition by chrooting from the live CD, but first...

You said you installed 10.10 to an external HD. And then when you tried the reboot, you got the error message:

```
ERROR: No such device ff93f56e-7de54879-a034-f921c27bdf72

GRUB RESCUE>
```Was that with or without the external drive attached? If without, what happens when you try to boot with the external drive attached? I suspect that the ff93f56e-7de54879-a034-f921c27bdf72 partition is partition #5 on the external drive and that the external drive became sda and the internal something else, and also that grub2 in the mbr is trying to find partition #5 on the external HD.

It looks as though you ran the boot script without the external drive attached. For completeness  it might be useful to attach (and switch on) the external drive, boot up the live CD and run the boot script again.

In the meantime, I'll see if I can find a link for installing grub2 via a chroot from the live CD.

Wow let me see if I can clarify anything for you.I can't say anything about 10.04 you guys are telling me I have it, I'm not sure since I have not been able to use Ubuntu since changing the source list so just assume it's still 9.10, I can say that at the grub menu (when booted up) 8.04 appeared at the bottom below other operating systems I wanted to remove it long ago because there's such a long list but if I recall correctly you need to much around with the kernel to remove them so I just left it alone. Moving on, I got the error message when I rebooted with the external drive still attached, assuming that was what caused the grub rescue message I unmounted and removed it then rebooted only to get the same message. I'm wondering if when doing the upgrade through package manager something has not been going 100% right and that perhaps from now on I should make a live cd

---

### Post by coffeecat on 2011-02-27
> **MibunoOokami said:**
> I can't say anything about 10.04 you guys are telling me I have it

Not us. Your boot script: :)

> **MibunoOokami said:**
> 
```

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [COLOR=Red]Ubuntu 10.04.2 LTS[/COLOR]
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab
```

Which is interesting - and inexplicable from what you say. I'll do a bit more thinking and get back later.

**EDIT**: Not so inexplicable after all. I just remembered this:

> **MibunoOokami said:**
> Basically I wanted to upgrade from 9.10 but  the button wouldn't appear, a suggestion was to change my source list  from 'karmic' to 'lucid' then do sudo update and upgrade which I did  then after a restart I couldn't log in.

You may have a hybrid Karmic/Lucid there which may be difficult to repair. As I said, I'll do some more thinking and get back.

---

### Post by MibunoOokami on 2011-02-27
I was just about to edit my post when I saw your reply, wanted to also say that I'm not sure how I ran the boot script (if I did) or how to do it again I mean I just clicked install entered my name and location and the disk did the rest as far as I know

edit: I hope I'm not coming across as a jack@$$ or anything I am grateful for and appreciative of all the help I am getting, this is all just a bit overwhelming for me, as long as a computer does what it is supposed to I am fine but when it doesn't then I have a few troubles but sometimes can take care of the problems myself

---

### Post by MibunoOokami on 2011-02-27
> **coffeecat said:**
> 
You may have a hybrid Karmic/Lucid there which may be difficult to repair.

Yea I probably do, most likely I fudged something in the source list. I will check up on this thread again in the morning, it's pretty late. Thanks

---

### Post by fabricator4 on 2011-02-27
> **Rubi1200 said:**
> I am going to ask some other users to take a look at the thread and offer some perspectives. 

You may need to chroot into the file system and run some commands to update, but I would rather make sure you can save your data first.

Hang in there please.

Well, getting back to the OP's ***real*** problem, being that he wants to rescue his data on /dev/sda5

Forgetting about problems with grub and messed up installations...  he can boot the live CD and get access to sda5, then use "sudo cp" to copy his data to an external drive.

Problem solved?

Regarding getting the machine booting, preferably with 10.04 LTS, I think at this point I'd favor a clean install from the 10.04 live CD once all the data is safe...  unless of course MibunoOokami really wants the intellectual exercise of fixing his broken system.

Personally I try to avoid hitting my head against brick walls.  Although it's nice when you stop, there's normally some comedian on the other side waiting for you to stick your head through the hole you just made so he take a swipe at it with one of those styrofoam stage mallets.  Nyuk Nyuk Nyuk.

Chris

---

### Post by Rubi1200 on 2011-02-27
@fabricator4: with all due respect, but the OP already said that he is having difficulties copying the data because of permissions issues, explainable, perhaps, if coffeecat is right because of an upgrade gone wrong.

@coffeecat: I appreciate the input. I already posted information about how to reinstall GRUB with a chroot.

@MibunoOokami: another possibility, if you can, is to download and burn to CD a distro called Slax.

I have found it can access partitions/data when the Ubuntu CD is having issues. In any event, it might be worth a shot.

At this point, unless you can rescue the data, you are looking at either a fresh install (which WILL wipe out any data) or my method of reinstalling GRUB (which *may* get you booting again, but might still leave you with the problem of accessing data). Either way, there is risk involved.

Both coffeecat and myself will continue looking for solutions in the meantime.

---

### Post by coffeecat on 2011-02-27
> **Rubi1200 said:**
> I already posted information about how to reinstall GRUB with a chroot.

Apologies, I missed that among all the other information. I'm 100% with you on that one.

However, it might be quicker in the long run if the OP were to backup all their data and do a fresh install. Having said that, there are the permissions problems to sort out. I would have thought a gksu nautilus should have dealt with that, and I'm surprised at the "Error opening file: Permission denied" and "error while copying. The  folder cannot be handled because you do not have permissions to read it" messages. I'll re-read that bit of the thread.

---

### Post by Rubi1200 on 2011-02-27
The other possibility, before trying to reinstall GRUB, might be to do either an fsck and/or chroot to run update/upgrade commands.

What do you think coffeecat?

I am also concerned about the permissions issue.

@MibunoOokami: during this whole process, did you ever change file permissions for any reason?

---

### Post by QLee on 2011-02-27
It does appear to be a complicated mess. 

Very likely that that failed upgrade attempt has left the system in a "mixed" version state which may or may not be recoverable.

Seems like a sane approach to try installing GRUB2 (grub-pc) from within the chroot as suggested. Then, (since you've already changed the sources list to Lucid) and since you're already in the chroot, try doing a dist-upgrade from there. 

If that doesn't work you could also try a Lucid install over what is already there but specifing to not format the partition (or your home if it is separate). In theory that should overwrite the system files and leave your data intact. I can't promise anything. [Edit] I don't want  to make this sound too scary so I will also mention the following. Even though I won't promise you luck with this, I will comment that it has worked for me with an inline /home which was left intact. Since I don't know the method the installer uses to "clean" before writing and since it might just wipe system directories I wouldn't hope to find any files I might have left around outside of my expected territory. First level sub-directories of / that were user created and not, regular dirs, might also be left but I haven't verified that yet.

Most important of all, be patient, give some time for others to look at things and wait for some agreement from at least a couple of posters on the course of action before you follow it. I realise it's hard to wait when you are worried about your data. There would be nothing wrong with you waiting until you have backups of important files. You could also get help with that issue if you didn't describe it in general terms, what "permission" problems, where were you trying to save the files, how did you have that location mounted.

Be of good courage, you have, at least, two very capable users helping you, if you stick with it, I expect success.

---

### Post by coffeecat on 2011-02-27
> **Rubi1200 said:**
> The other possibility, before trying to reinstall GRUB, might be to do either an fsck and/or chroot to run update/upgrade commands.

Yes. Doing an apt-get update/upgrade while in the chroot seems like a good idea, although QLee's suggestion of dist-upgrade rather than upgrade is a good one. A dist-upgrade should sort out any dependency discrepancies. Of course, the OP might prefer the option of a clean install once the data has been backed up.

I think I'll hold on any other suggestions until the OP has clarified what the circumstances were when they got the permissions errors, as QLee mentions. If we can sort out backing up the data without running into permissions issues, then the way may be clear for the OP to decide whether to try to repair the current installation or whether to re-install. 

@MibunoOokami, just to build on what QLee asked: When you opened a 'gksudo nautilus' file browser in the live CD, are you sure you navigated to your home folder on sda5 in your internal drive? It's easy to get lost. Also, what was the nature of the medium you were trying to backup to? USB drive? How was it formatted? Sorry if you've answered any of this and I've missed it but I'm mightily puzzled as to how a 'gksudo nautilus' would fail you.

---

### Post by MibunoOokami on 2011-02-27
Thanks for all the replies. I don't believe I ever changed any file permissions as it's never been something I've worried about. I am 100% positive I made it to my home folder. Once I have my particular files saved I don't mind whether I do a fresh reinstall or gain a little education on fixing whatever has gone wrong. I apologize if I came across as being in a hurry while I know my data isn't going anywhere I just can't stand using windows but I will put up with it for now.
I think I have answered the main questions directed at me if there's anything I have forgotten please let me know. I realize I am not as experienced as all of you but I had a thought which may be relevant, could it be that my live CD has some kind of error which is preventing me from saving those files?

Thanks again everyone.

---

### Post by coffeecat on 2011-02-27
> **MibunoOokami said:**
> I think I have answered the main questions directed at me if there's anything I have forgotten please let me know.

Yes. :wink: What was the medium you were trying to save to and was it formatted FAT32, NTFS, ext3/4 or something else? If it was formatted ext2/3/4 and you didn't open a second gksudo nautilus browser, that might cause write problems, but not necessarily the errors you described.

> **MibunoOokami said:**
> could it be that my live CD has some kind of error which is preventing me from saving those files?

A bad CD is always a possibility. I've had them on occasions even with all the normal precautions. Did you check the md5sum of the downloaded ISO? Did you burn the CD at a low speed? These are the two most important things to consider.

Don't worry if you're finding this difficult. Everyone who has contributed agrees that it is complicated, to use QLee's word. We'll get there in the end. :)

---

### Post by Rubi1200 on 2011-02-27
This is the approach I would suggest:

1. use another LiveCD like Slax or Knoppix to try and save your data. Unlike the Ubuntu CD, they don't try and auto-mount partitions (which may help with the permissions issue)

2. use a chroot to first run some housecleaning and upgrade commands, including dist-upgrade

3. assuming no errors or other problems, reinstall GRUB from the chroot

4. reboot and keep fingers crossed

coffeecat and QLee, what do you guys think?

---

### Post by QLee on 2011-02-27
[QUOTE=Rubi1200]
coffeecat and QLee, what do you guys think?[/QUOTE]

Yeah, some way to get those important files saved is the safest way to proceed and seems to satisfy the OP.

Personally, I've not had a problem using an Ubuntu live CD to grab files from a non-booting install but if what is available doesn't work then a Koppix or other live CD option would be worth trying if the OP has a connection with good bandwidth. Maybe the answer to coffeecat's questions will shed some light on the permission issue.

---

### Post by MibunoOokami on 2011-02-27
> **coffeecat said:**
> Yes. :wink: What was the medium you were trying to save to and was it formatted FAT32, NTFS, ext3/4 or something else? If it was formatted ext2/3/4 and you didn't open a second gksudo nautilus browser, that might cause write problems, but not necessarily the errors you described.

Quite right I had a feeling I forgot something. The medium is an external HDD formatted in NTFS format I believe it was as that is most compatible with both Linux and Windows as I understand it. I think I may have just realized something after reading this part of your post. Was I supposed to open the storage device through nautilus as well? I had only accessed my files then tried saving by clicking on the drive icon not via nautilus. I will try that shortly so that we can perhaps take a step forward.


> **coffeecat said:**
> 
A bad CD is always a possibility. I've had them on occasions even with all the normal precautions. Did you check the md5sum of the downloaded ISO? Did you burn the CD at a low speed? These are the two most important things to consider.

Don't worry if you're finding this difficult. Everyone who has contributed agrees that it is complicated, to use QLee's word. We'll get there in the end. :)

No I didn't check the md5sum this time, forgot completely about it

---

### Post by MibunoOokami on 2011-02-27
Couldn't edit my last post for some reason kept being told not enough characters so adding edit in new post not intentionally bumping this thread.

edit: Tried this (opening 2 nautilus windows to save files) but still didn't work got a message telling me  'destination is read only' not sure why that is. I have a very slow  internet connection due to heaps of congestion after a recent earthquake  so downloading another ISO will take time. If I can be given a link to  one of the two different OS that were mentioned I can try download and  see what happens from there.

---

### Post by fabricator4 on 2011-02-27
> **Rubi1200 said:**
> @fabricator4: with all due respect, but the OP already said that he is having difficulties copying the data because of permissions issues, explainable, perhaps, if coffeecat is right because of an upgrade gone wrong.

My bad, for coming in late.

Still look for the direct approach though, if all else fails, how about using a recovery program to get the data off the HDD.  Testdisk doesn't even need to have the HDD mounted does it?  If the file system is intact you'd hope that it would be relatively simple to get the relevant files backed up.  Tedious perhaps, but maybe worth trying as a last resort before giving up.

Chris.

---

### Post by MibunoOokami on 2011-02-28
I tried one more futile attempt at copying the files using nautilus and spotted something happening in terminal each time I clicked a folder I have coded it below thinking it is important

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ gksudo nautilus
Initializing nautilus-gdu extension

** (nautilus:6705): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '6705'

(nautilus:6705): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:6705): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs


(nautilus:6705): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:6705): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:6705): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.




```

---

### Post by coffeecat on 2011-02-28
> **MibunoOokami said:**
> Quite right I had a feeling I forgot something. The medium is an external HDD formatted in NTFS format I believe it was as that is most compatible with both Linux and Windows as I understand it. 

NTFS should automount read-write and you shouldn't need a root (gksudo) nautilus browser to write to it. If you are consistently getting a read-only error with a mounted NTFS filesystem then either the filesystem needs checking in Windows, or you do have a faulty ISO/CD. It will interesting to see what happens once you've downloaded a fresh ISO or different live distro.

> **MibunoOokami said:**
> I tried one more futile attempt at copying the files using nautilus and spotted something happening in terminal each time I clicked a folder I have coded it below thinking it is important

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ gksudo nautilus
Initializing nautilus-gdu extension

** (nautilus:6705): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '6705'

(nautilus:6705): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:6705): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs


(nautilus:6705): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:6705): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:6705): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.




```

I've often seen blood-curdling messages like that after opening nautilus with gksudo, and it's gone on to work fine nevertheless. They either mean nothing much in particular or you do have a bad CD/ISO so, again, it will be interesting to see what happens when you have a fresh live CD to try.

---

### Post by MibunoOokami on 2011-03-01
I checked the md5sum and it's OK so will download a different distro and see what happens then. Have a slow connection so might be a while before I post again.

---

### Post by Rubi1200 on 2011-03-01
As I mentioned in a previous post, give either Slax and/or Knoppix a try. 

If you are unsure of anything at any point, stop and ask us first.

We are all waiting and hoping this will be resolved soon.

---

### Post by MibunoOokami on 2011-03-01
> **Rubi1200 said:**
> As I mentioned in a previous post, give either Slax and/or Knoppix a try. 
 
Just finished downloading slax as per your earlier mention of it. Said was going to take 4 days to download coz was going at 1kbs then a few hours later I noticed it was finished so must have had a boost of speed which is lucky. I'm just going to do the md5sum check then boot it up.
 
edit: OK checked md5sum no problem, tried to burn ISO but it didn't work probably because I had to use a portable cd/dvd burner since my main one has the live cd in it and my other computer doesn't have a cd burner and doesn't like the portable one.
I've been thinking what I can do to get around this and am wondering is there something I can do or a command I can run to get ubuntu 10.10 to boot from the external drive I installed it on? I just need it long enough to use my main cd burner to burn the ISO and then play with Slax. Thanks

---

### Post by coffeecat on 2011-03-01
A couple of things:

If you want to try to boot 10.10 from the external drive, you'll need to run the bootscript again from the live CD but with the external drive attached and switched on. Without that output  we won't know how your BIOS is designating the drives or what you'll need to do from the CD. Make sure the external drive is switched on before you switch the computer on to boot from the CD. You may have to adjust the BIOS boot order.

I'm trying to get my head around all the details in this thread. It seems from what you say that the Ubuntu live CD ISO is OK. One other thing to check the integrity of the CD itself. As soon as the purple screen with two small icons at the bottom of the screen appears, tap the spacebar. Choose your language and then you'll see the live CD menu. Choose 'check CD' or words to that effect. You could still have a bad burn from a good ISO, so it's worth doing that as well.

Having said that, you say you are getting a read-only error when you try to copy to your NTFS external drive. That simply shouldn't happen - period. You need to check the external drive in Windows, even if it works with Windows. Use chkdsk from the command prompt or there is a GUI disc checker that you can use but offhand I can't remember where to find it.

---

### Post by MibunoOokami on 2011-03-01
> **coffeecat said:**
> A couple of things:
 
If you want to try to boot 10.10 from the external drive, you'll need to run the bootscript again from the live CD but with the external drive attached and switched on. Without that output we won't know how your BIOS is designating the drives or what you'll need to do from the CD. Make sure the external drive is switched on before you switch the computer on to boot from the CD. You may have to adjust the BIOS boot order.
 
It's a shame I didn't think about this sooner as I have just discovered that the OS on my external drive is device ff93f56e-7de54879-a034-f921c27bdf72. ](*,) Actually I think that may have been suggested earlier. Sorry folks.
Here is the new bootscript ```
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd
sda2: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
sda3: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  
sda5: _________________________________________________________________________
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab
sda6: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdb1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sdb2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  
sdb5: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sdb6: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1               2,048    22,388,735    22,386,688  27 Hidden HPFS/NTFS
/dev/sda2    *     22,388,736   128,003,970   105,615,235   7 HPFS/NTFS
/dev/sda3         128,005,981   768,147,974   640,141,994   5 Extended
/dev/sda5         128,005,983   757,866,374   629,860,392  83 Linux
/dev/sda6         757,866,438   768,147,974    10,281,537  82 Linux swap / Solaris

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 40.0 GB, 40007761920 bytes
64 heads, 32 sectors/track, 38154 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdb1                  32    64,747,234    64,747,203   c W95 FAT32 (LBA)
/dev/sdb2          64,747,518    78,139,391    13,391,874   5 Extended
/dev/sdb5          64,747,520    77,457,407    12,709,888  83 Linux
/dev/sdb6          77,459,456    78,139,391       679,936  82 Linux swap / Solaris

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/sda1        388A35028A34BDE6                       ntfs       Recovery                      
/dev/sda2        D0AC5FB4AC5F9436                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        f17d068f-b1cd-4864-87bf-dcc87924a63f   ext3                                     
/dev/sda6        32ff26f8-f948-4e09-b297-6eda46b51d37   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        AD2B-54D5                              vfat                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        ff93f56e-7de5-4879-a034-f921c27bdf72   ext4                                     
/dev/sdb6        aac421ff-4f1d-4f43-8c77-4364cfc0676e   swap                                     
/dev/sdb: PTTYPE="dos" 
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /media/ff93f56e-7de5-4879-a034-f921c27bdf72 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/AD2B-54D5         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

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
default  0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout  10
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
# title  Windows 95/98/NT/2000
# root  (hd0,0)
# makeactive
# chainloader +1
#
# title  Linux
# root  (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro
## default grub root device
## e.g. groot=(hd0,0)
# groot=f17d068f-b1cd-4864-87bf-dcc87924a63f
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
title  Ubuntu 9.10, kernel 2.6.31-22-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-22-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-22-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-22-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-22-generic
title  Ubuntu 9.10, kernel 2.6.31-21-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-21-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-21-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-21-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-21-generic
title  Ubuntu 9.10, kernel 2.6.31-20-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-20-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-20-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-20-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-20-generic
title  Ubuntu 9.10, kernel 2.6.31-19-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-19-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-19-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-19-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-19-generic
title  Ubuntu 9.10, kernel 2.6.31-17-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-17-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-17-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-17-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-17-generic
title  Ubuntu 9.10, kernel 2.6.31-16-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-16-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-16-generic
title  Ubuntu 9.10, kernel 2.6.31-15-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-15-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-15-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-15-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-15-generic
title  Ubuntu 9.10, kernel 2.6.31-14-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-14-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-14-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-14-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-14-generic
title  Ubuntu 9.10, kernel 2.6.28-16-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.28-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.28-16-generic
quiet
title  Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.28-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.28-16-generic
title  Ubuntu 9.10, memtest86+
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/memtest86+.bin
quiet
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title  Windows Vista (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title  Windows Vista (loader)
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title  Ubuntu 8.04.2, kernel 2.6.24-24-generic (on /dev/sda5)
root  (hd0,4)
kernel  /boot/vmlinuz-2.6.24-24-generic root=UUID=09e0b212-7601-48f9-8f8e-82ce7f237f26 ro quiet splash 
initrd  /boot/initrd.img-2.6.24-24-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title  Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode) (on /dev/sda5)
root  (hd0,4)
kernel  /boot/vmlinuz-2.6.24-24-generic root=UUID=09e0b212-7601-48f9-8f8e-82ce7f237f26 ro single 
initrd  /boot/initrd.img-2.6.24-24-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title  Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda5)
root  (hd0,4)
kernel  /boot/vmlinuz-2.6.24-23-generic root=UUID=09e0b212-7601-48f9-8f8e-82ce7f237f26 ro quiet splash 
initrd  /boot/initrd.img-2.6.24-23-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title  Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda5)
root  (hd0,4)
kernel  /boot/vmlinuz-2.6.24-23-generic root=UUID=09e0b212-7601-48f9-8f8e-82ce7f237f26 ro single 
initrd  /boot/initrd.img-2.6.24-23-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title  Ubuntu 8.04.2, memtest86+ (on /dev/sda5)
root  (hd0,4)
kernel  /boot/memtest86+.bin  
savedefault
boot

=============================== sda5/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=32ff26f8-f948-4e09-b297-6eda46b51d37 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=================== sda5: Location of files loaded by Grub: ===================

  76.0GB: boot/grub/menu.lst
  76.0GB: boot/grub/stage2
  76.0GB: boot/initrd.img-2.6.28-16-generic
  76.1GB: boot/initrd.img-2.6.31-14-generic
  76.0GB: boot/initrd.img-2.6.31-15-generic
  76.0GB: boot/initrd.img-2.6.31-16-generic
  81.5GB: boot/initrd.img-2.6.31-17-generic
  77.5GB: boot/initrd.img-2.6.31-19-generic
  76.0GB: boot/initrd.img-2.6.31-20-generic
  76.1GB: boot/initrd.img-2.6.31-21-generic
  76.1GB: boot/initrd.img-2.6.31-22-generic
  76.0GB: boot/vmlinuz-2.6.28-16-generic
  76.1GB: boot/vmlinuz-2.6.31-14-generic
  76.1GB: boot/vmlinuz-2.6.31-15-generic
  76.1GB: boot/vmlinuz-2.6.31-16-generic
  76.1GB: boot/vmlinuz-2.6.31-17-generic
  76.1GB: boot/vmlinuz-2.6.31-19-generic
  76.0GB: boot/vmlinuz-2.6.31-20-generic
  76.0GB: boot/vmlinuz-2.6.31-21-generic
  76.0GB: boot/vmlinuz-2.6.31-22-generic
  76.1GB: initrd.img
  76.1GB: initrd.img.old
  76.0GB: vmlinuz
  76.0GB: vmlinuz.old
=========================== sdb5/boot/grub/grub.cfg: ===========================
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi
function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  insmod vbe
  insmod vga
}
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set ff93f56e-7de5-4879-a034-f921c27bdf72
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set ff93f56e-7de5-4879-a034-f921c27bdf72
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###
### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos5)'
 search --no-floppy --fs-uuid --set ff93f56e-7de5-4879-a034-f921c27bdf72
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ff93f56e-7de5-4879-a034-f921c27bdf72 ro   quiet splash
 initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos5)'
 search --no-floppy --fs-uuid --set ff93f56e-7de5-4879-a034-f921c27bdf72
 echo 'Loading Linux 2.6.35-22-generic ...'
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ff93f56e-7de5-4879-a034-f921c27bdf72 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos5)'
 search --no-floppy --fs-uuid --set ff93f56e-7de5-4879-a034-f921c27bdf72
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos5)'
 search --no-floppy --fs-uuid --set ff93f56e-7de5-4879-a034-f921c27bdf72
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
 insmod part_msdos
 insmod ntfs
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 388a35028a34bde6
 chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
 insmod part_msdos
 insmod ntfs
 set root='(hd0,msdos2)'
 search --no-floppy --fs-uuid --set d0ac5fb4ac5f9436
 drivemap -s (hd0) ${root}
 chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-22-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-22-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-21-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-21-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-20-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-20-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-19-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-19-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-17-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-17-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-15-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-15-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.28-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.28-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
=============================== sdb5/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=ff93f56e-7de5-4879-a034-f921c27bdf72 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=aac421ff-4f1d-4f43-8c77-4364cfc0676e none            swap    sw              0       0
=================== sdb5: Location of files loaded by Grub: ===================

  38.0GB: boot/grub/core.img
  38.0GB: boot/grub/grub.cfg
  34.3GB: boot/initrd.img-2.6.35-22-generic
  38.0GB: boot/vmlinuz-2.6.35-22-generic
  34.3GB: initrd.img
  38.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader  on sda3
00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 28 e8 8a 25 00 fe  |..........(..%..|
000001d0  ff ff 05 fe ff ff 2a e8  8a 25 80 e2 9c 00 00 00  |......*..%......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
Unknown BootLoader  on sdb2
00000000  72 61 74 69 6f 6e 73 20  2a 2f 0a 0a 09 63 68 61  |rations */...cha|
00000010  72 20 72 65 61 64 5f 74  72 61 63 6b 3b 09 09 2f  |r read_track;../|
00000020  2a 20 75 73 65 20 72 65  61 64 74 72 61 63 6b 20  |* use readtrack |
00000030  64 75 72 69 6e 67 20 70  72 6f 62 69 6e 67 3f 20  |during probing? |
00000040  2a 2f 0a 0a 2f 2a 0a 20  2a 20 41 75 74 6f 2d 64  |*/../*. * Auto-d|
00000050  65 74 65 63 74 69 6f 6e  2e 20 45 61 63 68 20 64  |etection. Each d|
00000060  72 69 76 65 20 74 79 70  65 20 68 61 73 20 65 69  |rive type has ei|
00000070  67 68 74 20 66 6f 72 6d  61 74 73 20 77 68 69 63  |ght formats whic|
00000080  68 20 61 72 65 0a 20 2a  20 75 73 65 64 20 69 6e  |h are. * used in|
00000090  20 73 75 63 63 65 73 73  69 6f 6e 20 74 6f 20 74  | succession to t|
000000a0  72 79 20 74 6f 20 72 65  61 64 20 74 68 65 20 64  |ry to read the d|
000000b0  69 73 6b 2e 20 49 66 20  74 68 65 20 46 44 43 20  |isk. If the FDC |
000000c0  63 61 6e 6e 6f 74 20 6c  6f 63 6b 20 6f 6e 74 6f  |cannot lock onto|
000000d0  0a 20 2a 20 74 68 65 20  64 69 73 6b 2c 20 74 68  |. * the disk, th|
000000e0  65 20 6e 65 78 74 20 66  6f 72 6d 61 74 20 69 73  |e next format is|
000000f0  20 74 72 69 65 64 2e 20  54 68 69 73 20 75 73 65  | tried. This use|
00000100  73 20 74 68 65 20 76 61  72 69 61 62 6c 65 20 27  |s the variable '|
00000110  70 72 6f 62 69 6e 67 27  2e 0a 20 2a 2f 0a 09 73  |probing'.. */..s|
00000120  68 6f 72 74 20 61 75 74  6f 64 65 74 65 63 74 5b  |hort autodetect[|
00000130  38 5d 3b 09 09 2f 2a 20  61 75 74 6f 64 65 74 65  |8];../* autodete|
00000140  63 74 65 64 20 66 6f 72  6d 61 74 73 20 2a 2f 0a  |cted formats */.|
00000150  09 0a 09 69 6e 74 20 63  68 65 63 6b 66 72 65 71  |...int checkfreq|
00000160  3b 20 2f 2a 20 68 6f 77  20 6f 66 74 65 6e 20 73  |; /* how often s|
00000170  68 6f 75 6c 64 20 74 68  65 20 64 72 69 76 65 20  |hould the drive |
00000180  62 65 20 63 68 65 63 6b  65 64 20 66 6f 72 20 64  |be checked for d|
00000190  69 73 6b 20 0a 09 09 09  2a 20 63 68 61 6e 67 65  |isk ....* change|
000001a0  73 20 2a 2f 0a 09 69 6e  74 20 6e 61 74 69 76 65  |s */..int native|
000001b0  5f 66 6f 72 6d 61 74 3b  20 2f 2a 20 6e 61 00 3f  |_format; /* na.?|
000001c0  e0 ff 83 3f e0 ff 02 00  00 00 00 f0 c1 00 00 3f  |...?...........?|
000001d0  e0 ff 05 3f e0 ff 02 f0  c1 00 00 68 0a 00 00 00  |...?.......h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

 
> **coffeecat said:**
> I'm trying to get my head around all the details in this thread. It seems from what you say that the Ubuntu live CD ISO is OK. One other thing to check the integrity of the CD itself. As soon as the purple screen with two small icons at the bottom of the screen appears, tap the spacebar. Choose your language and then you'll see the live CD menu. Choose 'check CD' or words to that effect. You could still have a bad burn from a good ISO, so it's worth doing that as well.
 
Yes, the ISO is fine and I just checked the disc for defects and it too is fine.
 
> **coffeecat said:**
> Having said that, you say you are getting a read-only error when you try to copy to your NTFS external drive. That simply shouldn't happen - period. You need to check the external drive in Windows, even if it works with Windows. Use chkdsk from the command prompt or there is a GUI disc checker that you can use but offhand I can't remember where to find it.
 
Yes, got read only error trying to transfer a file. Tried the chkdsk command but it didn't work assuming I just had to type chkdsk and nothing else in command prompt. I don't know anything about a GUI disc checker so not sure what to do from here, perhaps don't need to do anything depending on what is discovered from the bootscript.

---

### Post by coffeecat on 2011-03-03
> **MibunoOokami said:**
> 
Yes, got read only error trying to transfer a file. Tried the chkdsk command but it didn't work assuming I just had to type chkdsk and nothing else in command prompt. I don't know anything about a GUI disc checker so not sure what to do from here, perhaps don't need to do anything depending on what is discovered from the bootscript.

I really think you need to have another go at checking that NTFS filesystem. Ubuntu will not mount a damaged filesystem at all, but mounting it read-only does suggest a problem in the filesystem, even if it is writeable in Windows. There may not be a problem, but it doesn't hurt to try checking it and if Windows does find and repair a problem, then you should be able to write to it from the live CD. 

In Windows 7 (I presume it's the same in Vista) simply open a Computer Explorer window and right-click on whichever drive the external drive is showing as. Choose properties > Tools tab and click on "Check now".

Or if you want to try chkdsk again, there's no point in trying to run it without any arguments. See here for more:

[http://searchenterprisedesktop.techtarget.com/feature/How-to-run-the-Chkdsk-utility-in-Windows-Vista](http://searchenterprisedesktop.techtarget.com/feature/How-to-run-the-Chkdsk-utility-in-Windows-Vista)

But to your new bootscript output. The reason that I strongly urge you to check the external NTFS drive you've been trying to copy data to first, is that if you re-install grub so that Ubuntu Maverick can boot from your 40GB external drive, you will only be able to boot if the external drive is attached. If you want to go ahead with this, then this is what you need to do.

Your Ubuntu 10.10 is on partition #5 of sdb (the 40GB external) = sdb5. The grub menu in 10.10 has entries for Vista, so once you have done the below, you will be able to boot Vista with the external drive attached. **However**...  Be aware that the entries for Vista and the recovery partition are the wrong way around - this is a known bug. Simply choose "recovery environment" for Vista, and "Vista loader" for the recovery environment. :? There are also entries for "Ubuntu 9.10" on sda5 so, with luck, you might be able to boot into your hybrid half-upgraded Karmic/Lucid on sda5.

This is what you do. Boot up with the Maverick/10.10 live CD with the external drive attached and switched on. **Do not use another version of Ubuntu. Do not use a live CD for another distro.** Open a terminal, and:

```
sudo mount /dev/sdb5 /mnt
```Then...

```
sudo grub-install --root-directory=/mnt /dev/sda
```Yes, /dev/sda is correct. We want to get grub into the mbr of sda looking to sdb5 for the rest of grub.

I'll pm Rubi1200 now to ask him to double-check what I've just written. You might want to hold off for a bit.

---

### Post by Alexd4 on 2011-03-03
deleted

---

### Post by Rubi1200 on 2011-03-03
I agree with coffeecat that you should try to run chkdsk and then follow the exact instructions to reinstall GRUB to the MBR of sda.

If there are errors or any other problem, stop what you are doing and report back here first.

Good luck!

---

### Post by QLee on 2011-03-03
Here's my take on your suggestion coffeecat.

I do not see any flaws in the logic of what you are suggesting. 

Following that method should leave MibunoOokami with a system that will  boot to the 10.10 partition and it should allow booting to Windows to do  the disk check on the ntfs partition which will hopefully explain why  MibunoOokami isn't able to write to it. It might even boot the failed  update system if  MibunoOokami is lucky and then could work from there.  This should be a reasonable path to getting copies of important files  backed up and then MibunoOokami can decide on whether to try and finish  the upgrade on sda5 from a chroot; or do an install over-writing (no  format) sda5; or a fresh install on sda5. A safe, if somewhat lengthy  procedure.

---

### Post by MibunoOokami on 2011-03-03
I'm starting to feel a bit stupid or insane now. I did the disc check using my other PC that has XP on it, by right clicking the drive, properties, tools and then check disc. It only took about 30 seconds and just pops up with a little window saying check complete and isn't showing any comments such as errors, so I am assuming the disc/disk is fine, but I seriously did get a message saying it is read only when trying to copy a certain file.
I'm a little confused as to why the 40GB drive is showing entries for Vista because Vista is/was on the built in HDD which I assume is what you refer to as MBR. The live CD did the installation so I don't understand why entries for Vista are now on the 40GB drive or something went wrong with grub.
Booting from the 40GB drive looks like it could be complicated and given what has gone wrong with the install of Maverick onto an external drive without my help, I'm a little reluctant to try boot from the 40GB in case I totally screw things up beyond repair..... I'm going to go away and give this some thought, I might be safer just to try fix this problem from chroot because right now I feel I'm not going to be able to back up the files that I need.

---

### Post by MibunoOokami on 2011-03-03
OK I thought about it long enough and ran the commands given by coffee cat. A message came up saying 'Installation finished. No error reported.' That sounds like good news, I assume I can remove the live cd and try booting and see what happens, so that is what I will do.
Oh I almost forgot I tried the chkdsk following the commands in the link provided but again got a message rejecting the chkdsk part of the command. I don't know what's going on there, but the other way I checked it from preferences etc didn't bring up any problems so I am going to assume it's OK and that something strange is happening with the live CD even though it says it burned fine.
 
edit:](*,) That did not work still getting grub rescue message. I don't understand this at all.
edit again: I calmed down a bit and am thinking there might be some more commands or something to follow or at least something more involved than removing the live CD and rebooting. I will try be more patient and await your responses. The time difference(s) don't help.

---

### Post by coffeecat on 2011-03-03
> **MibunoOokami said:**
> I'm a little confused as to why the 40GB drive is showing entries for Vista because Vista is/was on the built in HDD which I assume is what you refer to as MBR.

I would have been confused if the installation on the 40GB drive (sdb) did **not** show Vista. When you installed Maverick to sdb5 the os-prober would have scanned all drives, including sda, and would have detected Vista on sda. The mbr is not the internal HD. The mbr (master boot record) is the first 512 bytes of a hard drive. If you look in your bootscript you'll see that there's some legacy grub code in the mbr of sdb, presumably left over from an earlier use of that drive. It won't matter that it's there - it will be untouched the way you are using the drives at the moment.

The first 400-440 bytes of the mbr contains boot code, either Windows boot code or stage 1 of grub. The rest contains the partition table.

> **MibunoOokami said:**
> edit:](*,) That did not work still getting grub rescue message. I don't understand this at all.

Things to check:

Did you use the commands exactly as I posted them: sd[COLOR=Red]b[/COLOR]5 in the first command; sd[COLOR=Red]a[/COLOR] in the second?

Having reinstalled grub, did you remember to have the external drive switched on when you tried to boot up?

Did you change the boot order in the BIOS? Don't.

Are you getting the same device number in the grub error? This one:

```

ERROR: No such device ff93f56e-7de54879-a034-f921c27bdf72

GRUB RESCUE>
```

---

### Post by MibunoOokami on 2011-03-03
> **coffeecat said:**
> I would have been confused if the installation on the 40GB drive (sdb) did **not** show Vista. When you installed Maverick to sdb5 the os-prober would have scanned all drives, including sda, and would have detected Vista on sda. The mbr is not the internal HD. The mbr (master boot record) is the first 512 bytes of a hard drive. If you look in your bootscript you'll see that there's some legacy grub code in the mbr of sdb, presumably left over from an earlier use of that drive. It won't matter that it's there - it will be untouched the way you are using the drives at the moment.
 
The first 400-440 bytes of the mbr contains boot code, either Windows boot code or stage 1 of grub. The rest contains the partition table.
 
OK that's good to know.
 
 
> **coffeecat said:**
>  
Things to check:
 
Did you use the commands exactly as I posted them: sd[COLOR=red]b[/COLOR]5 in the first command; sd[COLOR=red]a[/COLOR] in the second?

 
Yes copied exactly and double checked before hitting enter.
 
> **coffeecat said:**
> 
Having reinstalled grub, did you remember to have the external drive switched on when you tried to boot up?
 
There is no on/off switch, the blue light was on and the drives showed on desktop.
 
> **coffeecat said:**
> Did you change the boot order in the BIOS? Don't. 
 
No, I don't know how and didn't look through this thread again to see if it's mentioned, not that the thought even crossed my mind.
 
> **coffeecat said:**
> Are you getting the same device number in the grub error? This one:
 
```

ERROR: No such device ff93f56e-7de54879-a034-f921c27bdf72
 
GRUB RESCUE>
```
 
Yes same message.

---

### Post by coffeecat on 2011-03-04
> **coffeecat said:**
> Are you getting the same device number in the grub error? This one:

```

ERROR: No such device ff93f56e-7de54879-a034-f921c27bdf72

GRUB RESCUE>
```

> **MibunoOokami said:**
> 
 
Yes same message.

That's the UUID of sdb5. Are you sure you are seeing "ff93f56e-7de54879-a034-f921c27bdf72"? If you are, that means  that grub can't detect the partition, which means that the BIOS didn't detect it either. Put it in another USB socket and try again.

> **MibunoOokami said:**
> There is no on/off switch, the blue light was on and the drives showed on desktop.

What do you mean, "drives showed on desktop"? If you are getting that message, then you won't be able to boot at all, so there will be no desktop to show anything on.

---

### Post by MibunoOokami on 2011-03-04
> **coffeecat said:**
> That's the UUID of sdb5. Are you sure you are seeing "ff93f56e-7de54879-a034-f921c27bdf72"? If you are, that means that grub can't detect the partition, which means that the BIOS didn't detect it either. Put it in another USB socket and try again.
 
I am absolutely sure I am seeing those numbers, I even had a friend read them out so there would be no uncertainty. Since seeing your post I have tried the drive in all the USB ports and the exact same error message keeps coming up.
 
 
 
> **coffeecat said:**
> What do you mean, "drives showed on desktop"? If you are getting that message, then you won't be able to boot at all, so there will be no desktop to show anything on.
 
I mean when I had the live CD in and running in order to run the commands you listed before, I'm sure both the Ubuntu partition and the storage partition icons were displayed on the desktop. Don't tell me that was not meant to happen either!?

---

### Post by coffeecat on 2011-03-04
> **MibunoOokami said:**
> I mean when I had the live CD in and running in order to run the  commands you listed before, I'm sure both the Ubuntu partition and the  storage partition icons were displayed on the desktop. Don't tell me  that was not meant to happen either!?

From the live CD, partitions will show on the desktop only if you mount them from the Places menu, or from the terminal. But only if they are mounted in a folder in /media. The command to mount sdb5 was:

```
sudo mount /dev/sdb5 /mnt
```I.e, you mounted sdb5 in /mnt and a desktop icon does not appear when a partition is mounted in /mnt.

> **MibunoOokami said:**
> I am absolutely sure I am seeing those numbers, I even had a friend read them out so there would be no uncertainty. Since seeing your post I have tried the drive in all the USB ports and the exact same error message keeps coming up.

If you are seeing those numbers, then grub cannot find sdb5, which means that the BIOS has not seen it - but I find that most extraordinary. Clearly sdb5 was detectable when you ran the grub-install commands I posted for you. Attach the external drive, boot up the live CD and run the bootscript again.

Perhaps Rubi1200 or QLee can comment because this makes absolutely no sense to me. We seem to be back where you were at the beginning. I wonder if there is some BIOS oddity in your machine that is getting in the way. Again, I can only hope that Rubi1200 or QLee can shed some light that I haven't seen.

I know you must be getting fed up with this, but let's take stock. One option was to rescue your data from sda5 and then do a fresh installation of Ubuntu to sda5. When you tried this before, you got permissions errors in the live CD trying to copy your files. But since then we've determined that the live CD is OK and that the external NTFS drive is OK. Try booting from the live CD again to attempt your data backup. To be clear: you need a "gksudo nautilus" browser to copy **from** your sda5 home folder. (That is because your UID in your account in sda5 is 1000, but the live user "ubuntu" has a UID of 99 - if I remember correctly, certainly different from 1000.)  But you don't need a "gksudo nautilus" browser to copy **to**  the NTFS drive - use the one that pops up automatically when you plug the NTFS drive in.

---

### Post by MibunoOokami on 2011-03-04
First I will check to see if the drive did auto mount or for some unknown reason I mounted it myself, if it was auto mounted I will do the bootscript again, if not auto mounted then I will re-run those earlier commands, I'm sure running them again won't hurt. Then go from there.
 
edit: I checked again, no auto mount so must have been me, re-entered commands, no error reported just as before, but still getting grub error with same long @$$ name.
Here is the bootscript again done immediately after restart. 
```
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd
sda2: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
sda3: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  
sda5: _________________________________________________________________________
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab
sda6: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdb1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sdb2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  
sdb5: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sdb6: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1               2,048    22,388,735    22,386,688  27 Hidden HPFS/NTFS
/dev/sda2    *     22,388,736   128,003,970   105,615,235   7 HPFS/NTFS
/dev/sda3         128,005,981   768,147,974   640,141,994   5 Extended
/dev/sda5         128,005,983   757,866,374   629,860,392  83 Linux
/dev/sda6         757,866,438   768,147,974    10,281,537  82 Linux swap / Solaris

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 40.0 GB, 40007761920 bytes
64 heads, 32 sectors/track, 38154 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdb1                  32    64,747,234    64,747,203   c W95 FAT32 (LBA)
/dev/sdb2          64,747,518    78,139,391    13,391,874   5 Extended
/dev/sdb5          64,747,520    77,457,407    12,709,888  83 Linux
/dev/sdb6          77,459,456    78,139,391       679,936  82 Linux swap / Solaris

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/sda1        388A35028A34BDE6                       ntfs       Recovery                      
/dev/sda2        D0AC5FB4AC5F9436                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        f17d068f-b1cd-4864-87bf-dcc87924a63f   ext3                                     
/dev/sda6        32ff26f8-f948-4e09-b297-6eda46b51d37   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        AD2B-54D5                              vfat                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        ff93f56e-7de5-4879-a034-f921c27bdf72   ext4                                     
/dev/sdb6        aac421ff-4f1d-4f43-8c77-4364cfc0676e   swap                                     
/dev/sdb: PTTYPE="dos" 
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/AD2B-54D5         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda5        /media/f17d068f-b1cd-4864-87bf-dcc87924a63f ext3       (rw,nosuid,nodev,uhelper=udisks)

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
default  0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout  10
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
# title  Windows 95/98/NT/2000
# root  (hd0,0)
# makeactive
# chainloader +1
#
# title  Linux
# root  (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro
## default grub root device
## e.g. groot=(hd0,0)
# groot=f17d068f-b1cd-4864-87bf-dcc87924a63f
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
title  Ubuntu 9.10, kernel 2.6.31-22-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-22-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-22-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-22-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-22-generic
title  Ubuntu 9.10, kernel 2.6.31-21-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-21-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-21-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-21-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-21-generic
title  Ubuntu 9.10, kernel 2.6.31-20-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-20-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-20-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-20-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-20-generic
title  Ubuntu 9.10, kernel 2.6.31-19-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-19-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-19-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-19-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-19-generic
title  Ubuntu 9.10, kernel 2.6.31-17-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-17-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-17-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-17-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-17-generic
title  Ubuntu 9.10, kernel 2.6.31-16-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-16-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-16-generic
title  Ubuntu 9.10, kernel 2.6.31-15-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-15-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-15-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-15-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-15-generic
title  Ubuntu 9.10, kernel 2.6.31-14-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-14-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.31-14-generic
quiet
title  Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.31-14-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.31-14-generic
title  Ubuntu 9.10, kernel 2.6.28-16-generic
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.28-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash 
initrd  /boot/initrd.img-2.6.28-16-generic
quiet
title  Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/vmlinuz-2.6.28-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro  single
initrd  /boot/initrd.img-2.6.28-16-generic
title  Ubuntu 9.10, memtest86+
uuid  f17d068f-b1cd-4864-87bf-dcc87924a63f
kernel  /boot/memtest86+.bin
quiet
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title  Windows Vista (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title  Windows Vista (loader)
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title  Ubuntu 8.04.2, kernel 2.6.24-24-generic (on /dev/sda5)
root  (hd0,4)
kernel  /boot/vmlinuz-2.6.24-24-generic root=UUID=09e0b212-7601-48f9-8f8e-82ce7f237f26 ro quiet splash 
initrd  /boot/initrd.img-2.6.24-24-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title  Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode) (on /dev/sda5)
root  (hd0,4)
kernel  /boot/vmlinuz-2.6.24-24-generic root=UUID=09e0b212-7601-48f9-8f8e-82ce7f237f26 ro single 
initrd  /boot/initrd.img-2.6.24-24-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title  Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda5)
root  (hd0,4)
kernel  /boot/vmlinuz-2.6.24-23-generic root=UUID=09e0b212-7601-48f9-8f8e-82ce7f237f26 ro quiet splash 
initrd  /boot/initrd.img-2.6.24-23-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title  Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda5)
root  (hd0,4)
kernel  /boot/vmlinuz-2.6.24-23-generic root=UUID=09e0b212-7601-48f9-8f8e-82ce7f237f26 ro single 
initrd  /boot/initrd.img-2.6.24-23-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title  Ubuntu 8.04.2, memtest86+ (on /dev/sda5)
root  (hd0,4)
kernel  /boot/memtest86+.bin  
savedefault
boot

=============================== sda5/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=32ff26f8-f948-4e09-b297-6eda46b51d37 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=================== sda5: Location of files loaded by Grub: ===================

  76.0GB: boot/grub/menu.lst
  76.0GB: boot/grub/stage2
  76.0GB: boot/initrd.img-2.6.28-16-generic
  76.1GB: boot/initrd.img-2.6.31-14-generic
  76.0GB: boot/initrd.img-2.6.31-15-generic
  76.0GB: boot/initrd.img-2.6.31-16-generic
  81.5GB: boot/initrd.img-2.6.31-17-generic
  77.5GB: boot/initrd.img-2.6.31-19-generic
  76.0GB: boot/initrd.img-2.6.31-20-generic
  76.1GB: boot/initrd.img-2.6.31-21-generic
  76.1GB: boot/initrd.img-2.6.31-22-generic
  76.0GB: boot/vmlinuz-2.6.28-16-generic
  76.1GB: boot/vmlinuz-2.6.31-14-generic
  76.1GB: boot/vmlinuz-2.6.31-15-generic
  76.1GB: boot/vmlinuz-2.6.31-16-generic
  76.1GB: boot/vmlinuz-2.6.31-17-generic
  76.1GB: boot/vmlinuz-2.6.31-19-generic
  76.0GB: boot/vmlinuz-2.6.31-20-generic
  76.0GB: boot/vmlinuz-2.6.31-21-generic
  76.0GB: boot/vmlinuz-2.6.31-22-generic
  76.1GB: initrd.img
  76.1GB: initrd.img.old
  76.0GB: vmlinuz
  76.0GB: vmlinuz.old
=========================== sdb5/boot/grub/grub.cfg: ===========================
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi
function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  insmod vbe
  insmod vga
}
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set ff93f56e-7de5-4879-a034-f921c27bdf72
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set ff93f56e-7de5-4879-a034-f921c27bdf72
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###
### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos5)'
 search --no-floppy --fs-uuid --set ff93f56e-7de5-4879-a034-f921c27bdf72
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ff93f56e-7de5-4879-a034-f921c27bdf72 ro   quiet splash
 initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos5)'
 search --no-floppy --fs-uuid --set ff93f56e-7de5-4879-a034-f921c27bdf72
 echo 'Loading Linux 2.6.35-22-generic ...'
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ff93f56e-7de5-4879-a034-f921c27bdf72 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos5)'
 search --no-floppy --fs-uuid --set ff93f56e-7de5-4879-a034-f921c27bdf72
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(hd1,msdos5)'
 search --no-floppy --fs-uuid --set ff93f56e-7de5-4879-a034-f921c27bdf72
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
 insmod part_msdos
 insmod ntfs
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 388a35028a34bde6
 chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
 insmod part_msdos
 insmod ntfs
 set root='(hd0,msdos2)'
 search --no-floppy --fs-uuid --set d0ac5fb4ac5f9436
 drivemap -s (hd0) ${root}
 chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-22-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-22-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-21-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-21-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-20-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-20-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-19-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-19-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-17-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-17-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-15-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-15-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.28-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro quiet splash
 initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/vmlinuz-2.6.28-16-generic root=UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f ro single
 initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda5)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos5)'
 search --no-floppy --fs-uuid --set f17d068f-b1cd-4864-87bf-dcc87924a63f
 linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
=============================== sdb5/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=ff93f56e-7de5-4879-a034-f921c27bdf72 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=aac421ff-4f1d-4f43-8c77-4364cfc0676e none            swap    sw              0       0
=================== sdb5: Location of files loaded by Grub: ===================

  38.0GB: boot/grub/core.img
  38.0GB: boot/grub/grub.cfg
  34.3GB: boot/initrd.img-2.6.35-22-generic
  38.0GB: boot/vmlinuz-2.6.35-22-generic
  34.3GB: initrd.img
  38.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader  on sda3
00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 28 e8 8a 25 00 fe  |..........(..%..|
000001d0  ff ff 05 fe ff ff 2a e8  8a 25 80 e2 9c 00 00 00  |......*..%......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
Unknown BootLoader  on sdb2
00000000  72 61 74 69 6f 6e 73 20  2a 2f 0a 0a 09 63 68 61  |rations */...cha|
00000010  72 20 72 65 61 64 5f 74  72 61 63 6b 3b 09 09 2f  |r read_track;../|
00000020  2a 20 75 73 65 20 72 65  61 64 74 72 61 63 6b 20  |* use readtrack |
00000030  64 75 72 69 6e 67 20 70  72 6f 62 69 6e 67 3f 20  |during probing? |
00000040  2a 2f 0a 0a 2f 2a 0a 20  2a 20 41 75 74 6f 2d 64  |*/../*. * Auto-d|
00000050  65 74 65 63 74 69 6f 6e  2e 20 45 61 63 68 20 64  |etection. Each d|
00000060  72 69 76 65 20 74 79 70  65 20 68 61 73 20 65 69  |rive type has ei|
00000070  67 68 74 20 66 6f 72 6d  61 74 73 20 77 68 69 63  |ght formats whic|
00000080  68 20 61 72 65 0a 20 2a  20 75 73 65 64 20 69 6e  |h are. * used in|
00000090  20 73 75 63 63 65 73 73  69 6f 6e 20 74 6f 20 74  | succession to t|
000000a0  72 79 20 74 6f 20 72 65  61 64 20 74 68 65 20 64  |ry to read the d|
000000b0  69 73 6b 2e 20 49 66 20  74 68 65 20 46 44 43 20  |isk. If the FDC |
000000c0  63 61 6e 6e 6f 74 20 6c  6f 63 6b 20 6f 6e 74 6f  |cannot lock onto|
000000d0  0a 20 2a 20 74 68 65 20  64 69 73 6b 2c 20 74 68  |. * the disk, th|
000000e0  65 20 6e 65 78 74 20 66  6f 72 6d 61 74 20 69 73  |e next format is|
000000f0  20 74 72 69 65 64 2e 20  54 68 69 73 20 75 73 65  | tried. This use|
00000100  73 20 74 68 65 20 76 61  72 69 61 62 6c 65 20 27  |s the variable '|
00000110  70 72 6f 62 69 6e 67 27  2e 0a 20 2a 2f 0a 09 73  |probing'.. */..s|
00000120  68 6f 72 74 20 61 75 74  6f 64 65 74 65 63 74 5b  |hort autodetect[|
00000130  38 5d 3b 09 09 2f 2a 20  61 75 74 6f 64 65 74 65  |8];../* autodete|
00000140  63 74 65 64 20 66 6f 72  6d 61 74 73 20 2a 2f 0a  |cted formats */.|
00000150  09 0a 09 69 6e 74 20 63  68 65 63 6b 66 72 65 71  |...int checkfreq|
00000160  3b 20 2f 2a 20 68 6f 77  20 6f 66 74 65 6e 20 73  |; /* how often s|
00000170  68 6f 75 6c 64 20 74 68  65 20 64 72 69 76 65 20  |hould the drive |
00000180  62 65 20 63 68 65 63 6b  65 64 20 66 6f 72 20 64  |be checked for d|
00000190  69 73 6b 20 0a 09 09 09  2a 20 63 68 61 6e 67 65  |isk ....* change|
000001a0  73 20 2a 2f 0a 09 69 6e  74 20 6e 61 74 69 76 65  |s */..int native|
000001b0  5f 66 6f 72 6d 61 74 3b  20 2f 2a 20 6e 61 00 3f  |_format; /* na.?|
000001c0  e0 ff 83 3f e0 ff 02 00  00 00 00 f0 c1 00 00 3f  |...?...........?|
000001d0  e0 ff 05 3f e0 ff 02 f0  c1 00 00 68 0a 00 00 00  |...?.......h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```
 
A bit frustrated is all, not really fed up, heading more toward the 'meh' stage now.

---

### Post by QLee on 2011-03-04
[QUOTE=MibunoOokami]A bit frustrated is all, not really fed up, heading more toward the 'meh' stage now.[/QUOTE]

Frustrated can be as bad as fed up in some cases because it can cloud logical thinking with a perceived need for haste. It's frustrating for us too, having neither hands nor eyes on the system.


> I'm a little confused as to why the 40GB drive is showing entries for Vista because Vista is/was on the built in HDD which I assume is what you refer to as MBR. The live CD did the installation so I don't understand why entries for Vista are now on the 40GB drive or something went wrong with grub.Why do you think the "entries for Vista are now on the 40GB drive"? There isn't anything to indicate that in the data that you have given us in this thread.

> Booting from the 40GB drive looks like it could be complicated and given what has gone wrong with the install of Maverick onto an external drive without my help, I'm a little reluctant to try boot from the 40GB in case I totally screw things up beyond repair..... Complicated? No just a matter of changing the BIOS boot order, given the "tone" of the rest of this thread do you think we would try and lead you through something that would "totally screw things up beyond repair"? Very little danger if you follow instructions to the letter (only the instructions) and give us accurate feedback of what is happening.

A couple of times in this thread you have told us something and, then later, corrected it to the opposite, are you absolutely sure we now have correct data to troubleshoot from? I sense you actually did more with this system than you have currently told us, for example from the bootinfo text > # / was on /dev/sda7 during installation
UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f /               ext3    relatime,errors=remount-ro 0       1but we know that specific UUID is now sda5, you must have deleted a partition or two at some point, eh. 

[Edit] Oops, I forgot to put in this quote, which shows an inconsistancy of the external.
> # / was on /dev/sdc5 during installation
UUID=ff93f56e-7de5-4879-a034-f921c27bdf72 /               ext4    errors=remount-ro 0       1Sdc? How many drives did you have connected when you did the 10.10 install? [/edit]


I agree with coffeecat, really hard to imagine how the bootinfo script could see the external and detail it's UUID partition correctly, and then the reinstall GRUB to the MBR work correctly, yet the system fail to find it when booting. That doesn't make sense.

> I'm going to go away and give this some thought, I might be safer  just to try fix this problem from chroot because right now I feel I'm  not going to be able to back up the files that I need.From the begining, we have taken the view that we would get backups of  your important files first. We've been trying to determine why you are  having trouble with it so we could produce those backups. That was the  reason for the check disk on the ntfs partition (different from checking the CD which is done  from the "live CD" menu). How did you get into Windows to do the disk  check on that partition that was showing as RO, since your system is  still not booting? We want that partition mounted RW so you can copy  your files to it. (How many files are we talking about? - What was the  name of the "certain file" you mention?) I got to this point expecting  you to continue with that procedure. You could also try copying the important files to the 10.10 partition, anywhere to get them backed up. This is still the bottom line for  safety of your files. Why have you given up on this?

---

### Post by MibunoOokami on 2011-03-04
> **QLee said:**
>  
Why do you think the "entries for Vista are now on the 40GB drive"? There isn't anything to indicate that in the data that you have given us in this thread. 
 
Just went back to check, I misread Coffeecat's post. The 10.10grub in the 40GB drive is showing entries for vista, not the actual drive itself my mistake.
 
> **QLee said:**
> Complicated? No just a matter of changing the BIOS boot order, given the "tone" of the rest of this thread do you think we would try and lead you through something that would "totally screw things up beyond repair"? Very little danger if you follow instructions to the letter (only the instructions) and give us accurate feedback of what is happening.
 
This whole thing started out with me wanting to upgrade Ubuntu but the button wouldn't appear in the update manager. I was supposed to do something as simple as changing all entries of the word 'karmic' in the source list to the word 'lucid' in order to upgrade, but seem to have stuffed that up and created what has been termed a 'hybrid'. Then I went on to try intall 10.10 onto an external drive and followed screen prompts from the live CD and now get the same grub rescue screen at startup with or without the external drive attached. 
Please forgive my tone, but as you can see, following instructions to the letter hasn't always worked with the desired results.
 
> **QLee said:**
> A couple of times in this thread you have told us something and, then later, corrected it to the opposite, are you absolutely sure we now have correct data to troubleshoot from? I sense you actually did more with this system than you have currently told us, for example from the bootinfo text but we know that specific UUID is now sda5, you must have deleted a partition or two at some point, eh.
 
I am sure you have the correct data. Just to make sure I am learning properly when you say sda5, you're talking about my main hdd (300+GB in size) No partitions have been deleted at least not with my knowledge, I bought it about a year ago, installed Ubuntu without deleting any partions and have been using it fine until a week ago.  
 
> **QLee said:**
> [Edit] Oops, I forgot to put in this quote, which shows an inconsistancy of the external.
Sdc? How many drives did you have connected when you did the 10.10 install? [/edit]
 
Just the 1 external drive, unless we're counting the internal one as well then it was 2. 
 
> **QLee said:**
> I agree with coffeecat, really hard to imagine how the bootinfo script could see the external and detail it's UUID partition correctly, and then the reinstall GRUB to the MBR work correctly, yet the system fail to find it when booting. That doesn't make sense.
 
All I can think to say here is, it may be hard to imagine, it may not make sense, but it is what it is. I'm not making this stuff up, I have better things to do with my time.
 
> **QLee said:**
> From the begining, we have taken the view that we would get backups of your important files first. We've been trying to determine why you are having trouble with it so we could produce those backups. That was the reason for the check disk on the ntfs partition (different from checking the CD which is done from the "live CD" menu). How did you get into Windows to do the disk check on that partition that was showing as RO, since your system is still not booting? We want that partition mounted RW so you can copy your files to it. (How many files are we talking about? - What was the name of the "certain file" you mention?) I got to this point expecting you to continue with that procedure. You could also try copying the important files to the 10.10 partition, anywhere to get them backed up. This is still the bottom line for safety of your files. Why have you given up on this?
 
As I said earlier, I am using another computer that has Windows XP installed but has no CD rom/writer. I plugged in the NTFS drive which was getting read only messages and it seems to have checked out fine. I have an external CD writer as well but it failed to copy the Slax ISO which was why I was hoping I could boot from the external drive long enough to use the CD writer on my PC and burn Slax to try save my files.
When you say copy to the 10.10 partition, you mean the live CD right? Assuming so, I have already tried that many times and get the error message about not having permissions. The files getting the error messages are photos, text documents and my Thunderbird profile. 
 
Again I apologise for any tone that is detected from me it is not intentional. I believe I have addressed all the questions and concerns from this post. If not please let me know.

---

### Post by QLee on 2011-03-04
[QUOTE=MibunoOokami]Just went back to check, I misread Coffeecat's post. The 10.10grub in the 40GB drive is showing entries for vista, not the actual drive itself my mistake.[/QUOTE]

That's just the GRUB menu on that partition, now I understand what you meant.
 
[QUOTE=MibunoOokami]This whole thing started out with me wanting to upgrade Ubuntu but the button wouldn't appear in the update manager. I was supposed to do something as simple as changing all entries of the word 'karmic' in the source list to the word 'lucid' in order to upgrade, but seem to have stuffed that up and created what has been termed a 'hybrid'. Then I went on to try intall 10.10 onto an external drive and followed screen prompts from the live CD and now get the same grub rescue screen at startup with or without the external drive attached. [/QUOTE]

Yes, I've read the posts. I'm afraid that there may have been a better way to deal with the issue of your first post. No one there actually isolated and identified the "problem" before they offered solutions. Many times that can work OK but not always.

[QUOTE=MibunoOokami] Please forgive my tone, but as you can see, following instructions to the letter hasn't always worked with the desired results.[/QUOTE]

 Well, it hasn't always done what we wanted but it was not risky, it did not risk your important files, that was what I was referring to by "tone", I think the tone in this thread has been we want to help and not have you lose important files in the process. Don't be insulted, but you have not always carried out the suggestions to the "letter" and a couple of times you did extra and didn't give us results until after that. Some of the results were misreported to us, but that is corrected now. Let's not get too involved with this, it was not my intention to criticise you personally, try and imagine what it is like to troubleshoot when you can't actually see what is happening and the data you are receiving is not consistant and what the user is telling doesn't agree always with the tests.

[QUOTE=MibunoOokami]I am sure you have the correct data. Just to make sure I am learning properly when you say sda5, you're talking about my main hdd (300+GB in size) No partitions have been deleted at least not with my knowledge, I bought it about a year ago, installed Ubuntu without deleting any partions and have been using it fine until a week ago.  [/QUOTE]

Not exactly, sda5 is one of the partitions on that drive, namely the one with the failed upgrade on it (identified by boot info script as a 10.04 installation) I'm just using the designations that I see in the results.txt.

OK, the previous owner is responsible for the partition deletion. That they were deleted is obvious from the boot info script. 
 
[QUOTE=MibunoOokami]Just the 1 external drive, unless we're counting the internal one as well then it was 2. [/QUOTE]

Well, that is strange because the boot info script shows that it was installed to sdc5. That is the 5th partition on the third hard drive, so your system thought it was installing to a third hard drive. 
 
[QUOTE=MibunoOokami]All I can think to say here is, it may be hard to imagine, it may not make sense, but it is what it is. I'm not making this stuff up, I have better things to do with my time.[/QUOTE] 
Sure we all have ways in which we would use our time differently if we weren't doing this. I agreeded with coffeecat, I still do, this was not about you, I wasn't accusing you of anything.
 
[QUOTE=MibunoOokami]As I said earlier, I am using another computer that has Windows XP installed but has no CD rom/writer. I plugged in the NTFS drive which was getting read only messages and it seems to have checked out fine. I have an external CD writer as well but it failed to copy the Slax ISO which was why I was hoping I could boot from the external drive long enough to use the CD writer on my PC and burn Slax to try save my files.
When you say copy to the 10.10 partition, you mean the live CD right? Assuming so, I have already tried that many times and get the error message about not having permissions. The files getting the error messages are photos, text documents and my Thunderbird profile.[/QUOTE]

I can't think of anything about files of those types which would cause a problem. We need to have you try that in a step-by-step process with us seeing the exact commands you are using and exact error messages. I realise that would be time consuming because of timezone differences. I know you've told us it doesn't work but that doesn't give us anything to troubleshoot with. Please boot up with the live CD and run an fsck on sdb5 while it is unmounted. (That is where, in theory, you installed 10.10 and now is not accessable.) If it runs, try copying your important files there.
 When I say to copy to the 10.10 partition. I mean boot with the live and try to copy from sda5 (old install, failed upgrade) the files you want to sdb5 (your new 10.10 install) [Edit] If it works keep them somewhere you can find them easily, perhaps a storage folder or something. [/edit]

[QUOTE=MibunoOokami]Again I apologise for any tone that is detected from me it is not intentional. I believe I have addressed all the questions and concerns from this post. If not please let me know.[/QUOTE]

I did not detect any "tone" from you other than the frustration that you have already mentioned. If this was happening to my system I too would be frustrated.

---

### Post by coffeecat on 2011-03-04
I must admit, I missed the fact that 10.10's fstab was referring to the root partition being on sdc5, when subsequently it turns up as sdb5 in the boot script. I wonder if the NTFS USB drive was plugged in when 10.10 was installed to the other drive with the NTFS one  being designated sdb then and the larger one sdc. @MibunoOokami, was this so?

Whatever, that would only solve a minor mystery and doesn't help with the bigger problem. So, a bit of late night lateral thinking here in the Northern Hemisphere before I log off for the night.

@MibunoOokami, two questions:

Q1: Do you have access to another system running Ubuntu? It doesn't have to be yours. Indeed it doesn't really need to be running Ubuntu so long as it is running a decent Linux distro.

Q2: Do you have access to a spare USB HD enclosure that you could put the 400GB drive into temporarily? Are you confident about opening up the machine and removing the HD? I'm assuming it's a desktop although I don't remember whether this was mentioned. With some laptops it's not that difficult removing the HD either.

If yes to both, boot up the other system, attach the 400GB drive in the enclosure and backup your files. If you still get a read-only error with the NTFS drive then there is definitely 101% something wrong with the filesystem whatever Windows says about it.

---

### Post by MibunoOokami on 2011-03-04
@ QLee, I guess I misunderstood you when I read the part about the tone of the thread, thought you meant it in the same way like tone of voice. 
 
@ Coffeecat, No other drive was attached, I don't know why there are signs a 3rd device was connected.
 
I think I gave a computer to a mate with Ubuntu installed on it, as long as they haven't changed the OS I can get access to it, no one I know uses Linux.
 
I'm using a laptop. I must say, removing the HDD sounds like a bit of a drastic measure, is there no other way around that?

---

### Post by coffeecat on 2011-03-05
> **MibunoOokami said:**
> @ Coffeecat, No other drive was attached, I don't know why there are signs a 3rd device was connected.

OK, at the risk of being repetitious, I'm going to go over this bit again because something must be preventing you from booting 10.10 from the external drive.

First, can we please confirm what hardware you have? You have laptop with a 400GB internal drive which appears as sda and which has Windows and the problematic half-upgraded Lucid on it. Correct?

Next, you have a 40GB external USB drive which has Ubuntu 10.10 on it (the partition with the UUID ff93f56e-7de5-4879-a034-f921c27bdf72). This is the drive that appears as sdb in the bootscript but which must have been sdc when you did the 10.10 installation. We'll come back to that point. It also has a FAT32 partition #1 of about 33GB. What's that for?

Last, you have another 40GB external USB drive formatted NTFS which has never appeared in your bootscript outputs. This is the one that you get a read-only error when you try to write to it from the live CD, but which checked out OK in Windows. Correct?

Back to the sdb/sdc business. The drive with Ubuntu 10.10 on it and which appears as sdb in the boot script output was designated sdc when you installed. You must have had a second USB drive attached when you installed Ubuntu. I can think of no other logical explanation, except perhaps a dodgy BIOS in the laptop. Please cast your mind back. Apart from the drive you were installing Ubuntu 10.10 to, what else did you have attached to the laptop? I dismissed this as a minor point last night; I think it may be a major one.

Next question: when you try to boot 10.10 from the USB drive, do you have any other drives, pendrives, whatever, attached and switched on? Try booting with only the 40GB drive with Ubuntu 10.10 on it. Only attach and switch on the NTFS drive if and when the system boots up.

If you cannot boot from the external drive when you have nothing else attached to the laptop, then I would seriously suspect a problem with the BIOS. However, there would be one last thing I would try. In outline it would be to:

1 - set the BIOS to boot from an attached USB device.

2 - install grub to the mbr of the external drive.

3 - try booting from the external drive in that configuration.

I'm happy to tell you how to do that, but please confirm or otherwise all the points above first.

---

### Post by MibunoOokami on 2011-03-05
> **coffeecat said:**
> OK, at the risk of being repetitious, I'm going to go over this bit again because something must be preventing you from booting 10.10 from the external drive.
 
No problem
 
> **coffeecat said:**
> First, can we please confirm what hardware you have? You have laptop with a 400GB internal drive which appears as sda and which has Windows and the problematic half-upgraded Lucid on it. Correct?
 
Um 64 bit processor, 4gb ram, 400gb hdd, that's about all I can think of off the top of my head.
 
> **coffeecat said:**
> Next, you have a 40GB external USB drive which has Ubuntu 10.10 on it (the partition with the UUID ff93f56e-7de5-4879-a034-f921c27bdf72). This is the drive that appears as sdb in the bootscript but which must have been sdc when you did the 10.10 installation. We'll come back to that point. It also has a FAT32 partition #1 of about 33GB. What's that for? 
 
33GB is just for mass storage, I think there's a few GB free space on it.
 
> **coffeecat said:**
> Last, you have another 40GB external USB drive formatted NTFS which has never appeared in your bootscript outputs. This is the one that you get a read-only error when you try to write to it from the live CD, but which checked out OK in Windows. Correct?
 
No that one is 100GB checked out fine on windows, has about 4GB or so free. 
 
> **coffeecat said:**
> Back to the sdb/sdc business. The drive with Ubuntu 10.10 on it and which appears as sdb in the boot script output was designated sdc when you installed. You must have had a second USB drive attached when you installed Ubuntu. I can think of no other logical explanation, except perhaps a dodgy BIOS in the laptop. Please cast your mind back. Apart from the drive you were installing Ubuntu 10.10 to, what else did you have attached to the laptop? I dismissed this as a minor point last night; I think it may be a major one.
 
I honestly don't think I had another device plugged in, when I saw the install option had automatically selected the 40GB drive instead of the 400GB one, I looked to see what else appeared in the drop down menu and only the 400gb and 40gb ones were there. That's when I got the smart idea (at that time) to install on the 40gb. I have nothing else that runs from USB other than my mobile broadband but that doesn't work on Ubuntu and I hadn't been using it at that time.
 
 > **coffeecat said:**
> 
Next question: when you try to boot 10.10 from the USB drive, do you have any other drives, pendrives, whatever, attached and switched on? Try booting with only the 40GB drive with Ubuntu 10.10 on it. Only attach and switch on the NTFS drive if and when the system boots up.
 
No other devices were attached when trying to boot 10.10.
 
> **coffeecat said:**
> If you cannot boot from the external drive when you have nothing else attached to the laptop, then I would seriously suspect a problem with the BIOS. However, there would be one last thing I would try. In outline it would be to:
 
1 - set the BIOS to boot from an attached USB device.
 
2 - install grub to the mbr of the external drive.
 
3 - try booting from the external drive in that configuration.
 
I'm happy to tell you how to do that, but please confirm or otherwise all the points above first.
 
OK is there a reason/explanation why the bios might develop a problem? I don't even know what that is, what it does or even where it is, so I can say with absolute 100% certainty, I did not do anything to it.
 
Cheers

---

### Post by coffeecat on 2011-03-05
> **MibunoOokami said:**
> Um 64 bit processor, 4gb ram, 400gb hdd, that's about all I can think of off the top of my head.

I should have asked this before. What's the exact make/model of the laptop? It might be worth doing abit of googling to see if anyone else with the same machine has had weird problems with Linux and/or grub. There are definitely Linux-hostile laptops out there.
 
 > **MibunoOokami said:**
> I honestly don't think I had another device plugged in, when I saw the install option had automatically selected the 40GB drive instead of the 400GB one, I looked to see what else appeared in the drop down menu and only the 400gb and 40gb ones were there. That's when I got the smart idea (at that time) to install on the 40gb. I have nothing else that runs from USB other than my mobile broadband but that doesn't work on Ubuntu and I hadn't been using it at that time.

That's very interesting. There must be some reason why the 40GB drive was designated sdc when you installed but appears as sdb in the boot script. I think we just need leave that observation hanging, albeit unexplained, for the time being.
 
 > **MibunoOokami said:**
> OK is there a reason/explanation why the bios might develop a problem? I don't even know what that is, what it does or even where it is, so I can say with absolute 100% certainty, I did not do anything to it.

If you haven't gone into the BIOS configuration screen you wouldn't have done anything to affect the BIOS; you can be reassured on that score. Things do go faulty spontaneously, so we can't rule that out just yet as a cause of the oddities we're seeing.

I think the next step - if you want to try it - is to set the 40GB drive as the bootable one and to install grub to its mbr. There is one reason and one reason alone that I suggest doing this. It's so that you can boot into 10.10 on the external drive to copy your personal files. No other reason at all, since you won't be able to boot at all without the USB drive attached and you don't want to be dragging a laptop around with a USB drive permanently attached to it. :?

This would be my suggested strategy:

1 - Install grub to the mbr of the USB drive using the live CD and set the BIOS to boot from the usb drive.

2 - Boot 10.10 on the external drive and copy your files. - assuming that they do copy to your NTFS drive. [-o<

3 - Set the BIOS back to where it was before step 1.

4 - Boot up with the CD and make a fresh install of Ubuntu to sda5. This will create a new grub menu dual-booting Ubuntu and Windows - hopefully!  [-o< [-o< [-o<

5 - Restore your data to the new Ubuntu installation.

I will give you detailed step-by-step instructions if you want, but first: when you first switch on the machine and when you get the manufacturer's splash, do you see a message something like "press ? key to enter setup" or "press ? key to enter BIOS", ar anything like that? If so, which key does it tell you to press? Manufacturers vary. It could be any F key, the delete key, the ESC key or something else.

---

### Post by MibunoOokami on 2011-03-05
> **coffeecat said:**
> I should have asked this before. What's the exact make/model of the laptop? It might be worth doing abit of googling to see if anyone else with the same machine has had weird problems with Linux and/or grub. There are definitely Linux-hostile laptops out there.
 
Sony Vaio vgn-fw72jgb. It's a Japanese model that a mate brought over and sold to me when visiting here. It was brand new in the box so why there is a partition number 5 is beyond me, unless it's just another one of those oddities that have happened.
 
 
 > **coffeecat said:**
>  I will give you detailed step-by-step instructions if you want, but first: when you first switch on the machine and when you get the manufacturer's splash, do you see a message something like "press ? key to enter setup" or "press ? key to enter BIOS", ar anything like that? If so, which key does it tell you to press? Manufacturers vary. It could be any F key, the delete key, the ESC key or something else.
 
Nope just VAIO comes up on screen then it changes to what should be grub. I know what you mean, it was F8 on my old machine.

---

### Post by coffeecat on 2011-03-05
> **MibunoOokami said:**
> Sony Vaio vgn-fw72jgb.

Excellent. Both the Sony Vaios that I have experience of use F2 to get into the BIOS.

Start the machine and as soon as the Vaio logo appears press F2 and keep it pressed. You will enter the BIOS configuration.

Questions:

Do you see "American Megatrends" top right of the screen - or anywhere?

Do you have Main, Security, Boot and Exit tabs?

Is the BIOS in English? :?

Once you've checked that, simply press ESC to get out of the BIOS without making any changes.

Let me know and I'll post some detailed directions, but that won't be for a few hours - time for when you get up in the morning perhaps. :)

---

### Post by MibunoOokami on 2011-03-05
> **coffeecat said:**
> Start the machine and as soon as the Vaio logo appears press F2 and keep it pressed. You will enter the BIOS configuration.
 
 
Done 
 
> **coffeecat said:**
> Do you see "American Megatrends" top right of the screen - or anywhere?
 
Yes
 
> **coffeecat said:**
> Do you have Main, Security, Boot and Exit tabs?
 
Yes
 
> **coffeecat said:**
> Is the BIOS in English? :?
 
Yes
 
> **coffeecat said:**
> Once you've checked that, simply press ESC to get out of the BIOS without making any changes.
 
Not done..... ESC isn't working yet even the screen says ESC: Exit. edit: I just used the arrows to the exit tab and clicked shutdown. Because exit wanted me to save any changes and whilst I had not made any, thought it better o be safe than sorry.
 
> **coffeecat said:**
> Let me know and I'll post some detailed directions, but that won't be for a few hours - time for when you get up in the morning perhaps. :)
 
Fell right asleep after making that other post. Hopefully got this one done on time [-o<
 
must be getting late there.

---

### Post by MibunoOokami on 2011-03-05
> **MibunoOokami said:**
> I know what you mean, it was F8 on my old machine.
 
OK, no, what I mean is, I know that a trouble shooting or some such prompt comes up at the splash screen which usually says to press F8. Not I've entered the BIOS before.
Until this very day I have never pressed the key at startup because have never had the need and judging from what I saw just before, I am guessing BIOS is the brain of the computer rather than an operating system.

---

### Post by coffeecat on 2011-03-05
> **MibunoOokami said:**
> OK, no, what I mean is, I know that a trouble shooting or some such prompt comes up at the splash screen which usually says to press F8. Not I've entered the BIOS before.
Until this very day I have never pressed the key at startup because have never had the need and judging from what I saw just before, I am guessing BIOS is the brain of the computer rather than an operating system.

If I remember correctly, F8 on a Sony Vaio takes you to the recovery partition, which is something else again. :)

BIOS. Not quite the brain of a computer. It's very basic and very antiquated as computer technology goes:

[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

I'll post instructions for getting grub installed to the external drive in the morning (here). It's late in this time zone and if I try to post this now, I'll make mistakes through tiredness. Fear not; I shall return! :wink:

---

### Post by MibunoOokami on 2011-03-05
> **coffeecat said:**
>  
BIOS. Not quite the brain of a computer. It's very basic and very antiquated as computer technology goes:
 
[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
 
Well they say you learn something new every day. So not the brain, but definitely a vital piece of software, in which if I do anything wrong, I could endup with a glorified paperweight. :o
 
> **coffeecat said:**
> I'll post instructions for getting grub installed to the external drive in the morning (here). It's late in this time zone and if I try to post this now, I'll make mistakes through tiredness. Fear not; I shall return! :wink:
 
No worries, certainly don't want any mistakes. See ya later.

---

### Post by QLee on 2011-03-06
[QUOTE=MibunoOokami]Well they say you learn something new every day. So not the brain, but definitely a vital piece of software, in which if I do anything wrong, I could endup with a glorified paperweight. :o[/QUOTE]
 
Not very likely. BIOS stands for Basic Input/Output System. It's probably better to think of it as "firmware" rather than software but you've got the idea. It's stored in memory that remains battery powered when the main power is off and which also keeps the clock time. It holds the instructions that allow the system to use video and keyboard and hard drive and CD, etc. before the operating system is loaded. It's a very simple "brain" that just knows how to read from the "inputs" attached to the system and how to "output"(.i.e. display). It is a simple brain which knows how to find the MBR of the first drive in the booting order set in it and read that into system memory then carry on.  

While it could be possible for you to go "into" the BIOS and make a bunch of incorrect or poor choices, the BIOS has a reset feature to set it back to factory defaults, so not much risk in this case. People sometimes "brick" a computer by doing an incorrect BIOS "flash" (change to a different version) but we aren't going to be trying that at this time. All coffeecat is going to have you do is set the boot order in the BIOS to boot the usb external drive first then install GRUB to the MBR and try to get your 10.10 installation working, it won't be touching your important files or the partition (on a different drive) they are on.

---

### Post by coffeecat on 2011-03-06
OK, here goes. Instructions for getting grub into the mbr of the external drive and to boot from the external drive. Just one point first:

> **MibunoOokami said:**
> Not done..... ESC isn't working yet even the screen says ESC: Exit. edit: I just used the arrows to the exit tab and clicked shutdown. Because exit wanted me to save any changes and whilst I had not made any, thought it better o be safe than sorry.

When in the BIOS, if you press ESC you are prompted with 'Quit without saving? Yes/No', and if you press F4 you get 'Save configuration and reset? Yes/No'. With either you have the chance to go back to the BIOS by choosing 'No'. You can certainly use the Exit tab if you are more comfortable with that - I just prefer to use the keyboard shortcuts because it is quicker and ESC to exit is universal on all BIOS's I have played with.

Anyway, to reset the BIOS:

Before you switch the laptop on, plug in the 40GB external drive and power it up. Some BIOS's won't let you set the external drive in the boot priority unless it can detect it. I don't think is so for the Vaio BIOS, but it won't do any harm. Now power on the laptop and press F2 as soon as you see the Vaio splash. Once in the BIOS, go to the Boot tab. Before you make any changes please take a note of what you see and post it here for the record. It will be in the form (if it's like mine):

```
Boot Configuration
          External Device Boot:
          Network Boot:

Boot Priority
          Select 1st Boot Priority
          Select 2nd Boot Priority
          Select 3rd Boot Priority
```There will be values beside each of those five parameters. Please post those. Now change them so that they look like this:

```
Boot Configuration
          External Device Boot:                     [Enabled]
          Network Boot:                             [Disabled]

Boot Priority
          Select 1st Boot Priority                  [Internal Optical Disc Drive]
          Select 2nd Boot Priority                  [External Device]
          Select 3rd Boot Priority                  [internal Hard Disk Drive]
```

To change each, use the arrow key, press enter, make your selection and then press enter again.

You can now press F4 to save, or you can use the Exit tab if you prefer. It will be quite OK to leave these settings as they are permanently. This is how my Vaio is set up. The BIOS will check each boot device in turn. If there's a bootable CD/DVD in the drive it will boot from that. If not, it will check for a USB device and try to boot from that. And, if not, it will then boot from the hard drive. The only disadvantage with that is if I leave an ordinary pendrive plugged in and then switch on, I get a black screen with a flashing cursor - which is perplexing if I don't realise what I've done.

Now to reinstalling grub.

Boot the Vaio up with the Ubuntu 10.10 CD in the optical drive and the 40GB USB drive plugged in and switched on. Let it boot up to the live desktop. Before you re-install grub, let's check that the internal and external drives are still sda and sdb respectively. They almost certainly will be, but sometimes weird things happen. Open a terminal and:

```
sudo fdisk -lu
```

You don't need to post the output. Just make sure you see that sda1 and sda2 are NTFS partitions and that sdb1 is FAT32. Then you can be sure that sda and sdb are the right way round. Now, from the terminal:

```
sudo mount /dev/sdb5 /mnt
```

and

```
sudo grub-install --root-directory=/mnt /dev/sdb
```

That's almost the same as I posted before but there is one single but very important change. Can you see it? Do you know why? :wink:

Now reboot, remove the CD but leave the external drive plugged in and powered and see if it will boot into 10.10. If it does, you should be able to mount your sda5 partition from the Places menu. This time you probably won't need a 'gksudo nautilus' browser because your UUID in the new Maverick installation should be the same as the UUID in the old installation. That won't be the case if you (or the previous owner) set up more than one account, but let's see how you get on. Of course, it remains to be seen whether you can write to the external NTFS drive. I'm still of the opinion that something may be wrong with that.

Which reminds me. We haven't seen the fdisk output for the NTFS drive. If you still get a read-only error with it, post the output of:

```
sudo fdisk -lu
```

... with it plugged in and switched on. You can do this either from your 10.10 Ubuntu (if it boots) or from a live CD session.

Good luck!

---

### Post by MibunoOokami on 2011-03-06
I meant to reply sooner but got sidetracked with what I was doing. I got a PM from another member who gave me detailed commands in order to copy all my files without having to worry about the permission errors. The theory was, that if I format a flash drive to FAT32 and use that for copying data to through the terminal, no permission errors would be encountered because that format type apparently doesn't recognise permissions etc. I believe that's how it was explained.
Due to the time difference between most of the members posting here and I, as well as my usual impatience, I decided to give it a go because at the end of the day if that failed, well then there was always the BIOS option and failing that, removing the HDD and plugging it to another Linux system to copy my files that way. 
 
I'm much glad to say, that the terminal method did work after many hours, because some files wouldn't copy in bulk, they needed to be done individually. I had a small look when copying one folder I knew had permission errors on all the files. I tried copying via nautilus and got the copy error messages, so then went into terminal, entered a command and voila that file was successfully copied with no error messages. 
 
The member who helped me do this (Fabricator4) has recommended just doing a fresh install of 10.10 and while earlier I was tempted to do that, I found the time I spent in terminal to be very rewarding, not (only) because I managed to get my files, but because of the learning experience I had whilst commanding my computer to do what I want it to do, not what it thinks it should do. So if Coffeecat, QLee, Rubi1200 and any other members are still willing to help me with this, I would like to finish the upgrade with a chroot rather than a fresh installation (unless absolutely necessary) as I think I will benefit from yet another learning experience. 
 
Thank you very much for all the help and support you have given me in this thread. I do apologise for my impatience, I just love using Ubuntu so much and when you are forced to stop using it and go back to windows is just no fun and you just want to get back to Ubuntu as soon as possible.

---

### Post by wep940 on 2011-03-07
> **QLee said:**
> Not very likely. BIOS stands for Basic Input/Output System. It's probably better to think of it as "firmware" rather than software but you've got the idea. It's stored in memory that remains battery powered when the main power is off and which also keeps the clock time. It holds the instructions that allow the system to use video and keyboard and hard drive and CD, etc. before the operating system is loaded. It's a very simple "brain" that just knows how to read from the "inputs" attached to the system and how to "output"(.i.e. display). It is a simple brain which knows how to find the MBR of the first drive in the booting order set in it and read that into system memory then carry on. 
 
While it could be possible for you to go "into" the BIOS and make a bunch of incorrect or poor choices, the BIOS has a reset feature to set it back to factory defaults, so not much risk in this case. People sometimes "brick" a computer by doing an incorrect BIOS "flash" (change to a different version) but we aren't going to be trying that at this time. All coffeecat is going to have you do is set the boot order in the BIOS to boot the usb external drive first then install GRUB to the MBR and try to get your 10.10 installation working, it won't be touching your important files or the partition (on a different drive) they are on.
 
I'm sure you know, but that is a simplified explanation of something that does a little more than that.  It's not just output to the display, etc..  The old interrupt handling routines are still in the BIOS.  They dictate such things as how the hard disk is addressed, etc., at the lowest level.

---

### Post by coffeecat on 2011-03-07
> **MibunoOokami said:**
> The theory was, that if I format a flash drive to FAT32 and use that for copying data to through the terminal, no permission errors would be encountered because that format type apparently doesn't recognise permissions etc. I believe that's how it was explained.

I'm really glad that you managed to get your data copied. However, the NTFS filesystem you were trying to copy to and getting the read-only error with is the same as FAT32 insofar as it doesn't support Linux permissions. NTFS and FAT32 are both Microsoft filesystems; neither supports Linux permissions. Both are automounted by Ubuntu whether using a permanent installation or the live CD. All else working properly you should be able to copy files to FAT32 or NTFS without issue. I have said several times that because you were repeatedly getting the read-only error that I believed the NTFS filesystem was damaged whatever Windows says about the matter. Perhaps we should have suggested a reformat of the NTFS drive.

In retrospect, I should have concentrated on getting the copy working  in the live CD. Doing the grub re-installs was one huge distraction. But at least you've got your data copied.

---

### Post by MibunoOokami on 2011-03-07
> **coffeecat said:**
> I'm really glad that you managed to get your data copied. However, the NTFS filesystem you were trying to copy to and getting the read-only error with is the same as FAT32 insofar as it doesn't support Linux permissions. NTFS and FAT32 are both Microsoft filesystems; neither supports Linux permissions. Both are automounted by Ubuntu whether using a permanent installation or the live CD. All else working properly you should be able to copy files to FAT32 or NTFS without issue. I have said several times that because you were repeatedly getting the read-only error that I believed the NTFS filesystem was damaged whatever Windows says about the matter. Perhaps we should have suggested a reformat of the NTFS drive.

In retrospect, I should have concentrated on getting the copy working  in the live CD. Doing the grub re-installs was one huge distraction. But at least you've got your data copied.

Oh I didn't know that, I thought NTFS was something that was universal for both Windows and Linux. Is there a format type that is supported by both OS's or do you need to just pick one? 
During the copying process I did copy some files to the NTFS drive as I didn't have much space on the one I formatted to FAT32 and had some stuff I could delete on NTFS.
I really don't know what the issue was though with the copying, as I understand it from you and others is that none of these issues should have been encountered whilst using the liveCD and Nautilus. 

So now, do I purge and re-install the grub or would you too recommend just doing a fresh install? I would like to defeat the grub rescue error without doing a fresh install, but I could understand if you have had enough of me and this thread.

---

### Post by coffeecat on 2011-03-07
> **MibunoOokami said:**
> So now, do I purge and re-install the grub or would you too recommend just doing a fresh install? I would like to defeat the grub rescue error without doing a fresh install, but I could understand if you have had enough of me and this thread.

Personally, I would go for a fresh install. Grub issues aside, the installation on sda5 was half-upgraded in a way that was probably not optimal anyway, so we don't know what state it's in. In theory it should be fixable but it could take a lot of troubleshooting and fiddling.

See what the others think, but it's your choice.

If you do go for a fresh install with the 10.10 disk, I have one warning. Don't use the "install alongside other operating system"  option in the installer. There is an appalling design flaw in it. In certain circumstances it will wipe out your Windows partition(s). Go for the manual/advanced option and select sda5 for your root (/) partition. The installer will detect you swap partition automatically.

---

### Post by MibunoOokami on 2011-03-07
> **coffeecat said:**
> 

```
sudo fdisk -lu
```You don't need to post the output. Just make sure you see that sda1 and sda2 are NTFS partitions and that sdb1 is FAT32. 

sda1 is unknown, sda2 is NTFS and sdb1 is FAT32. Does that mean anything with sda1 being unknown?

One thing I don't understand from that output is I seem to have sda1, sda2, sda3, sda5 and sda6 but no sda4. And I have sdb1, sdb2, sdb5 and sdb6 but no sdb3 and no sdb4. Why is that?

> **coffeecat said:**
> ```
sudo grub-install --root-directory=/mnt /dev/sdb
```That's almost the same as I posted before but there is one single but very important change. Can you see it? Do you know why? :wink:

I think I see it though maybe not. Is it that we are mounting /dev/sdb instead of /dev/sda? Why? because we are mounting the external drive instead of the internal one? I'm probably miles off with those answers.

I apologise for missing this post earlier.

---

### Post by QLee on 2011-03-07
Given your "usual impatience" that you mention in post 70, I vote for a clean install. Seems like the easiest and fastest way to get that system back up and running. A fresh install is something you can do yourself and now you know how to move files around to get them back to the install when you are ready for them.

Good luck!

---

### Post by coffeecat on 2011-03-07
> **MibunoOokami said:**
> sda1 is unknown, sda2 is NTFS and sdb1 is FAT32. Does that mean anything with sda1 being unknown?

I don't know. The fdisk output in your boot script shows sda1 as Hidden HPFS/NTFS. That's fairly common for a recovery partition which is what your sda1 probably is. For fdisk to identify it correctly as HPFS/NTFS and then as unknown is a little concerning.

> **MibunoOokami said:**
>  One thing I don't understand from that output is I seem to have sda1, sda2, sda3, sda5 and sda6 but no sda4. And I have sdb1, sdb2, sdb5 and sdb6 but no sdb3 and no sdb4. Why is that?

That's normal and all to do with the numbering conventions of the mbr-type partition table. You have a limit of four primary partitions per drive, numbered #1, #2, #3 and #4. In order to squeeze more partitions in, you may have one extended partition instead of a primary partition. An extended partition is a type of primary partition but its sole purpose is as a container for logical partitions. An extended partition will also therefore have a number in the range 1-4. Logical partitions are numbered 5 and upwards. If you have a partition numbered sda5, sda6, etc, you know it's a logical partition if in a mbr partition table drive. It cannot be anything else. Other types of partition tables are different, but that's not relevant here.

In your case sda1 and sda2 are primary partitions and sda3 is the extended, containing the logicals sda5 and sda6. There is a spare unused line in the partition table for partition #4. Since there's nothing there, it's not listed out by fdisk.

> **MibunoOokami said:**
> I think I see it though maybe not. Is it that we are mounting /dev/sdb instead of /dev/sda? Why? because we are mounting the external drive instead of the internal one? I'm probably miles off with those answers.

Distinguish between the **partition** (/dev/sdb5) your are mounting as the root partition for grub and the **drive** (/dev/sda or /dev/sdb) you are installing grub stage 1 to - to the mbr.

This is all theoretical now since, if you've rescued your data, there's absolutely no point in installing grub to the mbr of the external drive. A quick note on mbr's. The mbr of a disc is the first 512 bytes, the first 440 or so of which contains boot code. The rest is the partition table. You install grub (stage 1) to the mbr - strictly the first 440 bytes - of the first boot disc. This grub code points to the partition where the rest of grub resides - which can be on any hard drive you want. In your case, if the internal drive is set as the first boot drive in your BIOS - even when the bootable system is going to be on a external drive - then you need to install grub (stage 1) to the mbr of sda. We tried that - it didn't work for reasons which are a complete mystery to myself and everyone else. My latest suggestion of installing grub to the mbr of sdb needed to be taken together with setting the BIOS with a boot priority of an external drive before the internal. **This is now irrelevant**, and I posted all those instructions with great reluctance because it felt like an extremely large hammer to crack an extremely small nut.

---

### Post by MibunoOokami on 2011-03-07
> **coffeecat said:**
> I don't know. The fdisk output in your boot script shows sda1 as Hidden HPFS/NTFS. That's fairly common for a recovery partition which is what your sda1 probably is. For fdisk to identify it correctly as HPFS/NTFS and then as unknown is a little concerning.

Somehow I have created a number of problems with my attempted upgrade from Karmic to Lucid, and with much more advanced users like yourself being concerned/confused by these issues, I will take your advice and just do the fresh install and put this to rest. 
I posted the output for you to see for yourself, maybe I am just reading it wrong, I still consider myself to be completely clueless.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x75fe8965

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    22388735    11193344   27  Unknown
/dev/sda2   *    22388736   128003970    52807617+   7  HPFS/NTFS
/dev/sda3       128005981   768147974   320070997    5  Extended
/dev/sda5       128005983   757866374   314930196   83  Linux
/dev/sda6       757866438   768147974     5140768+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
64 heads, 32 sectors/track, 38154 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00099df3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32    64747234    32373601+   c  W95 FAT32 (LBA)
/dev/sdb2        64747518    78139391     6695937    5  Extended
/dev/sdb5        64747520    77457407     6354944   83  Linux
/dev/sdb6        77459456    78139391      339968   82  Linux swap / Solaris

```

> **coffeecat said:**
> 
**This is now irrelevant**, and I posted all those instructions with great reluctance because it felt like an extremely large hammer to crack an extremely small nut.

I still do appreciate you having done that for me, as well as all your other help in this thread. I am more thankful than can be expressed with lifeless text.

Thank you.

---

### Post by coffeecat on 2011-03-07
> **MibunoOokami said:**
> I posted the output for you to see for yourself, maybe I am just reading  it wrong, I still consider myself to be completely clueless.

No, you're not reading it wrong. Compare this from your bootscript output:

> **MibunoOokami said:**
> ```
_____________________________________________________
Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1               2,048    22,388,735    22,386,688  27 [COLOR=Red]Hidden HPFS/NTFS[/COLOR]
/dev/sda2    *     22,388,736   128,003,970   105,615,235   7 HPFS/NTFS
/dev/sda3         128,005,981   768,147,974   640,141,994   5 Extended
/dev/sda5         128,005,983   757,866,374   629,860,392  83 Linux
/dev/sda6         757,866,438   768,147,974    10,281,537  82 Linux swap / Solaris
```

... with this from your latest fdisk:

> **MibunoOokami said:**
> 
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x75fe8965

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    22388735    11193344   27 [COLOR=Red] Unknown[/COLOR]
/dev/sda2   *    22388736   128003970    52807617+   7  HPFS/NTFS
/dev/sda3       128005981   768147974   320070997    5  Extended
/dev/sda5       128005983   757866374   314930196   83  Linux
/dev/sda6       757866438   768147974     5140768+  82  Linux swap / Solaris
  

```

I don't know why.

---

### Post by JKyleOKC on 2011-03-07
> **coffeecat said:**
> I don't know why.I suspect the reason is simply that fdisk doesn't have an entry in its type-translation table for type 27; however I've not examined the source for fdisk to verify this conclusion...

---

### Post by coffeecat on 2011-03-07
> **JKyleOKC said:**
> I suspect the reason is simply that fdisk doesn't have an entry in its type-translation table for type 27; however I've not examined the source for fdisk to verify this conclusion...

Ah right - OK. I'd assumed (probably wrongly) that the output from the bootscript was also from fdisk, albeit with different options judging by the differences in the presentation. Whatever, I'll run an fdisk on my Sony Vaio next time I boot it up to see what that makes of the sda1 recovery partition.

**Edit**: yes, indeed, fdisk doesn't cope with type 27. Output of fdisk from my Vaio:

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xde3cb3d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    20238335    10118144   27  Unknown
/dev/sda2   *    20238336   229953535   104857600    7  HPFS/NTFS
/dev/sda3       229954410   481612634   125829112+   7  HPFS/NTFS
/dev/sda4       481612696   625141759    71764532    5  Extended
/dev/sda5       481612698   487910114     3148708+  82  Linux swap / Solaris
/dev/sda6       487910178   522208889    17149356   83  Linux
/dev/sda7       522211328   556519423    17154048   83  Linux
```

@JKyleOKC, do you know what the bootscript is using? It's not sfdisk either because that returns an "unknown" as well.

---

### Post by QLee on 2011-03-07
[QUOTE=coffeecat]I don't know why.[/QUOTE]

Two different results from two different versions of fdisk. [Edit] Oops, this was supposed to have a question mark rather than a period. [/edit]

@Coffeecat, I'm not the person you asked but the script uses utilities available on the system, one of the first things it does is check for required programs and prompt to suggest you install if a needed program isn't installed.

[Edit] It's the B.I.S. that identifies the "Hidden HPFS/NTFS" from fdisk output. There is a function starting at line 349 which converts the two digit hexcode of a partition type.[/edit]

---

### Post by MibunoOokami on 2011-03-09
I finished my fresh install last night (this time making a separate partition for /home to avoid any problems with files in the future) and whilst it was downloading updates I went to sleep. Woke up, everything looked fine, suspended my pc while I went out, came home to find it had restarted and on the desktop there were no toolbars, just my wallpaper. Not sure what to make of that but when I was browsing the new posts tab, I saw a thread started by another member with the same problem. Just working on a solution for that at the moment. Anyway, I decided to log into Vista to see if that was still fine. As it happens, I tried to log in 3x and got an error message ```
user profile service
login process failed
cannot read user profile
```
Tried for a 4th time and logged in successfully and what would you know, the Vista partition or whatever you want to call it has somehow reset to default, leaving only 1 or 2 programs installed that I had put on there. Just as well I was smart enough to copy some files that were on there from the odd occasion that I was using windows.

I'm wondering if I should perhaps start a new thread about that to see if this problem has ever been encountered before. It seems pretty random and I hate to think it could be my computer since it's only a year old.

It's quite disappointing to be honest.

---

### Post by coffeecat on 2011-03-09
> **MibunoOokami said:**
> I'm wondering if I should perhaps start a new thread about that to see if this problem has ever been encountered before. It seems pretty random and I hate to think it could be my computer since it's only a year old.

A new thread might be a good idea because then everyone could focus on the new issues, but first... Boot up the live CD rather than your new Ubuntu installation and open System > Administration > Disk Utility. Highlight your internal drive in the left pane and see what the right pane has to say about your SMART status. Run a self-test as well.

It's just possible that a failing drive could account for some of the unexpected things that happened to you before, and could also be the reason for your newest problems in Ubuntu and Vista. Unfortunately, new-ish drives do fail on occasion. This is a possibility.

---

### Post by QLee on 2011-03-09
[QUOTE=MibunoOokami]... Woke up, everything looked fine, suspended my pc while I went out, came home to find it had restarted and on the desktop there were no toolbars, just my wallpaper. Not sure what to make of that but when I was browsing the new posts tab, I saw a thread started by another member with the same problem. Just working on a solution for that at the moment. [/QUOTE]

Well that sucks, doesn't it!

When the system is in suspend it is no longer under control of the operating system, therefore that "restart" could not have been due to Ubuntu. Maybe coffeecat is correct suggesting possible hardware problems, although a hard drive fault is not going to make the system restart from suspend.

[QUOTE=MibunoOokami]Anyway, I decided to log into Vista to see if that was still fine. As it happens, I tried to log in 3x and got an error message ```
user profile service
login process failed
cannot read user profile
```Tried for a 4th time and logged in successfully and what would you know, the Vista partition or whatever you want to call it has somehow reset to default, leaving only 1 or 2 programs installed that I had put on there. ...[/QUOTE]

Once again, that sucks!

However, Ubuntu doesn't do anything to the Windows partition when it is installed and it certainly would not put anything back to "default" or selectively remove programs you had installed. I can't even think of a hardware fault that might do something like that, more likely to be random errors or crash.

[QUOTE=MibunoOokami]It's quite disappointing to be honest.[/QUOTE]

Yes, I am disappointed too.

---

### Post by MibunoOokami on 2011-03-09
I've started a new thread [here.]("http://ubuntuforums.org/showthread.php?t=1703360") Will quote QLee over there with a reply.

---


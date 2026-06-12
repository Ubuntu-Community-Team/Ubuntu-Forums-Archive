---
title: "GRUB boot when not needed?"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by craig810i386 on 2008-12-31
Fellow forum users,
  Thanks in advance for any help given. I am a newbie to ubuntu but not 
completely new to Linux.

  I have installed ubuntu on a Gateway Solo 5300 (800 Mhz CPU, 256 MB RAM,
30 GB HD). I think I made a mistake when I allowed GRUB to install to control the boot of this installation as I am not multi booting (I also have a WinXP Pro disk and just swap disks at my pleasure).

  I believe I have 3 options here:
     1) make GRUB work. every attempt that I have made to do this has failed - edited /etc/fstab, edited /boot/grub/menu.lst and ran sudo update-grub. This GRUB seems to use UUID to ID disks. However, disks did not become recognized until I 'worked around' and ID'd disks directly in /etc/fstab. But even after that, I cannot boot directly from HD - have to boot with LiveCD.
     2) Remove GRUB and boot directly from the HD without any bootloader. Dunno if that is even possible, so if I take this route I am gonna need more info.
     3) start over with a new install. least attractive option because dunno if problem will even be solved doing this. I actually had no problem connecting to my wireless network and so internet access was easy (thank goodness!). Gnome set up without problems as well, so if I don't have to reinstall I would prefer not to.

  Any help given would be greatly appreciated. My ability to access links is good as 'net access is good. 

                 Life is the next mess we make for ourselves,
                                           Craig

---

### Post by caljohnsmith on 2008-12-31
So what exactly is the problem? Can you boot into your Ubuntu? In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by SuperSonic4 on 2008-12-31
grub resides on the MBR which is on the hard disk not the motherboard or anything else.

Can't the bios just boot direct from hard drive with the NTLDR on the XP drive and grub on the ubuntu?

---

### Post by craig810i386 on 2009-01-01
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for its boot files.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91769176

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    57111074    28555506   83  Linux
/dev/sda2        57111075    58605119      747022+   5  Extended
/dev/sda5        57111138    58605119      746991   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="76102a94-9204-4c1a-b1d9-c1c515b9d02e" TYPE="ext3" 
/dev/sda5: UUID="3a77cb37-5926-41a6-88e3-daa86b315cfb" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/craig/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=craig)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=craig)

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		6

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
# kopt=root=/dev/sda1 ro

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

##title		Ubuntu 8.10, kernel 2.6.27-9-generic
##uuid		76102a94-9204-4c1a-b1d9-c1c515b9d02e
##kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=76102a94-9204-4c1a-b1d9-##c1c515b9d02e ro
##kernel          /boot/vmlinuz-2.6.27-9-generic rootdelay=15 root=/dev/sda1 ro   
##initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-9-generic rootdelay=30 root=/dev/sda1 ro   
initrd		/boot/initrd.img-2.6.27-9-generic


title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		76102a94-9204-4c1a-b1d9-c1c515b9d02e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=76102a94-9204-4c1a-b1d9-c1c515b9d02e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic


title		Ubuntu 8.10, memtest86+
uuid		76102a94-9204-4c1a-b1d9-c1c515b9d02e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sda1  UUID=76102a94-9204-4c1a-b1d9-c1c515b9d02e /  ext3    relatime,errors=remount-ro #0       1
/dev/sda1       /               ext3    relatime,errors=remount-ro   
#/dev/sda5  UUID=3a77cb37-5926-41a6-88e3-daa86b315cfb none            swap    sw              #0       0
/dev/sda5                                  swap  sw       0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 23796
drwxr-xr-x  3 root root    4096 2008-12-30 07:46 .
drwxr-xr-x 20 root root    4096 2008-12-30 07:41 ..
-rw-r--r--  1 root root  507665 2008-11-04 16:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 18:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 16:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 18:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-31 21:27 grub
-rw-r--r--  1 root root 8197320 2008-12-30 07:40 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8197298 2008-12-30 07:46 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 16:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 18:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 16:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 18:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 16:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 18:46 vmlinuz-2.6.27-9-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2008-12-31 21:27 .
drwxr-xr-x 3 root root   4096 2008-12-30 07:46 ..
-rw-r--r-- 1 root root    197 2008-12-29 03:10 default
-rw-r--r-- 1 root root     15 2008-12-29 03:10 device.map
-rw-r--r-- 1 root root   8108 2008-12-29 03:10 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-29 03:10 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-29 03:10 installed-version
-rw-r--r-- 1 root root   8712 2008-12-29 03:10 jfs_stage1_5
-rw-r--r-- 1 root root   4517 2008-12-31 21:27 menu.lst
-rw-r--r-- 1 root root   4517 2008-12-31 21:27 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-29 03:10 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-29 03:10 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-29 03:10 stage1
-rw-r--r-- 1 root root 121460 2008-12-29 03:10 stage2
-rw-r--r-- 1 root root   9556 2008-12-29 03:10 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.


 I followed your instructions and got the file on my desktop. Copied it here but 
see no # graphic to create the 'code' tags requested.

  I cannot boot into ubuntu HD without the LiveCD in the CDROM drive. Any attempt to do so seems to go into an endless loop. Any dmesg that I look at is only created after a successful boot with the LiveCD. I can copy and send that as well if that will help. I truly appreciate your reply and efforts to help me here!

                                                       Craig

---

### Post by craig810i386 on 2009-01-01
Thanks for the reply!

  I am speaking of having 2 physical hard drives for this laptop - 1 for WinXP and 1 for ubuntu 8.10. Have 2 Hard drive carriages for this laptop and just physically change from 1 disk to the other when i wish to change OS.

---

### Post by caljohnsmith on 2009-01-01
[QUOTE=craig810i386]I cannot boot into ubuntu HD without the LiveCD in the CDROM drive. Any attempt to do so seems to go into an endless loop. Any dmesg that I look at is only created after a successful boot with the LiveCD. I can copy and send that as well if that will help. I truly appreciate your reply and efforts to help me here![/QUOTE]
So do you mean you can boot Ubuntu on your HDD OK from the Live CD using the "boot from 1st HDD" type option? But if you try to boot the HDD directly (no Live CD in the CD drive), then it goes into an "endless loop"? Please be more specific--when you try to boot the HDD directly, what exactly happens? What do you mean by "endless loop"? Do you get any error messages?

---

### Post by craig810i386 on 2009-01-02
> **caljohnsmith said:**
> So do you mean you can boot Ubuntu on your HDD OK from the Live CD using the "boot from 1st HDD" type option? But if you try to boot the HDD directly (no Live CD in the CD drive), then it goes into an "endless loop"? Please be more specific--when you try to boot the HDD directly, what exactly happens? What do you mean by "endless loop"? Do you get any error messages?
You have described the situation.

  I attempted to boot directly from HDD and watching the scrolling 'info' 
I came across a message that tells of giving up looking for the root device.
Also lists comon problems - rootdelay= (... wait long enough?)and root= (...correct
device?) I now think that the 'endless loop' I mentioned is a continuing effort of the kernel to find the root device.

  The Gateway SOLO 5300 mounts removable devices thru a SCSI connection but I am pretty certain that the HDD is connected IDE. Being that I installed from CDROM (SCSI) is there a chance that the installation did not find the HDD as an IDE connection? There are NO devices in /dev under hd0 (IDE, I think).

  Also, When I do get a successful boot from HDD with the LiveCD I believe the
swap drive is never setup. There is a point in this bootup in which a message "mount point swap does not exist" and checking 'mount' after boot sucess does not show a mounted 'swap' drive.

  I really appreciate your posts and patience. I hope this post gives more specifics to you.                           thnks again,  Craig

---

### Post by caljohnsmith on 2009-01-02
OK, your problem is definitely strange, but how about booting into Ubuntu on your HDD with your Live CD, open a terminal and do:
```
gksudo gedit /boot/grub/menu.lst
```
And change your first Ubuntu entry to the following:
```
title Ubuntu 8.10, kernel 2.6.27-9-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=76102a94-9204-4c1a-b1d9-c1c515b9d02e ro quiet splash rootdelay=120
initrd /boot/initrd.img-2.6.27-9-generic
quiet
```
Try booting directly from your HDD, and please let me know exactly what happens or what errors you might get. We can work from there. :)

---

### Post by boof1988 on 2009-01-02
> **craig810i386 said:**
> I followed your instructions and got the file on my desktop. Copied it here but 
see no # graphic to create the 'code' tags requested.

Here's a screenshot to show where the "#" is.

Hope this helps.

---

### Post by craig810i386 on 2009-01-03
> **caljohnsmith said:**
> OK, your problem is definitely strange, but how about booting into Ubuntu on your HDD with your Live CD, open a terminal and do:
```
gksudo gedit /boot/grub/menu.lst
```
And change your first Ubuntu entry to the following:
```
title Ubuntu 8.10, kernel 2.6.27-9-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=76102a94-9204-4c1a-b1d9-c1c515b9d02e ro quiet splash rootdelay=120
initrd /boot/initrd.img-2.6.27-9-generic
quiet
```
Try booting directly from your HDD, and please let me know exactly what happens or what errors you might get. We can work from there. :)

   Thanks again for the reply.

   I have a question. Is it possible to 'capture' the messaging from the kernel from an unsuccessful boot attempt? Based on no completion, which is what I see when trying to boot from HDD, 'Capturing' kernel messaging may be the best way to show you what is actually happening. However, I realize this may not be possible. I do know about dmesg but is that not after a complete and successful boot?

                              Thanks again,   Craig
P.S. please see next post. Actually to you i replied to wrong poster

---

### Post by craig810i386 on 2009-01-03
> **boof1988 said:**
> Here's a screenshot to show where the "#" is.

Hope this helps.

  Made the changes to /boot/grub/menu.lst and tried HDD boot. Results follow (as best as I could put together)



Starting up...
loading, please wait
Gave up waiting for the root device. Common problems:
  rootdelay=(...wait long enough for the root device?)
  root=(... wait for the right device?)
Missing modules (cat /proc/modules  ls /dev)
!ALERT! /dev/disk-by-uuid=(uuid number in menu.lst) does not exist. Dropping to a shell

Busybox (.....

initramfs







         ata2.00 - synchronous SCSI scan failed with no progress


  and from here it seems 'initramfs' is looking for 'something' but all after this is hexidecimal numbers? I think scanning hardware.


  I hope this give us enough info to work with. Appreciate your help  Craig.

---

### Post by craig810i386 on 2009-01-03
> **boof1988 said:**
> Here's a screenshot to show where the "#" is.

Hope this helps.

  Thanks for your reply. I saw it once I replied with quote. I had been using quick reply and it does not seem to reside there.

        thanks Craig

---

### Post by caljohnsmith on 2009-01-03
About your question about capturing the booting messages on start up, I don't know of any easy way to do that offhand. I'm not even sure at exactly what point dmesg kicks in and starts recording the start up process, I would have to research it. :)

But about your strange booting problem, you might have an issue with how your HDD is set up in BIOS. It also doesn't help that your computer only has 256 MB of memory, although theoretically that is supposed to be enough to run Intrepid if I remember correctly; the Ubuntu website recommends a minimum of 384 MB of RAM for Intrepid though. Can you go into your BIOS and let me know what HDD-related settings you have? Look for settings like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. Also, is your HDD IDE or SATA? I would assume IDE, but maybe not.

Also, it might help to disable ACPI with the kernel or a few features like that to see if it helps you to boot Intrepid. How about trying the following in your menu.lst:
```
title Ubuntu 8.10, kernel 2.6.27-9-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=76102a94-9204-4c1a-b1d9-c1c515b9d02e ro quiet splash rootdelay=120 [COLOR="Blue"]noapic nolapic acpi=off[/COLOR]
initrd /boot/initrd.img-2.6.27-9-generic
quiet
```
Let me know if that makes any difference and we can work from there. :)

---

### Post by Elfy on 2009-01-03
Might be worth getting the result of

```
blkid
```

if UUID's are wrong > !ALERT! /dev/disk-by-uuid=(uuid number in menu.lst) does not exist. Dropping to a shell

OP - you don't have to use the # symbol to get code tags

Putting [noparse]```
[/noparse] at the beginning of the pasted output and[noparse]
```[/noparse] at the end is the same.

---

### Post by caljohnsmith on 2009-01-03
> **forestpixie said:**
> Might be worth getting the result of

```
blkid
```

if UUID's are wrong 

OP - you don't have to use the # symbol to get code tags

Putting [noparse]```
[/noparse] at the beginning of the pasted output and[noparse]
```[/noparse] at the end is the same.
Thanks forestpixie, but unless his partition UUIDs changed from post #4, then the blkid output from that post seems to show the UUID is OK. :)

---

### Post by craig810i386 on 2009-01-03
> **caljohnsmith said:**
> About your question about capturing the booting messages on start up, I don't know of any easy way to do that offhand. I'm not even sure at exactly what point dmesg kicks in and starts recording the start up process, I would have to research it. :)

But about your strange booting problem, you might have an issue with how your HDD is set up in BIOS. It also doesn't help that your computer only has 256 MB of memory, although theoretically that is supposed to be enough to run Intrepid if I remember correctly; the Ubuntu website recommends a minimum of 384 MB of RAM for Intrepid though. Can you go into your BIOS and let me know what HDD-related settings you have? Look for settings like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. Also, is your HDD IDE or SATA? I would assume IDE, but maybe not.

Also, it might help to disable ACPI with the kernel or a few features like that to see if it helps you to boot Intrepid. How about trying the following in your menu.lst:
```
title Ubuntu 8.10, kernel 2.6.27-9-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=76102a94-9204-4c1a-b1d9-c1c515b9d02e ro quiet splash rootdelay=120 [COLOR="Blue"]noapic nolapic acpi=off[/COLOR]
initrd /boot/initrd.img-2.6.27-9-generic
quiet
```
Let me know if that makes any difference and we can work from there. :)

  No difference after modifying the boot parameters as you requested. Still not finding the root device. 
 
  As to the BIOS settings parameters for the HDD are LBA is enabled, 32-bit is enabled, transfer mode is PIO4 DMA2. The CDROM shows the same parameters but there is an IDE adapter enabled on both devices which leaves me curious. Wonder if disabling this adapter would allow all to be seen as SCSI devices? :confused: 
  
 Appreciate your 'stickin with me' here - answers seem to be elusive.
                                  Thanks Craig

---

### Post by caljohnsmith on 2009-01-03
> **craig810i386 said:**
> No difference after modifying the boot parameters as you requested. Still not finding the root device. 
 
  As to the BIOS settings parameters for the HDD are LBA is enabled, 32-bit is enabled, transfer mode is PIO4 DMA2. The CDROM shows the same parameters but there is an IDE adapter enabled on both devices which leaves me curious. Wonder if disabling this adapter would allow all to be seen as SCSI devices? :confused: 
  
 Appreciate your 'stickin with me' here - answers seem to be elusive.
                                  Thanks Craig
OK, can you change the DMA2 setting to something else, i.e. maybe simply disable it? I would give that a try, and if that doesn't change anything, I would go with your idea of disabling the IDE adapter and seeing what happens about booting Ubuntu. If neither of those ideas work, at least you can revert back to the original BIOS settings and no harm should be done. How about giving it a shot and let me know what happens.

---

### Post by craig810i386 on 2009-01-05
> **caljohnsmith said:**
> OK, can you change the DMA2 setting to something else, i.e. maybe simply disable it? I would give that a try, and if that doesn't change anything, I would go with your idea of disabling the IDE adapter and seeing what happens about booting Ubuntu. If neither of those ideas work, at least you can revert back to the original BIOS settings and no harm should be done. How about giving it a shot and let me know what happens.

  First, tried to disable DMA2 and HDD was no longer seen in BIOS - 0MB.
Returned settings to DMA2. 

  Second, attempted to disable of the IDE adapter and got "operating system not found". (again HDD not seen in BIOS)

  Returning the settings to original restored ability for BIOS to see HDD and situation is I can only boot with LiveCD in CDROM.

                       Thanks   Craig

---

### Post by caljohnsmith on 2009-01-05
> **craig810i386 said:**
> First, tried to disable DMA2 and HDD was no longer seen in BIOS - 0MB.
Returned settings to DMA2. 

  Second, attempted to disable of the IDE adapter and got "operating system not found". (again HDD not seen in BIOS)

  Returning the settings to original restored ability for BIOS to see HDD and situation is I can only boot with LiveCD in CDROM.

                       Thanks   Craig
So you can't even boot the drive with the Live CD any more, even though you returned the BIOS settings back to their original values? What exactly happens when you try and boot the HDD from the Live CD like you were doing before?

---

### Post by craig810i386 on 2009-01-06
> **caljohnsmith said:**
> So you can't even boot the drive with the Live CD any more, even though you returned the BIOS settings back to their original values? What exactly happens when you try and boot the HDD from the Live CD like you were doing before?

I can still boot to the HDD with the liveCD with settings returned to original. 

I am beginning to wonder if a reinstallation is gonna be needed.

my thought is to copy the liveCD to the HDD and try installing from that
location. My thinking is that the HDD might be seen as an IDE device and
boot parameters would be based on that. I'm just throwing ideas out. Really don't know if will solve problem or not. The HDD is not found or recognized when trying to directly boot as root=/dev/sda1 but somehow that is dealt with when booting HDD from LivCD. Is there any log or info that might tell us what is happening during HDD boot from LiveCD?  


thanks thanks thanks   Craig:

---

### Post by caljohnsmith on 2009-01-06
> **craig810i386 said:**
> I can still boot to the HDD with the liveCD with settings returned to original. 

I am beginning to wonder if a reinstallation is gonna be needed.

my thought is to copy the liveCD to the HDD and try installing from that
location. My thinking is that the HDD might be seen as an IDE device and
boot parameters would be based on that. I'm just throwing ideas out. Really don't know if will solve problem or not. The HDD is not found or recognized when trying to directly boot as root=/dev/sda1 but somehow that is dealt with when booting HDD from LivCD. Is there any log or info that might tell us what is happening during HDD boot from LiveCD?  


thanks thanks thanks   Craig:
I'm not sure a reinstall would help, but it's difficult to say since your booting problems seem so strange. About installing the Live CD to your HDD, the Live CD boots in a manner quite different than a normal install as I understand it and even uses a different boot loader. If you were to install the Live CD to your HDD using something like UNetBootin, it would be just like your Live CD in that you would lose any changed settings upon rebooting. I think if I were in your shoes, I might just live with booting the HDD from the CD since that works, and I wouldn't think it would add too much extra to your booting time. If you do decide to reinstall, let me know how that goes. Sorry, but I can't think of much else right now that might realistically help.

---

### Post by craig810i386 on 2009-01-15
> **caljohnsmith said:**
> I'm not sure a reinstall would help, but it's difficult to say since your booting problems seem so strange. About installing the Live CD to your HDD, the Live CD boots in a manner quite different than a normal install as I understand it and even uses a different boot loader. If you were to install the Live CD to your HDD using something like UNetBootin, it would be just like your Live CD in that you would lose any changed settings upon rebooting. I think if I were in your shoes, I might just live with booting the HDD from the CD since that works, and I wouldn't think it would add too much extra to your booting time. If you do decide to reinstall, let me know how that goes. Sorry, but I can't think of much else right now that might realistically help.

   I think that is what I intend to do is just boot with LiveCD, especially 
with the info you just posted. I will keep my eyes and ears open for other ideas. Thanks VERY much for all your help. Craig:P

---


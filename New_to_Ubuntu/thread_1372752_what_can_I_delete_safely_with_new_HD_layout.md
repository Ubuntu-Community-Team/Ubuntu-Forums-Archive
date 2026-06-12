---
title: "what can I delete safely with new HD layout"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by wapfu on 2010-01-04
Hi,
Just installed 9.1 to a new partion.

layout is as follows from gparted.
sdb1 - ext 3 - old corrupt 9.1 - with a boot flag
unallocated
sdb2 - extended
unallocated
sdb5 - old linux swap for sdb1
sdb6 - new 9.1 install
sdb7 - linux swap for new installation

I want to get rid of the old files.

boot script is as follows
============================= Boot Info Summary: ==============================

 ```
=> Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=390ea972-4909-4d5f-a04a-27c5df7c8192)/boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
```

=========================== Drive/Partition Info: =============================

```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa592a592

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000be2f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    51,632,909    51,632,847  83 Linux
/dev/sdb2         150,657,570   312,576,704   161,919,135   5 Extended
/dev/sdb5         150,673,635   158,850,719     8,177,085  82 Linux swap / Solaris
/dev/sdb6         158,850,783   306,231,029   147,380,247  83 Linux
/dev/sdb7         306,231,093   312,576,704     6,345,612  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="6668823668820551" TYPE="ntfs" 
sdb1: UUID="5a3f01c6-01cd-4efa-98ee-44c92a023588" SEC_TYPE="ext2" TYPE="ext3" 
sdb5: LABEL="ID_FS_USAGE=oth" UUID="5e87dfa7-2587-40d0-9e5c-8948466df7ee" TYPE="swap" 
sdb6: UUID="390ea972-4909-4d5f-a04a-27c5df7c8192" TYPE="ext4" 
sdb7: UUID="45169d74-6d5e-4226-b00f-199891234757" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/billp/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=billp)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=2

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

H:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        4

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=5a3f01c6-01cd-4efa-98ee-44c92a023588 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=5a3f01c6-01cd-4efa-98ee-44c92a023588 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=5a3f01c6-01cd-4efa-98ee-44c92a023588 ro single
initrd        /boot/initrd.img-2.6.24-16-generic


title        Ubuntu 8.04, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


```
=============================== sdb1/etc/fstab: ===============================

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5a3f01c6-01cd-4efa-98ee-44c92a023588 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sdb5
UUID=600de7dc-44ae-4c38-9c09-6b70f6ab264b none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0 
```

=================== sdb1: Location of files loaded by Grub: ===================


    ```
.0GB: boot/grub/core.img
    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.24-19-generic
    .0GB: boot/initrd.img-2.6.24-19-generic.bak
    .0GB: boot/initrd.img-2.6.27-16-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.24-19-generic
    .0GB: boot/vmlinuz-2.6.27-16-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: vmlinuz

=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set 390ea972-4909-4d5f-a04a-27c5df7c8192
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 390ea972-4909-4d5f-a04a-27c5df7c8192
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=390ea972-4909-4d5f-a04a-27c5df7c8192 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 390ea972-4909-4d5f-a04a-27c5df7c8192
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=390ea972-4909-4d5f-a04a-27c5df7c8192 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6668823668820551
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 8.04, memtest86+ (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 5a3f01c6-01cd-4efa-98ee-44c92a023588
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=390ea972-4909-4d5f-a04a-27c5df7c8192 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=45169d74-6d5e-4226-b00f-199891234757 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


  81.3GB: boot/grub/core.img
  81.3GB: boot/grub/grub.cfg
  81.3GB: boot/initrd.img-2.6.31-16-generic-pae
  81.3GB: boot/vmlinuz-2.6.31-16-generic-pae
  81.3GB: initrd.img
  81.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```


how do I delete the old 9.1 on sdb1 with out affecting the new install?

Thanks

---

### Post by friv_livs on 2010-01-04
According to your boot info script, your grub 1.97 already on sda looks for your sd6 boot folder. 

You should be able to just delete sdb1 and sdb5 with gparted run from your sdb6 or live disk. 

The only messy part is sdb5 being in extended sdb2. 

As far as I know, you don't need grub installed to both drives for grub to work.
Someone else please confirm this in case i'm wrong.

---

### Post by tom.swartz07 on 2010-01-04
> **wapfu said:**
> Hi,
Just installed 9.1 to a new partion.

layout is as follows from gparted.
sdb1 - ext 3 - old corrupt 9.1 - with a boot flag
unallocated
sdb2 - extended
unallocated
sdb5 - old linux swap for sdb1
sdb6 - new 9.1 install
sdb7 - linux swap for new installation

I want to get rid of the old files.

how do I delete the old 9.1 on sdb1 with out affecting the new install?

Thanks

Phew. I dont mean to sound rude, but in the future, when you have large amounts of terminal output, PLEASE use the [ code][ / code] tags around the sections to prevent such large post sizes. Theyre the # symbol when you are writing your post. Thanks!


Okay, now to the problem.

Looking at your disk, it seems fairly straightforward. Lets get started.

First, you need to start using either a gParted live cd, or an Ubuntu LiveCD. If you want to follow along with this guide, go for the Ubuntu disk, but you could always print this out. :P


We will go forward in 3 steps; First, delete your old partitions. Second, re-arrange your partitions for better placement on the disk. Third, we will update your GRUB bootloader so that you could restart and boot back into your system (probs the most important, huh? :D )


Alrighty, step one:
If you have the space, be it an external hard drive or something else, BACK UP YOUR DATA. This is going to be a very data intensive set of actions, and there is going to be a lot of opportunities for your data to 'disappear'. Even if you need to steal someones flash drive and offload the files that you cannot live without, do so. Chances are, your data is going to be safe, but there is always the chance.


Next, boot to your livecd, and open gParted.

Each of these next steps should be performed one at a time, so that you reduce the chance of error.

1. select SDB1 and click the circle with a slash through it. This will delete your old partition. click apply- the green checkmark.

2. now select SDB5 and delete that also. apply.

3. select SDB2 and click the arrow with a line ( -->| ). This will bring up a dialog box with your drive's free space and the partition. Click and drag the left edge all the way to the left and right. apply.

4. select SDB6, your new ubuntu install, and click the -->| arrow. Click in the middle of the box for the partition and drag it all the way to the left. apply.

5. click SDB6 again, and the arrow again. this time, drag the right side of the partition to the right, it should touch your swap space when you apply. apply.

Final and most important step: updating the bootloader.

Go to applications, Accessories, Terminal.

type
```
sudo mount /dev/sdb6 /mnt
```then
```
sudo mount /dev/sdb7 /mnt
```Next type
```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```It will flash some information about your system, and when it finishes, you should be all set to reboot!

When you do reboot into your actual system, open the terminal one more time and type ```
sudo update-grub
``` to make sure that the changes stick.




Make sure that you understand everything here before you begin. Read over these instructions to familiarize yourself with them and follow them step by step. Missing a step here might mean the difference between saving your data and having to start from scratch! 

If you have any questions about any of the steps, post back and ask- the liveCD has firefox installed by default so you could make some quick back and forth looks here as you go along.


Good Luck! Let us know how it turns out!

---

### Post by wapfu on 2010-01-05
Thanks for the step by step instructions.
Sorry bout the length of print out - new to this - no excuse .
Point me to the method to do it correctly - must be a tip somewhere.
will proceed to follow instructions - will report back soon.

Thanks
Best regards
Bill

---

### Post by tom.swartz07 on 2010-01-05
> **wapfu said:**
> Thanks for the step by step instructions.
Sorry bout the length of print out - new to this - no excuse .
Point me to the method to do it correctly - must be a tip somewhere.
will proceed to follow instructions - will report back soon.

Thanks
Best regards
Bill

Great to hear that Bill!
No worries about the long post business, its just a formality- keeps the posts short and sweet for anyone looking through to see if they could help.


Ive outlined all of the steps as best I could, its pretty much self explanatory. Good luck!

---

### Post by wapfu on 2010-01-05
It worked .
All I can say Tom is Yahoooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo

It worked - and oh so well.::)

Had a glitch with gparted on the live CD not being able to unmount the swap sdb2 as it was in use? I was able to delete the old install though.
So went to the live gparted cd.
Deleted sdb2 and then found I couldn't move the new install sdb5 - couldnt even resize it.
So back to Ubuntu 9.1 live - where I moved and resized the new install.
Entered the code - yahoooooooooooooooooooooooooooooooooo - all is good.

Thanks a Million.
Kind Regards
Bill

---

### Post by tom.swartz07 on 2010-01-05
> **wapfu said:**
> It worked .
All I can say Tom is Yahoooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo

It worked - and oh so well.::)

Had a glitch with gparted on the live CD not being able to unmount the swap sdb2 as it was in use? I was able to delete the old install though.
So went to the live gparted cd.
Deleted sdb2 and then found I couldn't move the new install sdb5 - couldnt even resize it.
So back to Ubuntu 9.1 live - where I moved and resized the new install.
Entered the code - yahoooooooooooooooooooooooooooooooooo - all is good.

Thanks a Million.
Kind Regards
Bill

Yay! I'm so glad it worked!

If you would like to investigate further and try to give yourself more room with your current partitions, let me know. Otherwise, you could mark the thread as solved from thread tools and others could learn from this also!

Either way, I hope you have a great New Year! 

Tom.

---


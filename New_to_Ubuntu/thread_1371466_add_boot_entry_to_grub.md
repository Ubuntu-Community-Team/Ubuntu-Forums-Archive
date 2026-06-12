---
title: "add boot entry to grub"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by Stan% on 2010-01-03
I restored an image of Win98 to a partition on the hard drive. 

Now I need to add a boot entry to grub but not sure how to.

My fdisk -l is:


```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006a487

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        9729    78148161    5  Extended
/dev/sda5            6691        9729    24410736    b  W95 FAT32
/dev/sda6               1        1216     9767425+  83  Linux
/dev/sda7            1217        1338      979933+  82  Linux swap / Solaris
/dev/sda8            1339        2554     9767488+  83  Linux
/dev/sda9            6309        6563     2048256    b  W95 FAT32
/dev/sda10           6054        6308     2048256    b  W95 FAT32

Partition table entries are not in disk order

```

sda9 is the partition with Win98; grub menu list is owned by root; can you show me how to do this in terminal, please.

---

### Post by kansasnoob on 2010-01-03
It would be much easier if I could see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It can be run either from your Ubuntu OS or the Live CD, it doesn't matter which.

That said I've never done Win 98 but I think it should be the same as any Win.

---

### Post by kansasnoob on 2010-01-03
FYI just giving myself a refresher course:

> If you have your Windows partition formatted with the FAT32 file system, it is recognized by GRUB and GRUB can 'read' it, so you can use the 'root' command.
If you have your Windows partition formatted with the NTFS file system, you might still be able to use the 'root' command, but it has been known to cause error messages.

Thought I remembered something like that:

[http://members.iinet.net.au/~herman546/p15.html#root_or_rootnoverify_](http://members.iinet.net.au/~herman546/p15.html#root_or_rootnoverify_)

---

### Post by Stan% on 2010-01-03
> **kansasnoob said:**
> It would be much easier if I could see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It can be run either from your Ubuntu OS or the Live CD, it doesn't matter which.

That said I've never done Win 98 but I think it should be the same as any Win.



Boot Info script reads:

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /DEFAULT.MNU /default.mnu

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006a487

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *             63   156,296,384   156,296,322   5 Extended
/dev/sda5         107,474,913   156,296,384    48,821,472   b W95 FAT32
/dev/sda6                 189    19,535,039    19,534,851  83 Linux
/dev/sda7          19,535,103    21,494,969     1,959,867  82 Linux swap / Solaris
/dev/sda8          21,495,033    41,030,009    19,534,977  83 Linux
/dev/sda9         101,338,083   105,434,594     4,096,512   b W95 FAT32
/dev/sda10         97,241,508   101,338,019     4,096,512   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

sda5: UUID="C4A1-4383" TYPE="vfat" 
sda6: UUID="dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a" TYPE="ext3" 
sda7: UUID="5c6c499e-6741-4554-b962-da9b66045e16" TYPE="swap" 
sda8: UUID="9add4667-85ef-49fe-8fcd-ad5c61e864ee" TYPE="ext3" 
sda9: LABEL="GATEWAY" UUID="236E-1609" TYPE="vfat" 
sda10: LABEL="Music" UUID="4B40-C6F5" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-16-generic/volatile type tmpfs (rw,mode=755)
/dev/sda8 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/stan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stan)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a

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

title		Ubuntu 8.10, kernel 2.6.27-16-generic
uuid		dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a
kernel		/boot/vmlinuz-2.6.27-16-generic root=UUID=dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-16-generic (recovery mode)
uuid		dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a
kernel		/boot/vmlinuz-2.6.27-16-generic root=UUID=dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a ro  single
initrd		/boot/initrd.img-2.6.27-16-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=9add4667-85ef-49fe-8fcd-ad5c61e864ee /home           ext3    relatime        0       2
# /dev/sda7
UUID=5c6c499e-6741-4554-b962-da9b66045e16 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


   7.9GB: boot/grub/menu.lst
   8.0GB: boot/grub/stage2
   8.0GB: boot/initrd.img-2.6.27-16-generic
   7.9GB: boot/initrd.img-2.6.27-7-generic
   7.9GB: boot/vmlinuz-2.6.27-16-generic
   7.9GB: boot/vmlinuz-2.6.27-7-generic
   8.0GB: initrd.img
   7.9GB: initrd.img.old
   7.9GB: vmlinuz
   7.9GB: vmlinuz.old
```

---

### Post by Paqman on 2010-01-03
> **Stan% said:**
> 
Now I need to add a boot entry to grub but not sure how to.


Open a terminal window and paste in the following command:
```
sudo update-grub
```

It should spot your Windows installation and add it to Grub automatically.

---

### Post by kansasnoob on 2010-01-03
> **Paqman said:**
> Open a terminal window and paste in the following command:
```
sudo update-grub
```

It should spot your Windows installation and add it to Grub automatically.

Only in grub2.

---

### Post by Stan% on 2010-01-03
> **Paqman said:**
> Open a terminal window and paste in the following command:
```
sudo update-grub
```

It should spot your Windows installation and add it to Grub automatically.

Nope. After updating grub the grub menu.lst has no entry for Windows and upon rebooting it goes right into Ubuntu; no option for Windows.

---

### Post by Paqman on 2010-01-03
> **Stan% said:**
> Nope. After updating grub the grub menu.lst has no entry for Windows and upon rebooting it goes right into Ubuntu; no option for Windows.

Sorry, didn't spot that you were running Hardy, as Kansasnoob pointed out.

You'll need to open the menu.lst as root.

```
sudo nano /boot/grub/menu.lst
```

Add an entry for Windows to the list of operating systems:
```
title		Microsoft Windows 98
root		(hd0,8)
savedefault
makeactive
chainloader	+1

```
Ctrl-X > Y > Enter. Then do:
```
sudo update-grub
```

(At least I think that's right, I haven't fooled about with Grub Legacy for a while...)

---

### Post by kansasnoob on 2010-01-03
OK booted into Intrepid we need to edit the menu.lst so from Terminal:

```
gksudo gedit /boot/grub/menu.lst
```

Here's a copy of your menu.lst, all of the stuff in red is what needs to be changed/added (note that I've changed the timeout from 3 to 10 and added a comment "#" to unhide the menu):

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
timeout		**[COLOR="Red"]10[/COLOR]**

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**[COLOR="Red"]#[/COLOR]**hiddenmenu

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
# kopt=root=UUID=dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a

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

title		Ubuntu 8.10, kernel 2.6.27-16-generic
uuid		dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a
kernel		/boot/vmlinuz-2.6.27-16-generic root=UUID=dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-16-generic (recovery mode)
uuid		dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a
kernel		/boot/vmlinuz-2.6.27-16-generic root=UUID=dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a ro  single
initrd		/boot/initrd.img-2.6.27-16-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		dcafcbae-8f8c-4c2f-8e0b-4568b7fbac6a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

[B][COLOR="Red"]# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry added for a non-linux OS on /dev/sda9
title		Microsoft Windows 98
root	        (hd0,8)
savedefault
makeactive
chainloader	+1[/COLOR][/B]

```

Then click on Save & File > Quit.

Good luck! I wouldn't know what a "good" Win 98 bootsector looks like :confused:

---

### Post by Stan% on 2010-01-03
kansasnoob,

Boot menu has Win98 listed but when I choose to boot it I get **Error 12 invalid device requested.**

If this gets too involved; this is an old computer that I can format the HHD and reinstall everything (starting with WIN98 of course). But if you want to try to work it out, I'm game. 

However, I go to work in 6 hours; got to get some sleep now. Will check back tomorrow.

Thanks for your help.

---

### Post by kansasnoob on 2010-01-03
I don't think I'd be much help beyond what I can read here:

[http://members.iinet.net.au/~herman546/p15.html#12_](http://members.iinet.net.au/~herman546/p15.html#12_)

I sort of like the sound of this:

> A second way to make Windows bootable in a logical partition is to use GParted -- LiveCD or Gnome Partition Editor in a Ubuntu Live CD to set the boot flag in the logical (Windows) partition. GRUB can't do that, but a partition editor can.
Then you need to either delete or at least 'comment out' the 'makeactive' command from your /boot/grub/menu.lst file so GRUB will skip trying to move the boot flag and won't be stopped with the 'Error 12' message.

---

### Post by Stan% on 2010-01-05
I formated HDD and reinstalled everything. Seemed like the best way to go. All is working proper.

Mark this thread solved.

---


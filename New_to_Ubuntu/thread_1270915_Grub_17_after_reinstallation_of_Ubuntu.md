---
title: "Grub 17 after reinstallation of Ubuntu"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by virtualsamana on 2009-09-20
Hey all,

I finally made the decision to get rid of Windows. I was previously running a dual boot with Jaunty and XP. I decided to make the whole HD ubuntu. I put in the live cd and chose install to replace the entire disk with Jaunty. When I restarted the computer I got the Grub 17 error.  I assumed that because I replaced my entire HD with Jaunty that the Grub would be deleted. Why am I getting this error?

Thanks

---

### Post by Liolikas on 2009-09-20
Based on grub documentation:

Error 17 claims that the partition that you're attempting to boot is of a format that GRUB does not recognize.

Make certain that:
-The GRUB configuration file (/boot/grub/menu.lst) points to the correct device AND partition. ---very possible that you partition numbers changed and there is no changes in menu.lst
-Make certain that the partition on the device is formatted and of a format that GRUB can read (such as EXT3).

---

### Post by presence1960 on 2009-09-20
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by yanceypd on 2009-09-20
Lots of stuff under other discussions Tutorials and tips regarding rest:)oring grub with Live CD.

---

### Post by 3rdalbum on 2009-09-20
Maybe I'm completely off-track here, but it's possible that the old version of GRUB is still in the MBR, and that when you installed Jaunty you chose to use the Ext4 filesystem. The Ext4 filesystem can't be read by the old version of GRUB.

Have you tried following a HOWTO on how to reinstall GRUB from the live CD?

---

### Post by virtualsamana on 2009-09-21
Thanks for all of the suggestions and help. I believe that I reformatted the drive using the EXT3 extension format. 

Presence1960: I ran the command you specified in the terminal and I received the following:

------------------------------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
------------------------------------------------------------------------------------------------------------------

Also, re-reading my first post it looks like I forgot to mention that I reformatted the entire drive in ext3 using gparted before I put in the ubuntu live CD for install. Could this have deleted the GRUB entirely?

---

### Post by presence1960 on 2009-09-21
> **virtualsamana said:**
> Thanks for all of the suggestions and help. I believe that I reformatted the drive using the EXT3 extension format. 

Presence1960: I ran the command you specified in the terminal and I received the following.



Also, re-reading my first post it looks like I forgot to mention that I reformatted the entire drive in ext3 using gparted before I put in the ubuntu live CD for install. Could this have deleted the GRUB entirely?
Did you download the Boot Info Script to the desktop before running that command? The error says the file the command says to execute is not on the desktop.

---

### Post by virtualsamana on 2009-09-22
Duh! Thanks Presence. I totally didn't load the bootloader. I just ran it and I got back the following:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5005471f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,577,775   312,577,713   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44f944f8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="C41C4CA21C4C90FA" LABEL="Dub" TYPE="ntfs" 
/dev/sdb1: UUID="adc681db-4a6f-494f-995a-ef8c10d59661" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="db0039f3-03bb-4594-a89b-ed94e276e8d7" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
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
# kopt=root=UUID=adc681db-4a6f-494f-995a-ef8c10d59661 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=adc681db-4a6f-494f-995a-ef8c10d59661

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        adc681db-4a6f-494f-995a-ef8c10d59661
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=adc681db-4a6f-494f-995a-ef8c10d59661 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        adc681db-4a6f-494f-995a-ef8c10d59661
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=adc681db-4a6f-494f-995a-ef8c10d59661 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        adc681db-4a6f-494f-995a-ef8c10d59661
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=adc681db-4a6f-494f-995a-ef8c10d59661 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=db0039f3-03bb-4594-a89b-ed94e276e8d7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  70.9GB: boot/grub/menu.lst
  70.8GB: boot/grub/stage2
  70.8GB: boot/initrd.img-2.6.28-11-generic
  70.8GB: boot/vmlinuz-2.6.28-11-generic
  70.8GB: initrd.img
  70.8GB: vmlinuz
```

---

### Post by presence1960 on 2009-09-22
Boot the Ubuntu Live CD. Choose "try Ubuntu without any changes", when the desktop loads you will fix GRUB like this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

When you reboot go into BIOS and set your 80 GB disk (sdb) to boot first in the hard disk boot order. Save changes to CMOS. Exit and continue booting. You should be good to go.

---

### Post by virtualsamana on 2009-09-22
Thank you, Thank you, Thank you!

---

### Post by presence1960 on 2009-09-23
Glad you got it working! Enjoy Ubuntu.

---


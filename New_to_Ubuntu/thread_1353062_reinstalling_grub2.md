---
title: "reinstalling grub2?"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by garyed on 2009-12-12
After two years I finally understand grub now comes grub2 & I'm a little lost. I've read up enough to know a little about the the /etc/default/grub
& /etc/grub.d/*  files making up the /boot/grub/grub.cfg but that's about it. I'm about to do an install of 64 Studio & before I do I'd like to figure out how to reinstall grub2 if I mess things up. I'm planning on deleting & changing some partitions which is why I'm trying to get a grip on things now if it possible. My current setup is:

HD - 1  Windows XP - NTFS all one partition
HD - 2  Windows data - fat32  all one partition
HD - 3  partitioned with : 
                          Ubuntu Studio - Gusty  ext3   
                          Ubuntu Studio - Karmic 64 ext4 
                          Ubuntu Studio - Karmic 386 ext3

I don't want to touch the first two windows drives.
I also want to keep my Gusty partition on HD 3.
I plan on removing the two versions of Karmic on the third drive, making the two partitions one & installing 64 Studio in the space where they used to be. I'm just trying to plan on being able to reinstall grub2 if things go wrong.
Any ideas?

---

### Post by garyed on 2009-12-12
nudge...
All right, bump...........

---

### Post by ranch hand on 2009-12-12
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by garyed on 2009-12-12
Thanks,

A lot of great info

---

### Post by ranch hand on 2009-12-12
It is a good idea to ignore the instructions for editing files.  This is very rarely needed.  What you need is the "update-grub" and "grub-install /dev/<your drive> (in my case it is sda).

---

### Post by garyed on 2009-12-12
I started another thread because I thought I understood what I was doing but I was wrong.
Now I can't boot after my new installation.
I need help now. I'm in trouble.

---

### Post by ranch hand on 2009-12-12
Where is this thread?

---

### Post by Darkz_Soul on 2009-12-12
What happens when you boot? do you get to a recovery console. If so it can be more easily fixed... I had a corrupt grub and I was able to use the recover console to get my Ubuntu booting

---

### Post by Darkz_Soul on 2009-12-12
If you want to try this recovery using the live disk 9.1 at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
this is what i used to fix grub... i also had been able to use recovery to get to ubuntu so i didn't need the live distro

---

### Post by presence1960 on 2009-12-13
before you go installing and changing stuff let's get a clear idea of what you have now. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by garyed on 2009-12-13
Thanks for the help,
I've been banging my head against the wall for a while now.
To answer some questions:
I just bumped my thread  "I can't boot after new installation"
I don't get anything but a grub error & I can't go anywhere.
Luckily I did make a semi grub2 recovery floppy that gets me to a grub prompt.
I can get into windows by doing these commands in order:
```
set root=(hd0,1)
chainloader +1
boot 
```
I can't get into Ubuntu though ( I don't know how)
I was hoping there was some commands I could do at the grub prompt that could fix my mbr & get me back to where I was.
I'm in the process of burning a 9.10 live CD but I'm wore out & got to get some sleep. It would probably be easier to do another install but I'd like to know how to fix grub2.
I'll check back in the morning.

---

### Post by ranch hand on 2009-12-13
Use the instructions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

ignoring the file editing part and you should be up and running.

You do need that LiveCD to do that.  I do not think reinstalling is needed at all.

When you boot to the LiveCD you can go and look at all your files and I think you will find they look fine.  You just need grub on the MBR.

---

### Post by garyed on 2009-12-13
> **ranch hand said:**
> Use the instructions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
......
Here's what I've done:
Booted 9.10 Live CD, get to terminal then  
```

sudo fdisk -l (I'll post results below)
sudo mount /dev/sdb6 /mnt
sudo mount --bind /dev /mnt/dev

```
When I get to the chroot part I do:
```
sudo chroot /mnt
```
& get:
> cannot run command '/bin/bash' exec format error 

```
sudo update-grub 
```
gives me:
```
error cannot find device for '/ '
```


Results of fdisk -l:

Disk /dev/sda 160gig  (my Windows XP HD)
/dev/sda1  *  HPFS/NTFS  

Disk /dev/sdb 160 gig (my Linux HD)
/dev/sdb1   83 Linux  (Gusty ext3)
/dev/sdb2   5  Extended
/dev/sdb5   82 Swap
/dev/sdb6   83 Linux  (Ubuntu Studio 9.10 ext4) 
/dev/sdb7   82 Swap
/dev/sdb8   83 Linux   (64 Studio ext3) (everything was working until this OS was installed on this partition)

---

### Post by ranch hand on 2009-12-13
Here is the list of commands that I use every day to update testing OS' remotely, I have boinc running on one testing (10.04) install and do not want to leave it for much time not running so I do as much to the other installs as possible remotely;
```

sudo mkdir /mnt/Daily-root
sudo mount /dev/sda13 /mnt/Daily-root/
sudo mount -o bind /proc /mnt/Daily-root/proc
sudo mount -o bind /dev /mnt/Daily-root/dev
sudo mount -o bind /dev/pts /mnt/Daily-root/dev/pts
sudo mount -o bind /sys /mnt/Daily-root/sys
sudo cp /etc/resolv.conf /mnt/Daily-root/etc/resolve.conf
sudo chroot /mnt/Daily-root /bin/bash

```
I am new to chrooting too.  I just learned about it last testing cycle (9.10).  You will note that my partitions are labeled.  I only have one place where the partition is defined by its number.

Where mine says "Daily-root" put your "sdb6".

If that does not work use gparted to label your partition to "Studio" and insert that for "Daily-root".

This is a more complete chroot set  of commands and if you get it to work I would save it on your system.  This has your network up and running (wired anyway) and everything.

---

### Post by presence1960 on 2009-12-13
run the boot info script as requested so we can see exactly your setup and boot process!

---

### Post by garyed on 2009-12-13
> **presence1960 said:**
> run the boot info script as requested so we can see exactly your setup and boot process!

Okay here goes:
> 
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #58 for boot/grub/stage2 /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

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
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

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

sdb8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92819281

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005598e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    97,659,134    97,659,072  83 Linux
/dev/sdb2          97,659,135   312,576,704   214,917,570   5 Extended
/dev/sdb5         300,415,563   312,576,704    12,161,142  82 Linux swap / Solaris
/dev/sdb6          97,659,261   195,318,269    97,659,009  83 Linux
/dev/sdb7         292,077,828   300,415,499     8,337,672  82 Linux swap / Solaris
/dev/sdb8         195,318,333   292,077,764    96,759,432  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92c092c0

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   488,392,064   488,392,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="906C4EA36C4E83C6" LABEL="Duality" TYPE="ntfs" 
/dev/sdb1: UUID="19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="d2f0f089-7888-41be-8a33-7123fab40f40" TYPE="swap" 
/dev/sdb6: UUID="f766ec52-a79a-469b-b5a7-7fbd5449517c" TYPE="ext4" 
/dev/sdb7: UUID="08b0b7b1-fc17-4fa2-b294-18ae01bc3e03" TYPE="swap" 
/dev/sdb8: UUID="32302d56-0a81-4e2c-b0dd-11675dbfdae0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="ZADA" UUID="4463-14F5" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
default	       4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10
splashimage=(hd2,0)/boot/grub/splash1.xpm.gz 
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
# kopt=root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro single
initrd		/boot/initrd.img-2.6.22-14-rt

# title		Ubuntu 7.10, kernel 2.6.22-14-generic
# root		(hd2,0)
# kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro quiet splash
# initrd		/boot/initrd.img-2.6.22-14-generic
# quiet

# title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
# root		(hd2,0)
# kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro single
# initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=d2f0f089-7888-4100-be8a-337123fab40f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hda1      /media/music_c   ntfs-3g defaults,utf8,umask=007,gid=46 0 1
/dev/sda1      /media/music_d   vfat   iocharset=utf8,umask=000 0  0    

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.22-14-generic
    .0GB: boot/initrd.img-2.6.22-14-generic.bak
    .0GB: boot/initrd.img-2.6.22-14-rt
    .0GB: boot/initrd.img-2.6.22-14-rt.bak
    .0GB: boot/vmlinuz-2.6.22-14-generic
    .0GB: boot/vmlinuz-2.6.22-14-rt
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

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
set default="4"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set f766ec52-a79a-469b-b5a7-7fbd5449517c
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
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-9-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set f766ec52-a79a-469b-b5a7-7fbd5449517c
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=f766ec52-a79a-469b-b5a7-7fbd5449517c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set f766ec52-a79a-469b-b5a7-7fbd5449517c
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=f766ec52-a79a-469b-b5a7-7fbd5449517c ro single 
	initrd	/boot/initrd.img-2.6.31-9-rt
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 906c4ea36c4e83c6
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 7.10, kernel 2.6.22-14-rt (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5
	linux /boot/vmlinuz-2.6.22-14-rt root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro quiet splash
	initrd /boot/initrd.img-2.6.22-14-rt
}
menuentry "Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5
	linux /boot/vmlinuz-2.6.22-14-rt root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro single
	initrd /boot/initrd.img-2.6.22-14-rt
}
menuentry "Ubuntu 7.10, memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5
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
UUID=f766ec52-a79a-469b-b5a7-7fbd5449517c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=08b0b7b1-fc17-4fa2-b294-18ae01bc3e03 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


  50.0GB: boot/grub/grub.cfg
  50.0GB: boot/initrd.img-2.6.31-9-rt
  50.0GB: boot/vmlinuz-2.6.31-9-rt
  50.0GB: initrd.img
  50.0GB: vmlinuz

=========================== sdb8/boot/grub/grub.cfg: ===========================

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
set default="4"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set f766ec52-a79a-469b-b5a7-7fbd5449517c
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
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-9-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set f766ec52-a79a-469b-b5a7-7fbd5449517c
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=f766ec52-a79a-469b-b5a7-7fbd5449517c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set f766ec52-a79a-469b-b5a7-7fbd5449517c
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=f766ec52-a79a-469b-b5a7-7fbd5449517c ro single 
	initrd	/boot/initrd.img-2.6.31-9-rt
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 906c4ea36c4e83c6
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 7.10, kernel 2.6.22-14-rt (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5
	linux /boot/vmlinuz-2.6.22-14-rt root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro quiet splash
	initrd /boot/initrd.img-2.6.22-14-rt
}
menuentry "Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5
	linux /boot/vmlinuz-2.6.22-14-rt root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro single
	initrd /boot/initrd.img-2.6.22-14-rt
}
menuentry "Ubuntu 7.10, memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb8
UUID=32302d56-0a81-4e2c-b0dd-11675dbfdae0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=d2f0f089-7888-41be-8a33-7123fab40f40 none            swap    sw              0       0
# /dev/sdb7
UUID=08b0b7b1-fc17-4fa2-b294-18ae01bc3e03 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb8: Location of files loaded by Grub: ===================


 100.0GB: boot/grub/grub.cfg
 100.0GB: boot/initrd.img-2.6.31-9-rt
 100.0GB: boot/vmlinuz-2.6.31-9-rt



---

### Post by garyed on 2009-12-13
I'm pretty sure in a half hour or so I could solve this problem by reinstalling the OS again but more for future problems than anything else 
I would like to solve this without doing that .

I find it hard to believe the guys who wrote Grub2 would not make a simple command to put it back. When you do a new install it finds your OS's & does it so why not do it when you have a problem.

---

### Post by ranch hand on 2009-12-13
I would run the chroot stuff I gave you from your 9.10 LiveCD and try that once.

If that doesn't work I would use a 9.04 or older (like 7.10) LiveCD and reinstall grub-legacy to the MBR.  I am assuming that you know how to do that, if not just ask.

You need to run;
```

sudo update-grub

```
if you get grub2 reinstalled to get your grub.cfg file up to date.

If you use grub-legacy you will have to edit the menu.lst and hope it works as ext4 is not really supported by grub-legacy from that period, you may need to get the version from 9.04.

---

### Post by presence1960 on 2009-12-13
============================= Boot Info Summary: ==============================

[COLOR="Red"]=> Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive
in partition #58 for boot/grub/stage2 /boot/grub/menu.lst.[/COLOR]
=> No boot loader is installed in the MBR of /dev/sdb
=> Windows is installed in the MBR of /dev/sdc

In red is your problem. First I have to ask if you have any disk in RAID. You can go to gparted and look. here is what you need to know and how to remove RAID:

Also there is a bug in 9.10 that mounts raid arrays that you have deleted. To fix it first turn off raid in your bios.  Then load up the 9.10 live CD and open gparted.  If you get a drive with a funny name like nvidia_ahahdhjdfsjkf then you have mounted a raid drive that you don't want.

To get rid of it, Open a terminal and type ```
dmraid -E -r /dev/name_of_your_disk
```.

substitute appropriate disk for name _of_your_disk such as sda, sdb or sdc.

Once you have erased the raid meta data you should see the funny named disk disappear after restarting gparted.

If you don't have RAID on one of your disks then boot the Live CD to reinstall GRUB2 (1.97) and do this or do this after removing RAID to reinstall GRUB2:

Run in terminal ```
sudo mount /dev/sdb6 /mnt
```
This will mount your 9.10 root device (sdb6) 

Then run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sda
``` This will put GRUB2 on MBR of sda. if you want it on sdb substitute sdb at end of command. Reboot.

Go into BIOS and make sure whatever disk you put GRUB on MBR is first to boot in the hard disk boot order. Save changes to CMOS and continue booting. Boot into Ubuntu 9.10 and open a terminal and run ```
sudo update-grub
``` This will refresh the GRUB2 menu.

Here is a link on how to reinstall GRUB2 from Live CD for your reference: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

P.S. see pic below for where in gparted to look for name of disk

---

### Post by garyed on 2009-12-13
First I want to thank you guys for all the help.
I really do appreciate it but I just couldn't take it any more.

Nothing seemed to solve the problem.
I followed all the directions several times but I still couldn't do it.
every time I ran ```
update-grub
``` I got the same error about not finding '/'
Every time I tried chroot I got the an error too.
I finally installed 9.10 in place of the 64Studio since I never got a chance to use it & that solved the grub problem.
I really wanted to find a solution to this because the next time I may not be in a position to reinstall. 
As I was watching the screen during my new install I noticed at one point it said installing bootloader. It took about a second & then moved on to the next procedure. All I could think of is why does it have to be so difficult. Why can't the grub-install command find everything the same way? Just venting but I'm still a Linux Lover.

---

### Post by talsemgeest on 2009-12-13
> **garyed said:**
> First I want to thank you guys for all the help.
I really do appreciate it but I just couldn't take it any more.

Nothing seemed to solve the problem.
I followed all the directions several times but I still couldn't do it.
every time I ran ```
update-grub
``` I got the same error about not finding '/'
Every time I tried chroot I got the an error too.
I finally installed 9.10 in place of the 64Studio since I never got a chance to use it & that solved the grub problem.
I really wanted to find a solution to this because the next time I may not be in a position to reinstall. 
As I was watching the screen during my new install I noticed at one point it said installing bootloader. It took about a second & then moved on to the next procedure. All I could think of is why does it have to be so difficult. Why can't the grub-install command find everything the same way? Just venting but I'm still a Linux Lover.
If it fails again, give the instructions [here](http://ubuntuforums.org/showthread.php?t=1014708) a try.

---

### Post by garyed on 2009-12-17
> **talsemgeest said:**
> If it fails again, give the instructions [here](http://ubuntuforums.org/showthread.php?t=1014708) a try.
I finally got it!!

Thanks, 
I tried that link & it didn't work at first but it did with a small variation & it was really simple. 
I did this after booting from the live CD:
```

sudo mount /dev/sdb6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
 
```
then rebooted & got a grub menu to get me into my original system & did:
 ```
sudo update-grub
``` 
That was it & it picked up my new install of 64 Studio.

---

### Post by presence1960 on 2009-12-17
> **garyed said:**
> I finally got it!!

Thanks, 
I tried that link & it didn't work at first but it did with a small variation & it was really simple. 
I did this after booting from the live CD:
```

sudo mount /dev/sd6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
 
```
then rebooted & got a grub menu to get me into my original system & did:
 ```
sudo update-grub
``` 
That was it & it picked up my new install of 64 Studio.

WOW!! Glad you got it working. I believe I gave you those commands in post # 19. But if you figured it out on your own even better for you. Enjoy Ubuntu!

---

### Post by ranch hand on 2009-12-17
Good work!!!!

---

### Post by garyed on 2009-12-17
> **presence1960 said:**
> WOW!! Glad you got it working. I believe I gave you those commands in post # 19. But if you figured it out on your own even better for you. Enjoy Ubuntu!

Looking back I see you did but I mounted /dev/sdb8 because that was my new install I figured that's where the grub files should be but I couldn't get it working. I gave up for the time being & reformatted sd8 & installed Karmic on it & everything worked. After learning a little more how to access my kernels with a grub boot disk I decided to reinstall 64 Studio again on that partition assuming the same thing would happen so I could work on getting this solved again.

---

### Post by presence1960 on 2009-12-17
> **garyed said:**
> Looking back I see you did but I mounted /dev/sdb8 because that was my new install I figured that's where the grub files should be but I couldn't get it working. I gave up for the time being & reformatted sd8 & installed Karmic on it & everything worked. After learning a little more how to access my kernels with a grub boot disk I decided to reinstall 64 Studio again on that partition assuming the same thing would happen so I could work on getting this solved again.

No problem, as long as you got it working and hopefully gained some knowledge. That's how we learn- try new things and fixing the things we break!

---

### Post by talsemgeest on 2009-12-17
> **garyed said:**
> I finally got it!!

Thanks, 
I tried that link & it didn't work at first but it did with a small variation & it was really simple. 
I did this after booting from the live CD:
```

sudo mount /dev/sd6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
 
```
then rebooted & got a grub menu to get me into my original system & did:
 ```
sudo update-grub
``` 
That was it & it picked up my new install of 64 Studio.
Oh, so what was the variation? If it is something good I might have to add it into the guide :)

---

### Post by garyed on 2009-12-18
> **talsemgeest said:**
> Oh, so what was the variation? If it is something good I might have to add it into the guide :)

I tried it twice & it didn't work. 
The only thing that I did different is the commands I posted.
I mounted /mnt without having to make the directory first.
I don't see how that could make a difference but it does save one step.
I also used the slash afterwards /mnt/ instead of /media/sdb6
I checked both mount points with ls to make sure they were mounted before I issued the grub command.  


I'm just thankful for all the help you guys have given.

---

### Post by talsemgeest on 2009-12-18
Hmm, thanks for that. I can't see why it would make a difference, but since it does... ;)

---

### Post by garyed on 2009-12-18
> **talsemgeest said:**
> Hmm, thanks for that. I can't see why it would make a difference, but since it does... ;)

It might have something to do with a mixture of 1-SATA & 2-ATA drives on my system. Each version labels them different /dev/X but Grub2 worked fine every time on a new install & picked up all my OS's & Grub legacy didn't.

---


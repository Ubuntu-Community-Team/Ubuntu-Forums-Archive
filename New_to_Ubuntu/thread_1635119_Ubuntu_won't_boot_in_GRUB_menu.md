---
title: "Ubuntu won't boot in GRUB menu"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by jmitche1 on 2010-12-01
I am having troubles getting ubuntu to start up.

I dual boot windows 7 and Ubuntu 10.04 through wubi and was told about The Burg Project to switch how GRUB looks on logon. I tried to install The Burg Project and it "Failed to install." I gave up, and the next time I shutdown my computer I found I could not get farther than the page that asks whether I want to boot Windows or Ubuntu. When I choose Ubuntu a quick black screen flashes and says failure to boot (or something around those lines) followed by a black screen. 

Does anyone have any suggestions? I have some documents saved in my ubuntu partition that I need soon and have been trying also to find ways to view them on windows. DiskInternals Linux Reader doesn't seem to be working as it searches for files for hours with no end in sight. 

I'd really love to just get things back to normal and any help from anyone would be greatly appreciated!

---

### Post by Rubi1200 on 2010-12-01
Hi,
are you able to boot into Windows normally?

We need you to please boot the computer with a LiveCD and choose to try not install Ubuntu.

Then, follow the instructions in the link at the bottom of my post to run the boot info script.

Post the results back here and we will take a look.

Thanks.

---

### Post by jmitche1 on 2010-12-01
I am sorry, I am still pretty new to ubuntu and installed the dualboot using a usb drive. I can access windows. Do I need to burn an install CD from the ubuntu website and then run the instructions in your previous post?

Thank you for your help.

---

### Post by Rubi1200 on 2010-12-01
To be honest, that would be the best thing to do right now.

There is a fix for Wubi installs, but I am being cautious because you tried to install BURG and I want to make sure there are no leftover problems with that.

In any event, I am providing the links for the Wubi issues/fixes:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

---

### Post by jmitche1 on 2010-12-01
Thank you,
I will try to burn a disk tonight. 

In the mean time is there anyway for me to just view my documents saved on the Ubuntu partition while I am in windows 7? I have one important Open office document that didn't make my most recent back up and need access to it as soon as possible. 

I don't know if they do the right thing but I downloaded both Ext2Read and DiskInternals Ubuntu Reader and haven't quite figured out how to run them.

---

### Post by jmitche1 on 2010-12-01
Thank you for your help and patience. 
These are my results:

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   461,307,903   461,305,856   7 HPFS/NTFS
/dev/sda2         461,307,904   488,390,655    27,082,752   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       48fd8d9a-042d-453b-a51a-f07f7a51c531   ext4                                     
/dev/sda1        6F77649628C88E3E                       ntfs                                     
/dev/sda2        D6588C55588C35F1                       ntfs       RECOVERY                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 6f77649628c88e3e
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 6f77649628c88e3e
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-23-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6f77649628c88e3e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6f77649628c88e3e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6f77649628c88e3e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6f77649628c88e3e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6f77649628c88e3e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6f77649628c88e3e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6f77649628c88e3e
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set d6588c55588c35f1
	chainloader +1
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

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


    .3GB: boot/grub/grub.cfg
   2.0GB: boot/initrd.img-2.6.32-25-generic
    .5GB: boot/initrd.img-2.6.35-22-generic
   5.9GB: boot/initrd.img-2.6.35-23-generic
   8.6GB: boot/vmlinuz-2.6.32-25-generic
   8.3GB: boot/vmlinuz-2.6.35-22-generic
   8.3GB: boot/vmlinuz-2.6.35-23-generic
   5.9GB: initrd.img
    .5GB: initrd.img.old
   8.3GB: vmlinuz
   8.3GB: vmlinuz.old

---

### Post by bcbc on 2010-12-01
You can access your data from the live cd:
```
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
nautilus /mnt
```

Or from windows: [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) (download ext2read and point it at c:\ubuntu\disks\root.disk)

You can probably repair your ubuntu by following those links Rubi1200 posted. It seems like the burg install failed (which is a good thing, otherwise you wouldn't be booting windows either).

---

### Post by Rubi1200 on 2010-12-02
Hi jmitche1,
thanks for posting the results of the script.

I agree with bcbc that you can go ahead and repair the Wubi install.

I just wanted to be careful because I have seen vestiges of bootloader files left over after failed installs and I just wanted to make sure of what we were dealing with.

---


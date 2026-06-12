---
title: "Grub Rescue&gt; Prompt Please Help"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by beegary on 2010-05-07
I would really appreciate some help here.

My teenage cousin had a bricked Asus EeePc, I got it up and running by removing Windows and installing Karmic. I did this in January: [http://ubuntuforums.org/showthread.php?t=1392484](http://ubuntuforums.org/showthread.php?t=1392484)

Everything has been going fine until now. She lives 120miles away so I am unable to pick it up to fix it. She rebooted today and got this:

```
grub loading...
Error: file not found
Grub rescue>
```

From memory I think I did a fresh install of Karmic, with a separate /home directory. I asked her to type in ls @ the rescue prompt, this is the result:

```
hd0 hd0,1 hd1, hd2, hd1,1
```


Is anyone able to help me get it booting for her again? The only thing I can think of is that an update has bricked her Grub setting or it has lost the version to boot?
I could mail her a USB stick to re-install (i would give her Lucid Brilliant out of the box) but she has some school work she would like to keep.

I have had so much useful help here, come on folks I relying on you (so is my cousin)

Cheers
B

---

### Post by Mark_in_Hollywood on 2010-05-07
GRUB errors are tough. I had this happen a few weeks ago, that is, I got a GRUB 

>

prompt.

I think it was caused by Win7 and System Mechanic f@#$T my disk over. After a few reboots, and no success, I removed all installed cables, USB, sound, not the video. I again rebooted. That worked. So here is my idea for you and I hope you won't take offense.

Open the laptop, carefully noting were all the parts came from (screws mostly) and make a map (on paper of them). 

Remove the hard drive. Wait 30 minutes. Put the drive back. Close the laptop up.

That's my advice and I'm sticking to it.

Good Luck.

---

### Post by phillw on 2010-05-07
> **beegary said:**
> I would really appreciate some help here.



Your first port of call for things Grub should be [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

There's a lot on there, so take your time and work through it.

If that thread and re-installing grub does not work (which it  nearly always does), it is possible that the recent update of the kernel has gotten grub all confused, in which case you can do this [http://forum.phillw.net/viewtopic.php?f=4&t=35](http://forum.phillw.net/viewtopic.php?f=4&t=35)

Regards,

Phill.

---

### Post by beegary on 2010-05-08
> **phillw said:**
> Your first port of call for things Grub should be [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
There's a lot on there, so take your time and work through it.
If that thread and re-installing grub does not work (which it  nearly always does), it is possible that the recent update of the kernel has gotten grub all confused, in which case you can do this [http://forum.phillw.net/viewtopic.php?f=4&t=35](http://forum.phillw.net/viewtopic.php?f=4&t=35)

Regards,

Phill.

Thank you philw, I have had some success following this:
```


[LIST]
[*]ls  This will display the known devices and partitions.  From this information, the user must determine the device and partition  on which the system is installed.
[*]search -f /vmlinuz This should find linux kernels located in  the partitions located by "ls".
[*]set Check the current settings. Note the prefix  listing. If it is not pointing to the correct location:
[LIST]
[*]set  prefix=(hdX,Y)/boot/grub  Examples: sda1 is (hd0,1), sdb5 is  (hd1,5)
[/LIST]
 
[*]set root=(hdX,Y)  X is the device/drive, starting with 0. Y  is the partition, starting with 1. (Example: (hd0,1) is sda1. (hd3,5) is  sdc5.
[LIST]
[*]For Wubi installs, use: set root=(loop0)
[/LIST]
 
[*]ls /boot  Inspect the contents. The user should see varioius  kernels, initrd images and the grub folder. If not, use the ls command  to inspect the device and attempt to find these files and folders. If  necessary, set another device as root.
[*]insmod /boot/grub/linux.mod  Load the linux module. Without  this module loaded, the user will receive an "Unknown command linux"  message when trying to load the kernel.
[*]linux /vmlinuz root=/dev/sdXY ro  Load the linux kernel,  substituting the correct designations for "X" and "Y" (example: sda1).  The user will see a message showing the kernel has been loaded. (See  graphic above)
[LIST]
[*]Note: For Wubi installs within Windows, use this  code: linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro
[/LIST]
 
[*]initrd /initrd.img  Load the initrd image. When pressing  enter, the user may or may not see a message in the terminal. (See  highlighted graphic above)
[*]boot
[/LIST]

```

The problem is that It will be a bit difficult for me to get her booting into a Live Usb image. That is my last option really. I would have to send her a USB stick in the post.
We managed to use the commands above to find out that:
The prefix is incorrectly set to hd0,0
Using the commands above grub is on hd1,1. So we set the prefix and root to hd1,1.
When I get her to ls boot, a list of kernels etc is shown.
But I am unable to get the next steps to work:
Is hd1,1 sdb1?
Basically we can get to the stage of entering boot but it says the device doesn't exist?

Is there a way of changing the prefix and root settings so they remain after reboot from within Grub rescue>????

---

### Post by beegary on 2010-05-08
bump

---

### Post by beegary on 2010-05-10
I always manage to kill my own threads! Echo echo

---

### Post by beegary on 2010-05-13
OK so I worked a solution, thought I would post it here in the rare case it may help someone else.
I remembered that I had originally setup 9.10 with a separate /home for my cousin. So I mailed her a USB boot installation of 10.04. With the boot info scripts saved to the desktop.
I got her to run the scripts and email me the results.
Then I wrote some instructions for installing 10.04 using manual partition setup.

She now has a shiny new 10.04 installation, booting without problems.

Super duper.

I have posted the result of the boot info script below, in case someone can tell me what the original problem with grub was. I assume it was something to do with this entry...
> # / was on /dev/sdb1 during installation
UUID=bfbe7940-8af7-4783-aaf0-0daeea10f770 /               ext4    errors=remount-ro 0       1


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     7,871,849     7,871,787  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    13,799,834    13,799,772  83 Linux
/dev/sdb2          13,799,835    15,759,764     1,959,930  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2063 MB, 2063073280 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4029440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62     4,027,519     4,027,458   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       051346fa-fdd2-4c10-a7c7-ca9ef7c22e28   ext3                                     
/dev/sda1        b70efd77-3439-4024-847c-3f09fd67aff5   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        bfbe7940-8af7-4783-aaf0-0daeea10f770   ext4                                     
/dev/sdb2        1b4284ce-b3d2-4cc8-bde0-d0291fcc46ff   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        B256-F3ED                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set bfbe7940-8af7-4783-aaf0-0daeea10f770
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set bfbe7940-8af7-4783-aaf0-0daeea10f770
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=bfbe7940-8af7-4783-aaf0-0daeea10f770 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set bfbe7940-8af7-4783-aaf0-0daeea10f770
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=bfbe7940-8af7-4783-aaf0-0daeea10f770 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=bfbe7940-8af7-4783-aaf0-0daeea10f770 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=b70efd77-3439-4024-847c-3f09fd67aff5 /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=1b4284ce-b3d2-4cc8-bde0-d0291fcc46ff none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.8GB: boot/grub/core.img
   2.8GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.31-14-generic
   2.5GB: boot/vmlinuz-2.6.31-14-generic
    .8GB: initrd.img
   2.5GB: vmlinuz
```

---


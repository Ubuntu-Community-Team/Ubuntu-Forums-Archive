---
title: "grub error 15 file not found"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by saadlulu on 2009-12-28
hey people..

i have windows xp and ubuntu on the same physical hard disk but on different partitions, what i did was i wanted to add linux backtrack to them, so i did
after i installed backtrack to them, and now trying to access ubuntu, and error comes saying file not found.

i tried to fix this by going to the command line and finding my grub by typing 
```
 find /boot/grub/stage1 
```and it shows that its hd( 0,8 )

so i changed it from hd(0.6) to hd(0, 8 )and tried booting, still doesnt work.
tried all hd(0,0~9) still no luck at all. its either its no such file or cannot be accessed.

please help anyone :(

---

### Post by saadlulu on 2009-12-28
* bump *

---

### Post by mapes12 on 2009-12-28
You could try reinstalling GRUB from a LiveCD: [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by kansasnoob on 2009-12-28
Since the "find" command found a stage1 I think you still have legacy grub so I doubt those grub2 restore steps are going to help you.

The most helpful thing would be to see the results of the Boot Info Script run from Live CD as explained here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by saadlulu on 2009-12-28
> **kansasnoob said:**
> Since the "find" command found a stage1 I think you still have legacy grub so I doubt those grub2 restore steps are going to help you.

The most helpful thing would be to see the results of the Boot Info Script run from Live CD as explained here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)


here is the output result
hope this helps with anything 
```
 ============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x70505c5f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,482,874    20,482,812   7 HPFS/NTFS
/dev/sda2          20,482,875   195,366,464   174,883,590   f W95 Ext d (LBA)
/dev/sda5          52,436,223   156,296,384   103,860,162   7 HPFS/NTFS
/dev/sda6          20,483,001    49,785,434    29,302,434  83 Linux
/dev/sda7          49,785,498    52,436,159     2,650,662  82 Linux swap / Solaris
/dev/sda8         156,296,448   183,655,079    27,358,632  83 Linux
/dev/sda9         183,655,143   195,366,464    11,711,322  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0444606444605A86" TYPE="ntfs" 
/dev/sda5: UUID="32B0C1C3B0C18E33" LABEL="Data" TYPE="ntfs" 
/dev/sda6: UUID="b4020aef-7880-4f1b-94a1-c58d5a09e481" TYPE="ext4" 
/dev/sda7: UUID="553556d7-52f8-40ae-a3e3-069cb544990b" TYPE="swap" 
/dev/sda8: UUID="f990eed7-f769-453a-bc4d-0ef22066bdf6" TYPE="ext4" 
/dev/sda9: UUID="1e516149-7fbe-4bce-aa95-ff33283cc561" SEC_TYPE="ext2" TYPE="ext3" 

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
/dev/sda6 on /media/b4020aef-7880-4f1b-94a1-c58d5a09e481 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sda8 on /media/f990eed7-f769-453a-bc4d-0ef22066bdf6 type ext4 (rw,nosuid,nodev,uhelper=devkit)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoftsudo bash ~/Desktop/boot_info_script*.sh Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set b4020aef-7880-4f1b-94a1-c58d5a09e481
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set b4020aef-7880-4f1b-94a1-c58d5a09e481
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=b4020aef-7880-4f1b-94a1-c58d5a09e481 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set b4020aef-7880-4f1b-94a1-c58d5a09e481
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=b4020aef-7880-4f1b-94a1-c58d5a09e481 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set b4020aef-7880-4f1b-94a1-c58d5a09e481
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b4020aef-7880-4f1b-94a1-c58d5a09e481 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set b4020aef-7880-4f1b-94a1-c58d5a09e481
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b4020aef-7880-4f1b-94a1-c58d5a09e481 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0444606444605a86
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=b4020aef-7880-4f1b-94a1-c58d5a09e481 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=f990eed7-f769-453a-bc4d-0ef22066bdf6 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=553556d7-52f8-40ae-a3e3-069cb544990b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  10.4GB: boot/grub/grub.cfg
  10.4GB: boot/initrd.img-2.6.31-14-generic
  10.4GB: boot/initrd.img-2.6.31-16-generic
  10.4GB: boot/vmlinuz-2.6.31-14-generic
  10.4GB: boot/vmlinuz-2.6.31-16-generic
  10.4GB: initrd.img
  10.4GB: initrd.img.old
  10.4GB: vmlinuz
  10.4GB: vmlinuz.old

=========================== sda9/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1e516149-7fbe-4bce-aa95-ff33283cc561 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1e516149-7fbe-4bce-aa95-ff33283cc561

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=1e516149-7fbe-4bce-aa95-ff33283cc561/boot/grub/splash.xpm.gz

title        Ubuntu 8.10, kernel 2.6.29.4
uuid        1e516149-7fbe-4bce-aa95-ff33283cc561
kernel        /boot/vmlinuz-2.6.29.4 root=UUID=1e516149-7fbe-4bce-aa95-ff33283cc561 ro quiet splash 
initrd        /boot/initrd.img-2.6.29.4
quiet

title        Ubuntu 8.10, kernel 2.6.29.4 (recovery mode)
uuid        1e516149-7fbe-4bce-aa95-ff33283cc561
kernel        /boot/vmlinuz-2.6.29.4 root=UUID=1e516149-7fbe-4bce-aa95-ff33283cc561 ro  single
initrd        /boot/initrd.img-2.6.29.4

title        Ubuntu 8.10, memtest86+
uuid        1e516149-7fbe-4bce-aa95-ff33283cc561
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title        Ubuntu, Linux 2.6.31-16-generic (on /dev/hda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=b4020aef-7880-4f1b-94a1-c58d5a09e481 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title        Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/hda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=b4020aef-7880-4f1b-94a1-c58d5a09e481 ro single 
initrd        /boot/initrd.img-2.6.31-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title        Ubuntu, Linux 2.6.31-14-generic (on /dev/hda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=b4020aef-7880-4f1b-94a1-c58d5a09e481 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title        Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/hda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=b4020aef-7880-4f1b-94a1-c58d5a09e481 ro single 
initrd        /boot/initrd.img-2.6.31-14-generic
savedefault
boot


=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda9
UUID=1e516149-7fbe-4bce-aa95-ff33283cc561 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda7
UUID=553556d7-52f8-40ae-a3e3-069cb544990b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


  94.0GB: boot/grub/menu.lst
  94.0GB: boot/grub/stage2
  94.0GB: boot/initrd.img-2.6.29.4
  94.0GB: boot/vmlinuz-2.6.29.4
  94.0GB: initrd.img
  94.0GB: initrd.img.old
  94.0GB: vmlinuz

```
what to do now ??

---

### Post by audiomick on 2009-12-28
Hi.
It looks like everything is there. I think you just need to update the menu.lst associated with the backtrack install.

Have a look here
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by meierfra. on 2009-12-28
Everything on RESULTS.txt looks correct, including the menu.lst item for Ubuntu.
My guess is that the backtrack grub probably cannot handle the ext4 filesystem used by Ubuntu.(edit:  backtrack 4 is Ubuntu based  and should really be able to handle the ext4 filesystem. So I' don't know what is causing your problem. Anyway: )  I suggest to use the Ubuntu Grub 2, rather than the  back track grub.  So follow the advice from post 3, namely boot from the ubuntu live cd and

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot. You should now be able to boot into Ubuntu, but not backtrack. To add backtrack to your Ubuntu Grub, run:

```
sudo update-grub
```

---

### Post by saadlulu on 2009-12-28
> **meierfra. said:**
> Everything on RESULTS.txt looks correct, including the menu.lst item for Ubuntu.
My guess is that the backtrack grub probably cannot handle the ext4 filesystem used by Ubuntu.(edit:  backtrack 4 is Ubuntu based  and should really be able to handle the ext4 filesystem. So I' don't know what is causing your problem. Anyway: )  I suggest to use the Ubuntu Grub 2, rather than the  back track grub.  So follow the advice from post 3, namely boot from the ubuntu live cd and

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Reboot. You should now be able to boot into Ubuntu, but not backtrack. To add backtrack to your Ubuntu Grub, run:

```
sudo update-grub
```

worked like a charm.
thanks meierfra, thanks all :D
finally got my system back :) baaaad backtrack :P

---


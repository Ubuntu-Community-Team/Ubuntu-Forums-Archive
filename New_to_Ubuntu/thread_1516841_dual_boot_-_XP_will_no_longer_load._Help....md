---
title: "dual boot - XP will no longer load. Help..."
date: 2010-06-24
forum: New to Ubuntu
---

### Post by Windoze Refugee on 2010-06-24
HI Folks
Ive been Ubuntu-ing for a few months now and very happy with it (although in all honesty, I think Karmic Koala was more stable than Lucid Lynx) anyhoo.

My original install was alongside XP and gave me the choice at the grub screen.
Recently I tried to get into Xp for some stuff and found it woudnt load (flashing cursor and not much else)
I tried to boot from the XP install disk and got as far as the Recovery Console where I blithely invoked the fixmbr command. Assuming all was well I rebooted only to find that not only had this overwritten the Grub loader, it had also failed to write a new (or at least, working) MBR for windows either.
After much scouring I discovered the Ubunt grub loader CD recovery doodah and got it to install a new grub loader. 
I can now get into Ubuntu again, but im still having the same probs with trying to load XP (i.e it wont)
Naturally im not keen to go around again by "fixing the mbr" in windows thereby locking myself out again completely, but Id quite like to be able to get into XP now and again.

Any ideas?

Cheers

Jonathan

---

### Post by john newbuntu on 2010-06-24
From that recovery console of XP, if only you had run "fixboot", that would have fixed all your problems. Do not run fixmbr again.
Once this is done, boot back into Ubuntu and from a terminal run: "sudo update-grub" without quotes.  Hopefully that will take care of most of your issues.

---

### Post by arrange on 2010-06-24
Could you give us the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/")? (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)

---

### Post by Windoze Refugee on 2010-06-24
Hi Guys and thanks for your input.
John, I may well go with the fixboot command but just in case Id first like to know what kind of mess Ive created and what I can do about it.

Arrange, Ive installed and run the boot_info doodah and the script is below. I hope it means something to you cos it means next to nothing to me

Cheers
Jonathan

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=19deafb9-7707-4616-8c88-2f112de849b8)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 698511838 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 698513926 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 698515550 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   268,414,019   268,413,957  82 Linux swap / Solaris
/dev/sdb2         268,414,020   558,965,609   290,551,590   7 HPFS/NTFS
/dev/sdb3         558,965,610   976,768,064   417,802,455   5 Extended
/dev/sdb5         698,233,158   965,377,979   267,144,822  83 Linux
/dev/sdb6         965,378,043   976,768,064    11,390,022  82 Linux swap / Solaris
/dev/sdb7         558,965,736   692,465,759   133,500,024  83 Linux
/dev/sdb8         692,465,823   698,233,094     5,767,272  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        16407A8E407A73F9                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        16407A8E407A73F9                       ntfs                                     
/dev/sdb2        8624044024043629                       ntfs       New Volume                    
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        f67be2f8-9ced-42bc-97f5-ce12f58cc34d   ext4                                     
/dev/sdb6        c399f342-edba-4efa-8cff-446814bfda94   swap                                     
/dev/sdb7        19deafb9-7707-4616-8c88-2f112de849b8   ext4                                     
/dev/sdb8        678712b9-9628-47e7-a222-3b188685342c   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/16407A8E407A73F9  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/16407A8E407A73F9_ fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb7        /media/19deafb9-7707-4616-8c88-2f112de849b8 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 
C:\wubildr.mbr = "Ubuntu" 

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set f67be2f8-9ced-42bc-97f5-ce12f58cc34d
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
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set f67be2f8-9ced-42bc-97f5-ce12f58cc34d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set f67be2f8-9ced-42bc-97f5-ce12f58cc34d
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=f67be2f8-9ced-42bc-97f5-ce12f58cc34d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set f67be2f8-9ced-42bc-97f5-ce12f58cc34d
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=f67be2f8-9ced-42bc-97f5-ce12f58cc34d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set f67be2f8-9ced-42bc-97f5-ce12f58cc34d
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=f67be2f8-9ced-42bc-97f5-ce12f58cc34d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set f67be2f8-9ced-42bc-97f5-ce12f58cc34d
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=f67be2f8-9ced-42bc-97f5-ce12f58cc34d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set f67be2f8-9ced-42bc-97f5-ce12f58cc34d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set f67be2f8-9ced-42bc-97f5-ce12f58cc34d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 16407a8e407a73f9
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 16407a8e407a73f9
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=f67be2f8-9ced-42bc-97f5-ce12f58cc34d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c399f342-edba-4efa-8cff-446814bfda94 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 357.6GB: boot/grub/core.img
 363.5GB: boot/grub/grub.cfg
 379.0GB: boot/initrd.img-2.6.31-21-generic
 382.5GB: boot/initrd.img-2.6.32-22-generic
 358.3GB: boot/vmlinuz-2.6.31-21-generic
 359.7GB: boot/vmlinuz-2.6.32-22-generic
 382.5GB: initrd.img
 379.0GB: initrd.img.old
 359.7GB: vmlinuz
 358.3GB: vmlinuz.old

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
set root=(hd1,7)
search --no-floppy --fs-uuid --set 19deafb9-7707-4616-8c88-2f112de849b8
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
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 19deafb9-7707-4616-8c88-2f112de849b8
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=19deafb9-7707-4616-8c88-2f112de849b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 19deafb9-7707-4616-8c88-2f112de849b8
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=19deafb9-7707-4616-8c88-2f112de849b8 ro single 
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
    search --no-floppy --fs-uuid --set 16407a8e407a73f9
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 16407a8e407a73f9
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set f67be2f8-9ced-42bc-97f5-ce12f58cc34d
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=f67be2f8-9ced-42bc-97f5-ce12f58cc34d ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set f67be2f8-9ced-42bc-97f5-ce12f58cc34d
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=f67be2f8-9ced-42bc-97f5-ce12f58cc34d ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set f67be2f8-9ced-42bc-97f5-ce12f58cc34d
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=f67be2f8-9ced-42bc-97f5-ce12f58cc34d ro quiet splash
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set f67be2f8-9ced-42bc-97f5-ce12f58cc34d
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=f67be2f8-9ced-42bc-97f5-ce12f58cc34d ro single
    initrd /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=19deafb9-7707-4616-8c88-2f112de849b8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=678712b9-9628-47e7-a222-3b188685342c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb7: Location of files loaded by Grub: ===================


 289.4GB: boot/grub/core.img
 289.4GB: boot/grub/grub.cfg
 286.7GB: boot/initrd.img-2.6.31-14-generic
 286.7GB: boot/vmlinuz-2.6.31-14-generic
 286.7GB: initrd.img
 286.7GB: vmlinuz

---

### Post by arrange on 2010-06-24
I think Mr Newbuntu is right... You should *fixboot* (not *fixmbr*), because you've installed Grub into all the Win boot sectors.

---

### Post by Windoze Refugee on 2010-06-24
Hi Arrange. 
Thanks for your reply. 
OK so boot from xp install disk, run recovery console and select fixboot. 
if Im offered options, which boot should I choose to fix or will it auto select the right one?
Cheers
Jonathan

---

### Post by arrange on 2010-06-24
I don't really know, don't understand Windows very much. From your setup it looks like you have 2 Windows installations on the first partitions of both disks.

---

### Post by jtarin on 2010-06-24
It will automatically repair your windows MBR. Upon intializing the recovery console it will ask you which installation of win you want to repair.If you only have one its a simple choice.It will always be the one on the first drive, first partition.
I have found in the past that oftentimes this will not repair the MBR when GRUB is installed, if that is the case here post back and I'll tell you an alternate method that works for sure.

---

### Post by oldfred on 2010-06-24
From Ubuntu you can run this to fix it also, you need to run it for both sda1 and sda2:

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by snip3r8 on 2010-06-24
> **Windoze Refugee said:**
>  (flashing cursor and not much else)

mabe xp broke itself (typical of microsoft) .In this case reinstall,dont be hasty though ,make sure its broken.

---

### Post by wilee-nilee on 2010-06-24
> **oldfred said:**
> From Ubuntu you can run this to fix it also, you need to run it for both sda1 and sda2:

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

This is the correct answer before resorting to fix boot.

---

### Post by wilee-nilee on 2010-06-24
> **snip3r8 said:**
> mabe xp broke itself (typical of microsoft) .In this case reinstall,dont be hasty though ,make sure its broken.

:lolflag::confused:

---

### Post by john newbuntu on 2010-06-24
> **Windoze Refugee said:**
> 
OK so boot from xp install disk, run recovery console and select fixboot. 
if Im offered options, which boot should I choose to fix or will it auto select the right one?
Cheers
Jonathan
Typically, the recovery console presents you with all your Windows instllations.  You need to run fixboot on both of yours.  So choose the first one, run fixboot, follow the same with the second one.  Essentially, what you are doing is fixing the boot sector of the instance you are logging into.
I want to let you know that oldfred's suggestion will also work.

---


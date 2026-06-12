---
title: "UUID, disk cloning, &amp; GRUB2"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by Singlebbl on 2011-02-05
I have cloned my primary drive using dd and started to follow the instructions in [http://ubuntuforums.org/showthread.php?t=678629](http://ubuntuforums.org/showthread.php?t=678629) to update the UUID's so I can boot from the secondary drive.  I created a new UUID and updated FSTAB OK.  But this tutorial does not provide the information on how to handle doing the modifications to update the UUID's in grub.cfg that is used in GRUB2.  

I read [https://help.ubuntu.com/community/Grub2#/boot/grub/grub.cfg](https://help.ubuntu.com/community/Grub2#/boot/grub/grub.cfg) but it is not clear to me how to run update -grub so the instance of grub.cfg on the secondary drive is properly updated for the new UUID's in the partitions on that drive.  

Can someone provide that information for me?  

Pls & Thx, 
SingleBbl

---

### Post by oldfred on 2011-02-05
Your link is old enough that it was grub legacy. You need grub2 unless your existing install was an upgrade and you kept grub2.

Have you tried a sudo update grub in your current install to add the new drive? If UUIDs are different I would think it would let you boot it already.

To see exactly where you are, if you have changed UUIDs then you should be able to have both drives connected without problems:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

You probably just have to reinstall grub. If you are booting your old drive, you follow the same procedure as a liveCD but do not need to use liveCD. If you can boot into the new drive just install grub from it to the new drive.

Mount partition with install you want to boot if not in new system -change to your partition:
#confirm that linux is sdb5
sudo mount /dev/sdb5 /mnt

(if in system you do not do the mount command like in a liveCD or other running install, since it knows to install grub from where it is)
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc


How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by Singlebbl on 2011-02-05
Per request ...

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    37,380,095    37,378,048  83 Linux
/dev/sda2          37,382,142    39,100,415     1,718,274   5 Extended
/dev/sda5          37,382,144    39,100,415     1,718,272  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    37,380,095    37,378,048  83 Linux
/dev/sdb2          37,382,142    39,100,415     1,718,274   5 Extended
/dev/sdb5          37,383,255    39,086,144     1,702,890  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0203ece9-0c5c-456d-99ee-36e187918f8a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d5aeb159-6950-41a3-b1e0-40847c6c23ef   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8e31a181-31fc-483f-a03d-0e3ac0e18ef9   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        3c80c5d7-08ef-45ec-a19b-2949a72aadd6   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/8e31a181-31fc-483f-a03d-0e3ac0e18ef9 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0203ece9-0c5c-456d-99ee-36e187918f8a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d5aeb159-6950-41a3-b1e0-40847c6c23ef none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/core.img
   2.7GB: boot/grub/grub.cfg
   2.6GB: boot/initrd.img-2.6.32-21-generic
   2.9GB: boot/initrd.img-2.6.32-23-generic
   3.4GB: boot/initrd.img-2.6.32-24-generic
   3.4GB: boot/initrd.img-2.6.32-27-generic
   2.4GB: boot/vmlinuz-2.6.32-21-generic
   2.8GB: boot/vmlinuz-2.6.32-23-generic
   3.4GB: boot/vmlinuz-2.6.32-24-generic
   3.4GB: boot/vmlinuz-2.6.32-27-generic
   3.4GB: initrd.img
   3.4GB: initrd.img.old
   3.4GB: vmlinuz
   3.4GB: vmlinuz.old

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0203ece9-0c5c-456d-99ee-36e187918f8a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0203ece9-0c5c-456d-99ee-36e187918f8a
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=8e31a181-31fc-483f-a03d-0e3ac0e18ef9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=3c80c5d7-08ef-45ec-a19b-2949a72aadd6 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/core.img
   2.7GB: boot/grub/grub.cfg
   2.6GB: boot/initrd.img-2.6.32-21-generic
   2.9GB: boot/initrd.img-2.6.32-23-generic
   3.4GB: boot/initrd.img-2.6.32-24-generic
   3.4GB: boot/initrd.img-2.6.32-27-generic
   2.4GB: boot/vmlinuz-2.6.32-21-generic
   2.8GB: boot/vmlinuz-2.6.32-23-generic
   3.4GB: boot/vmlinuz-2.6.32-24-generic
   3.4GB: boot/vmlinuz-2.6.32-27-generic
   3.4GB: initrd.img
   3.4GB: initrd.img.old
   3.4GB: vmlinuz
   3.4GB: vmlinuz.old

```

---

### Post by oldfred on 2011-02-05
Either grub2 or the script do not correctly identify boot drive, so same drive is not always same drive. Since everything else is the same, I cannot tell much. I can see UUIDs are updated.

Have you run this?
```
sudo update-grub
```

Your grub.cfg in sdb is still identical to sda, so if you can get the update grub to see your sdb install, boot into it, reinstall grub to sdb and run this from sdb install.
```
sudo update-grub
```

See full instructions in previous post.

---

### Post by Singlebbl on 2011-02-13
[SIZE=3]> **oldfred said:**
> Have you run this?
```
sudo update-grub
```Your grub.cfg in sdb is still identical to sda, so if you can get the update grub to see your sdb install, boot into it, reinstall grub to sdb and run this from sdb install.

After I ran update-grub, grub-cfg included a bunch of entires for the various kernals on /dev/sdb1 and they showed up in the menu at boot time.  However, they all have the UUID of /dev/sda1 so when you select one to load, it uses the file system on /dev/sda1, not the one on /dev/sdb1.  So it winds up running in some kind of mixed mode (I did not leave it up long for fear of screwing up something).  

I'm a little surprised that 30_os-prober did not pick up the correct UUID's for the kernals on /dev/sdb1.  Does anyone know if this is WAD?  

So then, like the instructions say, I copied one of the /dev/sdb1 entries from grub-cfg into 40_custom, changed the UUID there to match /dev/sdb1, and re-ran grub-update.  Now that entry shows up in grub-cfg and in the menu you get at boot time.  When you select it, it appears that you have actually loaded from /dev/sdb1.  

I'll have to do some more testing, but for right now it looks OK.  I won't feel confident that it's a done deal until I can run the upgrade to 10.10 and use it for a while.  Now that I have a good idea of what needs to be done, I'm going to start from scratch with a fresh clone and take notes as I go along.  I'll post back here on how it goes.  
[/SIZE]

---

### Post by oldfred on 2011-02-13
Did you check fstab also. It uses UUID entries and has to be updated.

I am surprised that a grub update did not find correct UUIDs.

Grub also has an entry on which drive to install into by hard drive ID.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---


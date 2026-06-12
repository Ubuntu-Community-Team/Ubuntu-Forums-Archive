---
title: "Extending unallocated space in existing installation"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by blues2use on 2010-08-23
I removed my XP partition and updated grub and the system boots fine. I have since tried to extend my ubuntu partition to have it use the unallocated space with the Gparted Live CD. I am unable to do that though and, from what I have read, it is because that space is to the left of my ubuntu partition rather than to the right.

Can someone explain to me how to add that unallocated space to my existing partition? A screenshot of gparted is attached.

Thanks for the help

---

### Post by Elfy on 2010-08-23
Boot the livecd - go to gparted. Right click swap (sda6) turn off swap.

Expand sda2, then the unallocated space will be inside the extended.

You can now try expanding sda5 - it may be that sda5 needs moving to the left hand side of sda2 beforehand.

Once done right click sda6 turn on swap.

---

### Post by blues2use on 2010-08-23
> **forestpiskie said:**
> Boot the livecd - go to gparted. Right click swap (sda6) turn off swap.

Expand sda2, then the unallocated space will be inside the extended.

You can now try expanding sda5 - it may be that sda5 needs moving to the left hand side of sda2 beforehand.

Once done right click sda6 turn on swap.

I followed the steps and it looks like about 55 minutes or so to complete the growing operation. I'll turn swap on and reboot and let you know what happened.

Thanks for the help. I sincerely appreciate it...

---

### Post by Elfy on 2010-08-23
Yep - it can take a while - and it can also look like it has hung too - don't be fooled by that ;) 

Welcome of course :)

---

### Post by Elfy on 2010-08-23
> **nu2u904 said:**
> I believe my situation falls in the same class to continue this thread.

Not really, moving /home is a different beast. 

I will move your post to it's own thread in ABT.

Here - [http://ubuntuforums.org/showthread.php?t=1559480](http://ubuntuforums.org/showthread.php?t=1559480)

---

### Post by blues2use on 2010-08-23
> **forestpiskie said:**
> Yep - it can take a while - and it can also look like it has hung too - don't be fooled by that ;) 

Welcome of course :)

Okay, steps completed but now I'm stuck at a flashing cursor in the upper left corner...I'm researching that at the moment on my other laptop...I must have missed something somewhere...

Thanks for the help

---

### Post by lavinog on 2010-08-23
I believe that you need at least one primary partition to be set as the boot partition.

Also for future reference, sometimes it is easier to just make a new partition, and use it as extra storage.  I have a storage partition that I use for videos, pictures, and other large files.  This makes disk checks quicker since the storage partition can be checked after the computer boots.

---

### Post by blues2use on 2010-08-23
> **lavinog said:**
> I believe that you need at least one primary partition to be set as the boot partition.

Also for future reference, sometimes it is easier to just make a new partition, and use it as extra storage.  I have a storage partition that I use for videos, pictures, and other large files.  This makes disk checks quicker since the storage partition can be checked after the computer boots.

Here's a screenshot of my new partitioning from gparted...does this look right? I thought I would end up with one large partition of around 290+GB...I don't really want another partition for /home or storage or backup or whatever...

I'm still stuck at the flashing cursor...no boot menu...no disk activity...I have no idea what to do at this point...

**I can boot to my ubuntu installation using a SuperGrub CD**...

**_Help would be very much appreciated._**

GParted screenshot attached...

Thanks

---

### Post by Elfy on 2010-08-24
Try reinstalling grub from the livecd - [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If that doesn't help - boot with supergrub and do this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by blues2use on 2010-08-24
> **forestpiskie said:**
> Try reinstalling grub from the livecd - [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If that doesn't help - boot with supergrub and do this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Tried reinstalling grub...rebooted...that got me to an invalid partition  grub rescue prompt...

Here's the info from the boot info script:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
    partition #5 for /boot/grub.

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2                   1   312,580,095   312,580,095   5 Extended
/dev/sda5    *             63   306,905,759   306,905,697  83 Linux
/dev/sda6         306,909,184   312,580,095     5,670,912  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2: PTTYPE="dos"
/dev/sda5        b6518d28-c33b-4ef5-96ce-53bac062dd51   ext4                                     
/dev/sda6        a027dcb9-83ba-4255-a1bf-a7fc4ad5032d   swap                                     
/dev/sda: PTTYPE="dos"

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b6518d28-c33b-4ef5-96ce-53bac062dd51 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b6518d28-c33b-4ef5-96ce-53bac062dd51 ro single
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=b6518d28-c33b-4ef5-96ce-53bac062dd51 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=b6518d28-c33b-4ef5-96ce-53bac062dd51 ro single
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b6518d28-c33b-4ef5-96ce-53bac062dd51 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a027dcb9-83ba-4255-a1bf-a7fc4ad5032d none            swap    sw              0       0

#XP desktop mount follows
#UUID=F4A0E05AA0E02538 /media/xpc ntfs-3g defaults 0 0

#WD Mybook follows
//DELL6000/My\040Book\040(F) /media/mybook cifs _netdev,auto,credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

=================== sda5: Location of files loaded by Grub: ===================


  47.3GB: boot/grub/grub.cfg
  47.5GB: boot/initrd.img-2.6.32-23-generic
  47.5GB: boot/initrd.img-2.6.32-24-generic
  47.5GB: boot/vmlinuz-2.6.32-23-generic
  47.5GB: boot/vmlinuz-2.6.32-24-generic
  47.5GB: initrd.img
  47.5GB: initrd.img.old
  47.5GB: vmlinuz
  47.5GB: vmlinuz.old
```

Once I get this all figured out, I'm going to do the same thing with my other dual boot system...this is definitely a good learning experience. I can always reinstall ubuntu but that teaches me nothing. I'd much rather learn how to troubleshoot and fix these kinds of problems...

GParted screenshot attached...

**_Thanks for the help_**

---

### Post by blues2use on 2010-08-24
> **blues2use said:**
> Tried reinstalling grub...rebooted...that got me to an invalid partition  grub rescue prompt...

Here's the info from the boot info script:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
    partition #5 for /boot/grub.

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2                   1   312,580,095   312,580,095   5 Extended
/dev/sda5    *             63   306,905,759   306,905,697  83 Linux
/dev/sda6         306,909,184   312,580,095     5,670,912  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2: PTTYPE="dos"
/dev/sda5        b6518d28-c33b-4ef5-96ce-53bac062dd51   ext4                                     
/dev/sda6        a027dcb9-83ba-4255-a1bf-a7fc4ad5032d   swap                                     
/dev/sda: PTTYPE="dos"

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b6518d28-c33b-4ef5-96ce-53bac062dd51 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b6518d28-c33b-4ef5-96ce-53bac062dd51 ro single
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=b6518d28-c33b-4ef5-96ce-53bac062dd51 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=b6518d28-c33b-4ef5-96ce-53bac062dd51 ro single
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b6518d28-c33b-4ef5-96ce-53bac062dd51
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b6518d28-c33b-4ef5-96ce-53bac062dd51 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a027dcb9-83ba-4255-a1bf-a7fc4ad5032d none            swap    sw              0       0

#XP desktop mount follows
#UUID=F4A0E05AA0E02538 /media/xpc ntfs-3g defaults 0 0

#WD Mybook follows
//DELL6000/My\040Book\040(F) /media/mybook cifs _netdev,auto,credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

=================== sda5: Location of files loaded by Grub: ===================


  47.3GB: boot/grub/grub.cfg
  47.5GB: boot/initrd.img-2.6.32-23-generic
  47.5GB: boot/initrd.img-2.6.32-24-generic
  47.5GB: boot/vmlinuz-2.6.32-23-generic
  47.5GB: boot/vmlinuz-2.6.32-24-generic
  47.5GB: initrd.img
  47.5GB: initrd.img.old
  47.5GB: vmlinuz
  47.5GB: vmlinuz.old
```

Once I get this all figured out, I'm going to do the same thing with my other dual boot system...this is definitely a good learning experience. I can always reinstall ubuntu but that teaches me nothing. I'd much rather learn how to troubleshoot and fix these kinds of problems...

GParted screenshot attached...

**_Thanks for the help_**

Well, I tried to boot with SuperGrub CD and there is _no OS detected_, _no grub.cfg detected_, _no core.img files detected_ and the only _devices/partitions detected are for the CD with fd0 and fd1 listed as unknown_. It looks like a reinstall is (in this scenario) going to be required. That's fine as I had very little installed in ubuntu. 

I'll hold off for another hour or so pending any other suggestions before I start the new installation.

**_Thanks for the help_**

---

### Post by blues2use on 2010-08-24
> **blues2use said:**
> Well, I tried to boot with SuperGrub CD and there is _no OS detected_, _no grub.cfg detected_, _no core.img files detected_ and the only _devices/partitions detected are for the CD with fd0 and fd1 listed as unknown_. It looks like a reinstall is (in this scenario) going to be required. That's fine as I had very little installed in ubuntu. 

I'll hold off for another hour or so pending any other suggestions before I start the new installation.

**_Thanks for the help_**

Once again, thanks for all of the help. I am going to reinstall ubuntu and put XP in Vbox. I had hoped to resolve this issue just for the learning experience as I have another laptop that I would like to remove the XP partition from, extend the ubuntu partition and reinstall XP in Vbox.

This forum is a wonderful resource and I search it on a regular basis. I sincerely appreciate those who take the time to respond to new user requests for help.

**_Thanks again for the help_** =D>

---


---
title: "Tried to install as dual boot with xp but got error: no such device"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by PeeJay16 on 2011-02-19
I'm a Ubuntu newbie and I'm trying to install 10.10 in a dual boot configuration with XP.

The system has two HDs, a 200GB internal (sda in the results.txt file) and a 500GB external (sdb) plugged into a USB port 

I ran the install specifying the installation as dual boot with Linux on sdb giving it about 20GB. It all seemed to go OK (no error messages) however when I tried to re-boot instead of offering the dual boot menu it seemed to try and go straight into Linux and I received

error: no such device: 070dc7e9-b033-4cdb-8ca8-5e25a3aaae1a

grub rescue >

I've got windows back up using the XP install CD to repair the MBR and run the boot info script (enclosed below). sda1 is a hidden XP factory install/recovery partition and sda2 is the windows xp install partition as well as code etc. I can see Linux files and directories on sdb but don't know what, if anything, I can do to repair the installation.

 Can anyone tell me what I need to do to get a working Linux dual boot system in place?

Thanks

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/mapper/pdc_bibcdjigbe

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_bibcdjigbe1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

pdc_bibcdjigbe2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /menu.lst /boot.ini /grldr /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     9,221,309     9,221,247  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *      9,221,310   398,283,479   389,062,170   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   936,637,421   936,637,359   7 HPFS/NTFS
/dev/sdb2         936,638,462   976,771,071    40,132,610   5 Extended
/dev/sdb5         936,638,464   975,007,743    38,369,280  83 Linux
/dev/sdb6         975,009,792   976,771,071     1,761,280  82 Linux swap / Solaris


Drive: pdc_bibcdjigbe ___________________ _____________________________________________________

Disk /dev/mapper/pdc_bibcdjigbe: 203.9 GB, 203928043520 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398296960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_bibcdjigbe1                 63     9,221,309     9,221,247  1c Hidden W95 FAT32 (LBA)
/dev/mapper/pdc_bibcdjigbe2   *      9,221,310   398,283,479   389,062,170   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_bibcdjigbe1 A82A-F795                              vfat       RECOVERY                      
/dev/mapper/pdc_bibcdjigbe2 01CBB1D56F9383C0                       ntfs       Windows                       
/dev/mapper/pdc_bibcdjigbe: PTTYPE="dos" 
/dev/sda1        A82A-F795                              vfat       RECOVERY                      
/dev/sda2        01CBB1D56F9383C0                       ntfs       Windows                       
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        000226FC000F884F                       ntfs       500GB                         
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        070dc7e9-b033-4cdb-8ca8-5e25a3aaae1a   ext4                                     
/dev/sdb6        a7bd2e88-e82c-455c-a50f-2625b7b08c8f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/500GB             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/070dc7e9-b033-4cdb-8ca8-5e25a3aaae1a ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 070dc7e9-b033-4cdb-8ca8-5e25a3aaae1a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 070dc7e9-b033-4cdb-8ca8-5e25a3aaae1a
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 070dc7e9-b033-4cdb-8ca8-5e25a3aaae1a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=070dc7e9-b033-4cdb-8ca8-5e25a3aaae1a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 070dc7e9-b033-4cdb-8ca8-5e25a3aaae1a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=070dc7e9-b033-4cdb-8ca8-5e25a3aaae1a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 070dc7e9-b033-4cdb-8ca8-5e25a3aaae1a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 070dc7e9-b033-4cdb-8ca8-5e25a3aaae1a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=070dc7e9-b033-4cdb-8ca8-5e25a3aaae1a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=a7bd2e88-e82c-455c-a50f-2625b7b08c8f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 484.3GB: boot/grub/core.img
 484.3GB: boot/grub/grub.cfg
 493.2GB: boot/initrd.img-2.6.35-22-generic
 484.3GB: boot/vmlinuz-2.6.35-22-generic
 493.2GB: initrd.img
 484.3GB: vmlinuz

========================== pdc_bibcdjigbe1/boot.ini: ==========================

[boot loader] 
timeout=5 
default=c:\cmdcons\bootsect.dat 
[operating systems] 
c:\cmdcons\bootsect.dat="Microsoft XP Preinstall Environment" /cmdcons 

========================== pdc_bibcdjigbe2/menu.lst: ==========================

hiddenmenu  
timeout 0  
title openSUSE 11.3 installer (LOCAL)  
find --set-root /openSUSE_hitme.txt 
kernel /openSUSE/linux devfs=mount,dall ramdisk_size=65536  lang=en splash=silent vga=0x31A 
initrd /openSUSE/initrd 

========================== pdc_bibcdjigbe2/boot.ini: ==========================

[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

============== pdc_bibcdjigbe2: Location of files loaded by Grub: ==============


    ??GB: menu.lst

```

---

### Post by Sudo JC on 2011-02-19
Did you install Windows before Linux? This is mandatory haha. 

Looks like something went wrong when you configured the partitions. This is my guess :D

Install Windows again and then Linux :D

---

### Post by natex on 2011-02-19
Peejay,
You may want to read this [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by PeeJay16 on 2011-02-19
If I press F8 during BIOS load then the USB connected drive comes up as an option to use as the boot device, so I'm not sure it's an issue with booting from a USB connected drive.

---

### Post by PeeJay16 on 2011-02-21
Since the first post in this thread I have re-formatted both HDDs and reloaded Windows from scratch. I then attempted to reload Ubuntu however I'm getting exactly the same result, i.e. the install seems to go OK (no errors) but when I try and re-boot I simply get the error: no such device message followed by the grub rescue prompt. 

The system has an internal HD and an external (USB connected) HD. I'm attempting to install to the external HD. I've checked as far as I can that I can boot from this device - it appears in the boot list you get when you press F8 during Windows startup, and an internet search on my mobo indicated that you can boot from USB devices.

Out of interest I ran the boot info script post install but before I rebooted. The results of that are below

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   398,267,414   398,267,352   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   878,542,401   878,542,339   7 HPFS/NTFS
/dev/sdb2         878,542,846   976,771,071    98,228,226   5 Extended
/dev/sdb5         878,542,848   972,662,783    94,119,936  83 Linux
/dev/sdb6         972,664,832   976,771,071     4,106,240  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0090C84B90C8493C                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9898A55898A535A2                       ntfs       500GB                         
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        72185043-1a62-4eee-af14-cf758ebe7b97   ext4                                     
/dev/sdb6        bf14c801-57d4-4e50-b670-25f911f1c722   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 72185043-1a62-4eee-af14-cf758ebe7b97
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 72185043-1a62-4eee-af14-cf758ebe7b97
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 72185043-1a62-4eee-af14-cf758ebe7b97
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=72185043-1a62-4eee-af14-cf758ebe7b97 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 72185043-1a62-4eee-af14-cf758ebe7b97
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=72185043-1a62-4eee-af14-cf758ebe7b97 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 72185043-1a62-4eee-af14-cf758ebe7b97
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 72185043-1a62-4eee-af14-cf758ebe7b97
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0090c84b90c8493c
    drivemap -s (hd0) ${root}
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=72185043-1a62-4eee-af14-cf758ebe7b97 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=bf14c801-57d4-4e50-b670-25f911f1c722 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 471.4GB: boot/grub/core.img
 460.8GB: boot/grub/grub.cfg
 463.5GB: boot/initrd.img-2.6.35-22-generic
 471.4GB: boot/vmlinuz-2.6.35-22-generic
 463.5GB: initrd.img
 471.4GB: vmlinuz

```Then after I'd repaired the windows installation (using the XP install disc to sort out the MBR)  to get the system back up and running I ran it again 

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   398,267,414   398,267,352   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   878,542,401   878,542,339   7 HPFS/NTFS
/dev/sdb2         878,542,846   976,771,071    98,228,226   5 Extended
/dev/sdb5         878,542,848   972,662,783    94,119,936  83 Linux
/dev/sdb6         972,664,832   976,771,071     4,106,240  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0090C84B90C8493C                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9898A55898A535A2                       ntfs       500GB                         
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        72185043-1a62-4eee-af14-cf758ebe7b97   ext4                                     
/dev/sdb6        bf14c801-57d4-4e50-b670-25f911f1c722   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/500GB             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/72185043-1a62-4eee-af14-cf758ebe7b97 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 72185043-1a62-4eee-af14-cf758ebe7b97
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 72185043-1a62-4eee-af14-cf758ebe7b97
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 72185043-1a62-4eee-af14-cf758ebe7b97
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=72185043-1a62-4eee-af14-cf758ebe7b97 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 72185043-1a62-4eee-af14-cf758ebe7b97
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=72185043-1a62-4eee-af14-cf758ebe7b97 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 72185043-1a62-4eee-af14-cf758ebe7b97
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 72185043-1a62-4eee-af14-cf758ebe7b97
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0090c84b90c8493c
    drivemap -s (hd0) ${root}
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=72185043-1a62-4eee-af14-cf758ebe7b97 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=bf14c801-57d4-4e50-b670-25f911f1c722 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 471.4GB: boot/grub/core.img
 460.8GB: boot/grub/grub.cfg
 463.5GB: boot/initrd.img-2.6.35-22-generic
 471.4GB: boot/vmlinuz-2.6.35-22-generic
 463.5GB: initrd.img
 471.4GB: vmlinuz

```

Can anyone provide some advice on how I can go forward from here?

Thanks

---

### Post by oldfred on 2011-02-21
Boot script looks ok. Sometimes you do have to reinstall grub2 for some odd reason.

On my system, I cannot seem to boot USB devices, but it shows up as a hard drive and is bootable from that.

If you get to rescue promt have you tried manually booting?
The boot drive is hd0.

Manual boot:
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

Other ways to manually boot:
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by Oathanvil on 2011-02-21
I had the same error when I deleted the Ubuntu drive partition I created in Windows7, when I booted back up I had lost the dual boot screen option and ubuntu would boot to your error message.

I had no access anymore to my Windows7 install.

The SOLUTION I used was to boot to DOS on an old Windows 98 installation CD I still had and got to the command,

fdisk

when you are in fdisk you can view none DOS partitions and these will contain the ubuntu Grub loader that has hijacked your boot loader.

I deleted both of the small partitions found then exit DOS and reboot and Windows should again simply boot for you.

DO not remove the NTFS file or DOS partitions just the two none dos partitions that have the grub loader hidden on them.

I of course am still learning LINUX so I re created a new 200 gig partition in Windows7 and again installed Ubuntu ver 10.10 and still having fun learning stuff!

FYI I had to use a Windows 98 CD as my new case build has no floppy disc in it now I really miss that and might buy a SATA capable floppy! such a life line to people who play with all this type of stuff. The flight from Germany to ROME then back to Canada wiped and destroyed my USB drive on my Keyring to many airport scanners while you dump all your valuable's into the giant plastic bin and they nuke everything! Ya electronics guy 27 years I know its not supposed too do that but that usb key is deader then a door stop! wont even tickle a usb response out of 4 or 5 different computers I could be plugging in a goldfish!

---

### Post by PeeJay16 on 2011-02-22
Thanks Oldfred

An ls command only returns (hd0), (hd0,msdos1)  (hd1), (hd1,msdos1)  (fd0)

I'm guessing from this that grub rescue can't find the filesystem, which if I understand the boot info script correctly should be on (hd1,5)?

I ran a surface check of the disc only a few days OK, so I don't believe there are any physical problems with it. I'm wondering if there is some reason why I can't use it as a boot device, even though I can't find anything on the web to say my mobo doesn't support it.

I think at this point my next option (unless anyone can suggest another way forward) is to scrap the current install and attempt a dual boot install with both systems on the internal hard disk (i.e. Linux and Windows in separate partitions on the same HD)

Does anyone have any other suggestions before I try that?

Thanks

---

### Post by oldfred on 2011-02-22
If you are booting the sdb drive that will usually be hd0 - first boot drive in BIOS. When I boot sdc it is hd0 and if I chainload to the MBR in sda I have to use hd1. But if I boot sda it is hd0.

Did you try any of the manual booting with hd0,5 or lhd1,5?

---

### Post by PeeJay16 on 2011-02-23
After trying numerous suggestions from the thread I finally decided to scrap the current install and try again installing Ubuntu on my internal HD in a separate partition, and hey presto it works.  

Despite the information I found on the internet it seems I can't boot from an external HD (at least not with the BIOS version I have.)

Thanks very much to Oldfred and others for the advice and support I've been given to get this up and working. 

I'm off to play now........................  :)

---

### Post by oldfred on 2011-02-23
Well, whatever it takes to get it to work. Happy Ubuntu-ing.

---

### Post by PeeJay16 on 2011-02-23
Thanks. I'm still confused as to why I had this problem. If I unplug and re-plug the USB connected drive the BIOS automatically puts it as the first drive in the boot list, but apparently won't let me boot from it.

---


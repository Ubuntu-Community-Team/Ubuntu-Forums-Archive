---
title: "Help installing Ubuntu onto drive"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by Colopus on 2011-07-09
Hello all.

Im trying to create a dual boot with windows 7 and Ubuntu 11.04 on my pc.

I'm trying to get it so that windows stays on my hard disk and UBuntu is on my external harddisk which has 5 partitions.

When I install it, and restart my pc, I choose to boot from external, and all the comes up is 'grub>' command lines which have a Linux core, as in 'ls' works and 'tab' and 'help' don't.

I've tried using easybcd etc. And that doesnt work because 'partition not found'.

I've installed ubuntu onto 'dev/sdb6' which is ext3, mountpoint is / and bootloader Is set to dev/sdb. 

My aim is to have it so that I can have ubuntu on my hardisk, so I can use it on my laptop and my desktop, Which must be possible....

Any help would be great, as ive never used ubuntu before and the wiki makes it sound amazing!

---

### Post by ajgreeny on 2011-07-09
Please download and run the Boot-info-script from my signature, then copy back the RESULTS.txt file between (code)  (/code)  tags by clicking on the # in the text entry box toolbar.

---

### Post by jtarin on 2011-07-09
A little slow...Boot Info Script.

---

### Post by Colopus on 2011-07-09
That was harder than expected! It couldnt find the dekstop or the name so had to move it to the ubuntu folder and rename it....                 

 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,953,521,663 1,953,314,816   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   470,077,964   470,075,917   7 NTFS / exFAT / HPFS
/dev/sdb2         470,078,026   976,768,064   506,690,039   f W95 Extended (LBA)
/dev/sdb5         470,078,028   627,884,459   157,806,432   7 NTFS / exFAT / HPFS
/dev/sdb6    *    627,884,523   785,562,434   157,677,912   c W95 FAT32 (LBA)
/dev/sdb7         785,562,498   965,827,799   180,265,302   7 NTFS / exFAT / HPFS
/dev/sdb8         965,827,863   976,768,064    10,940,202  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0406A001069FF242                       ntfs       System Reserved
/dev/sda2        6236A32636A2FA65                       ntfs       
/dev/sdb1        01CC3C180A26FA30                       ntfs       Files
/dev/sdb5        01CC3C180EB227A0                       ntfs       MS Windows 7
/dev/sdb6        b227b053-648d-420c-acae-e96f5c6f8094   ext3       
/dev/sdb7        01CC3D8B481B02E0                       ntfs       Backups
/dev/sdb8                                               swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root b227b053-648d-420c-acae-e96f5c6f8094
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root b227b053-648d-420c-acae-e96f5c6f8094
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root b227b053-648d-420c-acae-e96f5c6f8094
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b227b053-648d-420c-acae-e96f5c6f8094 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root b227b053-648d-420c-acae-e96f5c6f8094
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b227b053-648d-420c-acae-e96f5c6f8094 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root b227b053-648d-420c-acae-e96f5c6f8094
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root b227b053-648d-420c-acae-e96f5c6f8094
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 0406A001069FF242
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
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=b227b053-648d-420c-acae-e96f5c6f8094 /               ext3    errors=remount-ro 0       1
/dev/sdb8       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 337.828469753 = 362.740557312  boot/grub/core.img                             1
 337.775712490 = 362.683909632  boot/grub/grub.cfg                             1
 337.801251888 = 362.711332352  boot/initrd.img-2.6.38-8-generic               5
 337.890389919 = 362.807043584  boot/vmlinuz-2.6.38-8-generic                  3
 337.801251888 = 362.711332352  initrd.img                                     5
 337.890389919 = 362.807043584  vmlinuz                                        3

=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by Colopus on 2011-07-09
Why does it say about windows XP when ive never had XP On here?!

Also, the MBR points to a dos, why doesnt it point to the partition with ubuntu on it?

Any help would be amazing, thanks!

---

### Post by oldfred on 2011-07-09
You have an inconsistency between format of partition sdb6 and tools that look at that and see ext3 and the partition table that says it is type c when it should be 83 or Linux.

> sdb6: ______________________________

File system: [COLOR=Red]ext3[/COLOR]
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 11.04
Boot files: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

/dev/sdb6 * 627,884,523 785,562,434 157,677,912 [COLOR=Red]c W95 FAT32 [/COLOR](LBA)

/dev/sdb6 b227b053-648d-420c-acae-e96f5c6f8094 [COLOR=Red]ext3 [/COLOR]


It looks like it may just be a bad entry in the partition table. Lets first back up partition table.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sdb > PT.txt

I am sure you can just edit PT.txt to change the c to 83 and read it back in and it should work. Maybe just using System, Utility, Disk Utility will let you can it to Linux (0x83).

This is a PT.txt from my windows drive, I have a ext3 backup linux partition on that drive, so you can see a correct style entry:
```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=115330572, Id= 7, bootable
/dev/sda2 : start=156296385, size=156280320, [COLOR=Red]Id=83[/COLOR]
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=115330635, size= 40965750, Id= b

```

---

### Post by Colopus on 2011-07-09
Thank you for replying :)

i did as you said using the disk utility, and ran the boot info script again top confirm it changed.

Here are the new results:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,953,521,663 1,953,314,816   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   470,077,964   470,075,917   7 NTFS / exFAT / HPFS
/dev/sdb2         470,078,026   976,768,064   506,690,039   f W95 Extended (LBA)
/dev/sdb5         470,078,028   627,884,459   157,806,432   7 NTFS / exFAT / HPFS
/dev/sdb6    *    627,884,523   785,562,434   157,677,912  83 Linux
/dev/sdb7         785,562,498   965,827,799   180,265,302   7 NTFS / exFAT / HPFS
/dev/sdb8         965,827,863   976,768,064    10,940,202  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0406A001069FF242                       ntfs       System Reserved
/dev/sda2        6236A32636A2FA65                       ntfs       
/dev/sdb1        01CC3C180A26FA30                       ntfs       Files
/dev/sdb5        01CC3C180EB227A0                       ntfs       MS Windows 7
/dev/sdb6        b227b053-648d-420c-acae-e96f5c6f8094   ext3       
/dev/sdb7        01CC3D8B481B02E0                       ntfs       Backups
/dev/sdb8                                               swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root b227b053-648d-420c-acae-e96f5c6f8094
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root b227b053-648d-420c-acae-e96f5c6f8094
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root b227b053-648d-420c-acae-e96f5c6f8094
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b227b053-648d-420c-acae-e96f5c6f8094 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root b227b053-648d-420c-acae-e96f5c6f8094
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b227b053-648d-420c-acae-e96f5c6f8094 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root b227b053-648d-420c-acae-e96f5c6f8094
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root b227b053-648d-420c-acae-e96f5c6f8094
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 0406A001069FF242
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
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=b227b053-648d-420c-acae-e96f5c6f8094 /               ext3    errors=remount-ro 0       1
/dev/sdb8       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 337.828469753 = 362.740557312  boot/grub/core.img                             1
 337.775712490 = 362.683909632  boot/grub/grub.cfg                             1
 337.801251888 = 362.711332352  boot/initrd.img-2.6.38-8-generic               5
 337.890389919 = 362.807043584  boot/vmlinuz-2.6.38-8-generic                  3
 337.801251888 = 362.711332352  initrd.img                                     5
 337.890389919 = 362.807043584  vmlinuz                                        3

=============================== StdErr Messages: ===============================

unlzma: Decoder error


But when i try and boot, i still get:

error: no such partition.
grub rescue>



Do you have any other ideas?

Im very thankful for your help :)

---

### Post by oldfred on 2011-07-09
Your swap does not have an UUID, but that is not a major problem as far as I know. It is mounting by dev/sda8, but UUID is the preferred way.

Can you manually boot. Sometimes you can and then reinstall grub2 from the system you have booted:

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

See links above but two ways , grub usually sees BIOS boot drive as hd0 even if it is sdb:
Manual boot:
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,6), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

Adjust drive, partition to your install may be hd1,6 or hd0,6 but dev should still be /dev/sdb6 in both cases, one is grub's view and the other Ubuntu's:
sh:grub>ls
#If on (hd1,6) or sdb6
sh:grub>ls (hd1,6)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,6)/vmlinuz root=/dev/sdb6
sh:grub>initrd (hd1,6)/initrd.img
sh:grub>boot

---

### Post by Colopus on 2011-07-11
on my ls, i get the following:

(hd0) (hd0,msdos1) (hd1) (hd1,msdos2) (hd1,msdos1)

When i disconnect the internal harddrive, i get:

(hd0) (hd0,msdos1)

and when i try and do ANY commands on these i get an invalid response such as 'error: no such partition'.

Thanks for all your help, it is much appreciated

---

### Post by oldfred on 2011-07-12
It is not seeing partition sdb6. Is this an older system with the BIOS boot limit of 137GB or perhaps you have a setting in BIOS that makes it think it is an older system with the boot limit. Some have solved it by creating a boot partition at the beginning of the drive. Some with newer systems have been able to change BIOS settings and get it to work.

These are all comments from others who have made one or more of these corrections and then it works.

Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
Old gpt data on drive
BIOS setting, Keyboard response in grub really slow

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

---

### Post by Colopus on 2011-07-12
Hello.

I will try putting it on SDB1 tonight and try, thanks, i really should have tried that anyway to be honest!

I experimented lots with trial and error last night by putting the bootloader in different places etc. and using easyBCD's boot, but to no avail.

I put the PC together in February, trying to get the best bits at the best value, like AMD phenom II, samsung harddrive, Intel chipsets, ATI radeon HD 1GB graphics cards trying to get it so that i wouldnt have to update for a few years and avoid things like this!

Im now debating whether to just put the OS onto the internal hdd and put any files on the external HDD and remote between all the computers... But i hate giving up on something!

Cheers

---

### Post by oldfred on 2011-07-12
I like having an operating system on every drive, with all the parts it need to boot on that drive. Then link in data from anywhere else from other drives. If other drives do not mount for some reason you get an error but can boot.

I then like to have a smaller operating system partition of 20-25GB. If you have a BIOS setting that is causing it not to see a boot beyond 137GB then just make a / (root) partition that is fully inside the first 137GB and /home or /data in the rest of the drive.

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---


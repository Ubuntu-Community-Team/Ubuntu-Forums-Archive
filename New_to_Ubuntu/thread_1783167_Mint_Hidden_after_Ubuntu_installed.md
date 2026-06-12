---
title: "Mint Hidden after Ubuntu installed"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by JohnBonne on 2011-06-15
I had Windows and Mint installed in a dual boot using Mint's installer. It was a dual install with Windows in the front of the partition. I installed Ubuntu in Windows place and now Ubuntu cannot find Mint. 

I would like to find Mint to obtain some files I had there and to make the partition useable. Best would be to recover the Mint O/s intact and dual boot into it.

Someone out there have help?

---

### Post by Quackers on 2011-06-15
Have you run ```
sudo update-grub
``` in the terminal?
Does it pick up Linux Mint as grub.cfg is run?

---

### Post by TBABill on 2011-06-15
And did you verify your partition layout after install to be sure you didn't install over something if Grub is actually seeing all partitions?

---

### Post by JohnBonne on 2011-06-15
I tried several things. I updated Grub and I searched for a Mint in the launcher, I also tried to fing the partition several ways. Is there a way to detect the old install at all using softwares or a command line to find the old install. I have one last resort I know of. I will be right back.

---

### Post by JohnBonne on 2011-06-15
```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   566,546,431   566,544,384  83 Linux
/dev/sda2         566,548,478   625,141,759    58,593,282   5 Extended
/dev/sda5         566,548,480   625,141,759    58,593,280  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301908992 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1       2,200,680,153 2,930,272,064   729,591,912   7 NTFS / exFAT / HPFS
/dev/sdb2          84,550,095 2,200,680,089 2,116,129,995   f W95 Extended (LBA)
/dev/sdb5          84,550,158    91,008,224     6,458,067  83 Linux
/dev/sdb6          91,008,288 1,465,336,844 1,374,328,557   7 NTFS / exFAT / HPFS
/dev/sdb7       1,465,336,908 2,200,680,089   735,343,182   7 NTFS / exFAT / HPFS
/dev/sdb3               2,048    84,549,631    84,547,584  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        fad75621-ce4f-4e1e-8e0f-ade58a4461e7   ext4       
/dev/sda5        64bfc3e5-3ada-4be2-91d5-82b39ce12f1b   swap       
/dev/sdb1        01CBD0945E4134E0                       ntfs       
/dev/sdb3        5398b826-dc2f-4106-94a3-b0717b553e92   ext4       
/dev/sdb5        eddbccae-e949-4ef5-8b04-83283b8dc2c0   ext4       
/dev/sdb6        01CC23A0B75AEA30                       ntfs       
/dev/sdb7        8CC651E0C651CADA                       ntfs       Drive 2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/01CBD0945E4134E0  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb3        /media/5398b826-dc2f-4106-94a3-b0717b553e92 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /media/eddbccae-e949-4ef5-8b04-83283b8dc2c0 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb6        /media/01CC23A0B75AEA30  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb7        /media/Drive 2           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root fad75621-ce4f-4e1e-8e0f-ade58a4461e7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root fad75621-ce4f-4e1e-8e0f-ade58a4461e7
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root fad75621-ce4f-4e1e-8e0f-ade58a4461e7
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=fad75621-ce4f-4e1e-8e0f-ade58a4461e7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root fad75621-ce4f-4e1e-8e0f-ade58a4461e7
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=fad75621-ce4f-4e1e-8e0f-ade58a4461e7 ro single 
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root fad75621-ce4f-4e1e-8e0f-ade58a4461e7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root fad75621-ce4f-4e1e-8e0f-ade58a4461e7
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fad75621-ce4f-4e1e-8e0f-ade58a4461e7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=64bfc3e5-3ada-4be2-91d5-82b39ce12f1b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  72.135009766 = 77.454376960   boot/grub/core.img                             1
  72.137126923 = 77.456650240   boot/grub/grub.cfg                             1
   1.067607880 = 1.146335232    boot/initrd.img-2.6.38-8-generic               1
  72.133281708 = 77.452521472   boot/vmlinuz-2.6.38-8-generic                  1
   1.067607880 = 1.146335232    initrd.img                                     1
  72.133281708 = 77.452521472   vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

Here is the bootinfoscript information.

---

### Post by Quackers on 2011-06-15
I don't see Mint anywhere on your boot script output :-(
Maybe you over-wrote it?
Where was it?

---

### Post by JohnBonne on 2011-06-15
Thanks Quackers,

No, I didn't. Though I can't read it, I have a notion the boot summary is telling me there is no O/s on the Main Drive of the computer. According to the different Device readers  have used Windows is installed on the main drive and Ubuntu is installed there as well. According to Supergrub I have Ubuntu installed on the 1.5 Terrabyte ED, but the Ubuntu install says Ubuntu is installed on that drive, usung the Drives Manager that comes with Ubuntu. Ubuntu wasn't installed on the Windows/Mint Drive but that drive was disconnected during the Ubuntu install, for when I disconnect the ED and boot it up, the Ubuntu splash screen comes up, but the o/s wont boot. At lest that's what I remember before the truck hit me.

Whether or not I like it, I have to install Windows again, and then Ubuntu alongside it, and a fresh install of Mint or Other system of my choosing then can be installed on the ED. I have looked at my options and I have decided to take this course, as I was always wanting Ubuntu on the Main HDD with Mint or Xbuntu installed on the slowest drive. I love Mint and though I have the disks for Edbuntu, Xbuntu, and Unix, may choose it after all.

It would be easier this way. I have not planned everything out but I will map everything and have disks to back me up in case of failure. this is happening because I didn't plan things well from the start, didn't know there were different boot loaders and they will not boot together and may install in a way that makes cross linking a problem. I thought this problem was a Windows thing and was solved a long time ago.

But...It would be easier if different flavors of Linux didn't come with different arguments.

---

### Post by JohnBonne on 2011-06-18
Yep. Attention has to be paid to every detail during install to prevent over-writing of the operating systen and to make sure you have an O/s when installation is over. Each system has a different loader and a different way way to address hard disks.

I Even have had to write down the disk size to avoid writing to teh wrong hdd when installing. Microsoft is easier and I know its language or maybe because it has taken over most of these tasks for me since 3.1, I have allowed it to become grotesque.

Still working on it. I have Fedora installed and find it to be harder than Ubuntu, which is more user friendly. I will install Ubuntu later.

---

### Post by JohnBonne on 2011-06-26
Or it has become grotesque. Just look at the different size of one to another.

---


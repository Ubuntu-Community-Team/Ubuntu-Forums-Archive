---
title: "Remastersys installation - grub not installed."
date: 2010-09-19
forum: New to Ubuntu
---

### Post by Fifthmarch on 2010-09-19
So, I accidentally deleted ubuntu-desktop yesterday from Synaptic (Don't ask me how). I tried to use my remastersys USB to reinstall the system. Everything went fine, except that grub didn't install, and I can't boot it. 

I've tried to use this forum:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

but I'm stuck at this command:
sudo chroot /mnt/root /bin/bash
This is what I'm getting:
chroot: cannot run command `/bin/bash': No such file or directory

Any help?

---

### Post by wilee-nilee on 2010-09-19
Post the boot script in my signature in code tags as described.

---

### Post by Fifthmarch on 2010-09-19
What exactly is the boot script? I'm very new to this

---

### Post by wilee-nilee on 2010-09-19
> **Fifthmarch said:**
> What exactly is the boot script? I'm very new to this

Just click on it in my sig then download it, drag it to the desktop, then run this command.
```
sudo bash ~/Desktop/boot_info_script*.sh
``` 

This will create another file on the desktop, open it copy and paste the whole thing in a reply. The easiest way to get the code tags is to before pasting click on the # in the reply panel and put the text in between the generated code tags. The code tags are important as you will see a lot of text and so this make it a scrolling window.

---

### Post by Fifthmarch on 2010-09-19
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    22,009,049    22,008,987  83 Linux
/dev/sda2          22,009,050    70,011,269    48,002,220   5 Extended
/dev/sda5          22,009,176    30,009,419     8,000,244  82 Linux swap / Solaris
/dev/sda6          30,009,483    70,011,269    40,001,787  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    57,159,269    57,159,207  83 Linux
/dev/sdb2          57,159,270   371,728,034   314,568,765  83 Linux
/dev/sdb3         371,728,035   686,296,799   314,568,765  83 Linux
/dev/sdb4         686,296,800   976,768,064   290,471,265  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6baa752b-be03-43fc-9a77-1833b0aefb06   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a5875ae7-9abc-452b-931c-e8c3279f5c3e   swap                                     
/dev/sda6        98eb190f-b46d-46cf-8d75-a1c2d3e72980   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        51c5cf5d-3d7e-46b7-b51c-8ddebf81c7dc   ext3       For_Ubuntu                    
/dev/sdb2        e74d376d-1990-4d2c-a8e5-4c03b4a5c656   ext3       Partition1                    
/dev/sdb3        f26231af-d0c0-4a1e-8406-5a244bb0f6b4   ext3       Partition 2                   
/dev/sdb4        ccf415c0-6ca4-4971-b335-70b38cd2e2ff   ext3       Partition 3                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /mnt/root                ext3       (rw)
/dev             /mnt/root/dev            none       (rw,bind)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=6baa752b-be03-43fc-9a77-1833b0aefb06 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=98eb190f-b46d-46cf-8d75-a1c2d3e72980 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=a5875ae7-9abc-452b-931c-e8c3279f5c3e none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   7.6GB: boot/initrd.img-2.6.28-17-generic
   7.6GB: boot/initrd.img-2.6.31-18-generic
   7.6GB: boot/initrd.img-2.6.31-19-generic
   7.6GB: boot/initrd.img-2.6.31-20-generic
   7.6GB: boot/initrd.img-2.6.31-21-generic
   7.5GB: boot/initrd.img-2.6.31-22-generic
   7.6GB: boot/vmlinuz-2.6.28-17-generic
   7.6GB: boot/vmlinuz-2.6.31-18-generic
   7.6GB: boot/vmlinuz-2.6.31-19-generic
   7.6GB: boot/vmlinuz-2.6.31-20-generic
   7.6GB: boot/vmlinuz-2.6.31-21-generic
   7.7GB: boot/vmlinuz-2.6.31-22-generic
   7.5GB: initrd.img
   7.6GB: initrd.img.old
   7.7GB: vmlinuz
```

Hope I did that right

---

### Post by wilee-nilee on 2010-09-19
It looks like a lot is missing, I don't see the full boot file set for any distro. Your going to need somebody who is more qualified to help. IMHO it looks toasted but I could be wrong, and there may be ways to fix it, but I wouldn't peck at it just wait and see if somebody sees a fixable setup there. The good thing is that if it isn't fixable you can still get your stuff out with a live cd and a external to transfer to, or maybe some thing could be done with the 2 HD you have. 

A fresh install slipped in somewhere, would see all the other partitions as well probably, so there are options.

Just for a example here is a bootscript of mine for you to compare with.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    83,888,127    83,886,080   7 HPFS/NTFS
/dev/sda2         113,676,001   312,580,095   198,904,095   5 Extended
/dev/sda5         113,676,003   264,669,183   150,993,181  83 Linux
/dev/sda6         308,385,792   312,580,095     4,194,304  82 Linux swap / Solaris
/dev/sda7         264,671,232   308,383,743    43,712,512  83 Linux
/dev/sda3          83,891,430   113,675,939    29,784,510   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2CFB6750453E160C                       ntfs       W7                            
/dev/sda2: PTTYPE="dos" 
/dev/sda3        7D061649158B4024                       ntfs       share                         
/dev/sda5        6f28beba-e464-480e-9d4c-329416a13f3c   ext4       Lucid                         
/dev/sda6        c739a546-bd75-4a85-8a36-dc860c0895d2   swap                                     
/dev/sda7        dadc267d-cff9-4d6f-8551-b4a9c02fbeae   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
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
search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=5
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
    search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6f28beba-e464-480e-9d4c-329416a13f3c ro  vga=758  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6f28beba-e464-480e-9d4c-329416a13f3c ro single  vga=758
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2cfb6750453e160c
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d26066da6066c537
    chainloader +1
}
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
UUID=6f28beba-e464-480e-9d4c-329416a13f3c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=05e757f7-cfb0-4edb-b045-f5c46524db5e none            swap    sw              0       0




=================== sda5: Location of files loaded by Grub: ===================


 109.8GB: boot/grub/core.img
  59.3GB: boot/grub/grub.cfg
 110.1GB: boot/initrd.img-2.6.32-24-generic
 110.2GB: boot/vmlinuz-2.6.32-24-generic
 110.1GB: initrd.img
 110.2GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set dadc267d-cff9-4d6f-8551-b4a9c02fbeae
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set dadc267d-cff9-4d6f-8551-b4a9c02fbeae
set locale_dir=($root)/boot/grub/locale
set lang=
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
menuentry 'Ubuntu, with Linux 2.6.35-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set dadc267d-cff9-4d6f-8551-b4a9c02fbeae
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=dadc267d-cff9-4d6f-8551-b4a9c02fbeae ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set dadc267d-cff9-4d6f-8551-b4a9c02fbeae
    echo    'Loading Linux 2.6.35-19-generic ...'
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=dadc267d-cff9-4d6f-8551-b4a9c02fbeae ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2cfb6750453e160c
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6f28beba-e464-480e-9d4c-329416a13f3c ro vga=758 quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 6f28beba-e464-480e-9d4c-329416a13f3c
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6f28beba-e464-480e-9d4c-329416a13f3c ro single vga=758
    initrd /boot/initrd.img-2.6.32-24-generic
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=dadc267d-cff9-4d6f-8551-b4a9c02fbeae /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c739a546-bd75-4a85-8a36-dc860c0895d2 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 148.6GB: boot/grub/core.img
 155.1GB: boot/grub/grub.cfg
 140.1GB: boot/initrd.img-2.6.35-19-generic
 149.0GB: boot/vmlinuz-2.6.35-19-generic
 140.1GB: initrd.img
 149.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  18 55 72 6c 50 61 72 61  6d 65 74 65 72 52 65 61  |.UrlParameterRea|
00000010  64 65 72 20 43 6c 61 73  73 95 cf 52 b8 cf 52 d3  |der Class..R..R.|
00000020  cf 52 00 01 2a 07 4d 65  6d 62 65 72 73 00 01 30  |.R..*.Members..0|
00000030  14 55 72 6c 50 61 72 61  6d 65 74 65 72 57 72 69  |.UrlParameterWri|
00000040  74 65 72 28 29 01 01 43  0c 43 6f 6e 73 74 72 75  |ter()..C.Constru|
00000050  63 74 6f 72 73 ad d0 52  00 01 30 0d 47 65 74 52  |ctors..R..0.GetR|
00000060  65 71 75 65 73 74 55 72  6c 01 01 4d 07 4d 65 74  |equestUrl..M.Met|
00000070  68 6f 64 73 d8 d0 52 03  1d 65 63 6d 61 3a 32 34  |hods..R..ecma:24|
00000080  38 32 23 55 72 6c 50 61  72 61 6d 65 74 65 72 57  |82#UrlParameterW|
00000090  72 69 74 65 72 2f 18 55  72 6c 50 61 72 61 6d 65  |riter/.UrlParame|
000000a0  74 65 72 57 72 69 74 65  72 20 43 6c 61 73 73 a2  |terWriter Class.|
000000b0  d0 52 c5 d0 52 e9 d0 52  00 01 2a 07 4d 65 6d 62  |.R..R..R..*.Memb|
000000c0  65 72 73 00 01 30 20 56  61 6c 75 65 43 6f 6c 6c  |ers..0 ValueColl|
000000d0  65 63 74 69 6f 6e 50 61  72 61 6d 65 74 65 72 52  |ectionParameterR|
000000e0  65 61 64 65 72 28 29 01  01 43 0c 43 6f 6e 73 74  |eader()..C.Const|
000000f0  72 75 63 74 6f 72 73 c3  d1 52 00 01 30 0e 47 65  |ructors..R..0.Ge|
00000100  74 49 6e 69 74 69 61 6c  69 7a 65 72 00 01 31 0a  |tInitializer..1.|
00000110  49 6e 69 74 69 61 6c 69  7a 65 00 01 32 2c 49 73  |Initialize..2,Is|
00000120  53 75 70 70 6f 72 74 65  64 28 53 79 73 74 65 6d  |Supported(System|
00000130  2e 52 65 66 6c 65 63 74  69 6f 6e 2e 50 61 72 61  |.Reflection.Para|
00000140  6d 65 74 65 72 49 6e 66  6f 29 00 01 33 3c 49 73  |meterInfo)..3<Is|
00000150  53 75 70 70 6f 72 74 65  64 28 53 79 73 74 65 6d  |Supported(System|
00000160  2e 57 65 62 2e 53 65 72  76 69 63 65 73 2e 50 72  |.Web.Services.Pr|
00000170  6f 74 6f 63 6f 6c 73 2e  4c 6f 67 69 63 61 6c 4d  |otocols.LogicalM|
00000180  65 74 68 6f 64 49 6e 66  6f 29 02 0b 49 73 53 75  |ethodInfo)..IsSu|
00000190  70 70 6f 72 74 65 64 0b  49 73 53 75 70 70 6f 72  |pported.IsSuppor|
000001a0  74 65 64 9a d2 52 ca d2  52 00 01 34 04 52 65 61  |ted..R..R..4.Rea|
000001b0  64 04 01 4d 07 4d 65 74  68 6f 64 73 fa d1 00 fe  |d..M.Methods....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 1d f9 ff 08 00 fe  |................|
000001d0  ff ff 05 fe ff ff 1f 01  9b 0b 00 08 40 00 00 00  |............@...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Fifthmarch on 2010-09-19
I've got all my data backed up, including my home folder, so that's not a problem. I guess I'll just wait for any other suggestion.

---

### Post by wilee-nilee on 2010-09-19
> **Fifthmarch said:**
> I've got all my data backed up, including my home folder, so that's not a problem. I guess I'll just wait for any other suggestion.

Glad to hear your backed up.

---

### Post by Fifthmarch on 2010-09-21
I waited another day for more replies, then installed a fresh copy of Lucid. Got the preferences of all the applications done - took a day, but the system's fine now. Thanks for your help.

---


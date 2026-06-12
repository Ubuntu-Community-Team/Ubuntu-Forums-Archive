---
title: "Won't boot without flash drive"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by josh_2.0@comcast.net on 2011-01-05
I recently completed my first Ubunto installation (10.04 server LTS), but I think I made a mistake. While manually partitioning drives, I told it to mount my flash drive into /windows/ijosh (iJosh is the name of the flash drive in question) as fat32.
 
It mounts fine, and unmounts using $ sudo umount /windows/ijosh. The problem is that the server will not boot without the flash drive plugged in. If I unmount it, remove it, then reboot, it fails to boot. It starts booting, gets past the POST, then I get about a quarter page of startup messages, ending with this:
 
init: ureadahead-other main process (971) terminated with status 4
 
Then the computer just sits there.
 
If I then plug the flash drive in, it continues to start up just fine. The problem is that I don't want to have to have that flash drive plugged into that box every time I reboot the machine.
 
Anyway to fix this without having to reinstall the operating system? Any help would be appreciated.
 
 
Here's some additional information, in case it helps:
The machine contains 2 identical 320GB western digital hard drives. I partitioned them into 4 raid1 volumes to mount into /, /home, /var, and /temp, using ext4, ext3, ext3, and reiserfs, respectively.

---

### Post by presence1960 on 2011-01-05
Let's get a better look at your setup & boot process. Boot into Ubuntu with the flash disk plugged in. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by josh_2.0@comcast.net on 2011-01-08
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

md1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

md3: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   197,462,015   197,459,968  fd Linux raid autodetect
/dev/sda2         197,462,016   324,415,487   126,953,472  fd Linux raid autodetect
/dev/sda3         324,415,488   461,133,823   136,718,336  fd Linux raid autodetect
/dev/sda4         461,133,824   625,141,759   164,007,936  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   197,462,015   197,459,968  fd Linux raid autodetect
/dev/sdb2         197,462,016   324,415,487   126,953,472  fd Linux raid autodetect
/dev/sdb3         324,415,488   461,133,823   136,718,336  fd Linux raid autodetect
/dev/sdb4         461,133,824   625,141,759   164,007,936  fd Linux raid autodetect


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1               8,192    15,523,839    15,515,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/md0         51cfd42d-52c3-4a3c-8bb6-b280b5292e19   ext4                                     
/dev/md1         0bbc43ca-cda5-4a86-b1f3-a5c6e348c7d6   ext3                                     
/dev/md2         d09da6ba-057d-4a49-b88c-f4d4dc9280e4   ext3                                     
/dev/md3         b7783b29-1a6c-43b1-a980-09ccdeff8743   reiserfs                                 
/dev/sda1        f0393904-d951-8fb1-6764-a9db74b2fae3   linux_raid_member                               
/dev/sda2        3697dd6a-0d39-2d26-20f6-6bf77a18ce80   linux_raid_member                               
/dev/sda3        58faf240-35c5-ecb9-924a-4ab7a47063ed   linux_raid_member                               
/dev/sda4        46b018f2-531d-508d-d0c3-c8e399294ce1   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        f0393904-d951-8fb1-6764-a9db74b2fae3   linux_raid_member                               
/dev/sdb2        3697dd6a-0d39-2d26-20f6-6bf77a18ce80   linux_raid_member                               
/dev/sdb3        58faf240-35c5-ecb9-924a-4ab7a47063ed   linux_raid_member                               
/dev/sdb4        46b018f2-531d-508d-d0c3-c8e399294ce1   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        6332-3039                              vfat       IJOSH2                        
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/md0         /                        ext4       (rw,errors=remount-ro)
/dev/sdg1        /windows/ijosh           vfat       (rw,utf8,umask=007,gid=46)
/dev/md1         /home                    ext3       (rw)
/dev/md2         /var                     ext3       (rw)
/dev/md3         /tmp                     reiserfs   (rw)


=========================== md0/boot/grub/grub.cfg: ===========================

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
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
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
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-24-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
    linux    /boot/vmlinuz-2.6.32-24-server root=UUID=51cfd42d-52c3-4a3c-8bb6-b280b5292e19 ro   quiet
    initrd    /boot/initrd.img-2.6.32-24-server
}
menuentry 'Ubuntu, with Linux 2.6.32-24-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
    echo    'Loading Linux 2.6.32-24-server ...'
    linux    /boot/vmlinuz-2.6.32-24-server root=UUID=51cfd42d-52c3-4a3c-8bb6-b280b5292e19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
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

================================ md0/etc/fstab: ================================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=51cfd42d-52c3-4a3c-8bb6-b280b5292e19 /               ext4    errors=remount-ro 0       1
# /home was on /dev/md1 during installation
UUID=0bbc43ca-cda5-4a86-b1f3-a5c6e348c7d6 /home           ext3    defaults        0       2
# /tmp was on /dev/md3 during installation
UUID=b7783b29-1a6c-43b1-a980-09ccdeff8743 /tmp            reiserfs defaults        0       2
# /var was on /dev/md2 during installation
UUID=d09da6ba-057d-4a49-b88c-f4d4dc9280e4 /var            ext3    defaults        0       2
# /windows/ijosh was on /dev/sdg1 during installation
UUID=6332-3039  /windows/ijosh  vfat    utf8,umask=007,gid=46 0       1

==================== md0: Location of files loaded by Grub: ====================


  30.2GB: boot/grub/core.img
  30.2GB: boot/grub/grub.cfg
    .1GB: boot/initrd.img-2.6.32-24-server
  30.1GB: boot/vmlinuz-2.6.32-24-server
    .1GB: initrd.img
  30.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 


```

---

### Post by josh_2.0@comcast.net on 2011-01-08
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

md1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

md3: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   197,462,015   197,459,968  fd Linux raid autodetect
/dev/sda2         197,462,016   324,415,487   126,953,472  fd Linux raid autodetect
/dev/sda3         324,415,488   461,133,823   136,718,336  fd Linux raid autodetect
/dev/sda4         461,133,824   625,141,759   164,007,936  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   197,462,015   197,459,968  fd Linux raid autodetect
/dev/sdb2         197,462,016   324,415,487   126,953,472  fd Linux raid autodetect
/dev/sdb3         324,415,488   461,133,823   136,718,336  fd Linux raid autodetect
/dev/sdb4         461,133,824   625,141,759   164,007,936  fd Linux raid autodetect


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1               8,192    15,523,839    15,515,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/md0         51cfd42d-52c3-4a3c-8bb6-b280b5292e19   ext4                                     
/dev/md1         0bbc43ca-cda5-4a86-b1f3-a5c6e348c7d6   ext3                                     
/dev/md2         d09da6ba-057d-4a49-b88c-f4d4dc9280e4   ext3                                     
/dev/md3         b7783b29-1a6c-43b1-a980-09ccdeff8743   reiserfs                                 
/dev/sda1        f0393904-d951-8fb1-6764-a9db74b2fae3   linux_raid_member                               
/dev/sda2        3697dd6a-0d39-2d26-20f6-6bf77a18ce80   linux_raid_member                               
/dev/sda3        58faf240-35c5-ecb9-924a-4ab7a47063ed   linux_raid_member                               
/dev/sda4        46b018f2-531d-508d-d0c3-c8e399294ce1   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        f0393904-d951-8fb1-6764-a9db74b2fae3   linux_raid_member                               
/dev/sdb2        3697dd6a-0d39-2d26-20f6-6bf77a18ce80   linux_raid_member                               
/dev/sdb3        58faf240-35c5-ecb9-924a-4ab7a47063ed   linux_raid_member                               
/dev/sdb4        46b018f2-531d-508d-d0c3-c8e399294ce1   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        6332-3039                              vfat       IJOSH2                        
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/md0         /                        ext4       (rw,errors=remount-ro)
/dev/sdg1        /windows/ijosh           vfat       (rw,utf8,umask=007,gid=46)
/dev/md1         /home                    ext3       (rw)
/dev/md2         /var                     ext3       (rw)
/dev/md3         /tmp                     reiserfs   (rw)


=========================== md0/boot/grub/grub.cfg: ===========================

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
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
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
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-24-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
    linux    /boot/vmlinuz-2.6.32-24-server root=UUID=51cfd42d-52c3-4a3c-8bb6-b280b5292e19 ro   quiet
    initrd    /boot/initrd.img-2.6.32-24-server
}
menuentry 'Ubuntu, with Linux 2.6.32-24-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
    echo    'Loading Linux 2.6.32-24-server ...'
    linux    /boot/vmlinuz-2.6.32-24-server root=UUID=51cfd42d-52c3-4a3c-8bb6-b280b5292e19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
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

================================ md0/etc/fstab: ================================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=51cfd42d-52c3-4a3c-8bb6-b280b5292e19 /               ext4    errors=remount-ro 0       1
# /home was on /dev/md1 during installation
UUID=0bbc43ca-cda5-4a86-b1f3-a5c6e348c7d6 /home           ext3    defaults        0       2
# /tmp was on /dev/md3 during installation
UUID=b7783b29-1a6c-43b1-a980-09ccdeff8743 /tmp            reiserfs defaults        0       2
# /var was on /dev/md2 during installation
UUID=d09da6ba-057d-4a49-b88c-f4d4dc9280e4 /var            ext3    defaults        0       2
# /windows/ijosh was on /dev/sdg1 during installation
UUID=6332-3039  /windows/ijosh  vfat    utf8,umask=007,gid=46 0       1

==================== md0: Location of files loaded by Grub: ====================


  30.2GB: boot/grub/core.img
  30.2GB: boot/grub/grub.cfg
    .1GB: boot/initrd.img-2.6.32-24-server
  30.1GB: boot/vmlinuz-2.6.32-24-server
    .1GB: initrd.img
  30.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf
```

-------------------------------------------------------------------------------------------------------

I posted it twice because I wanted it in direct reply to your post instead of in reply to my original post

---

### Post by presence1960 on 2011-01-08
> **josh_2.0@comcast.net said:**
> ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

md1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

md3: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   197,462,015   197,459,968  fd Linux raid autodetect
/dev/sda2         197,462,016   324,415,487   126,953,472  fd Linux raid autodetect
/dev/sda3         324,415,488   461,133,823   136,718,336  fd Linux raid autodetect
/dev/sda4         461,133,824   625,141,759   164,007,936  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   197,462,015   197,459,968  fd Linux raid autodetect
/dev/sdb2         197,462,016   324,415,487   126,953,472  fd Linux raid autodetect
/dev/sdb3         324,415,488   461,133,823   136,718,336  fd Linux raid autodetect
/dev/sdb4         461,133,824   625,141,759   164,007,936  fd Linux raid autodetect


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1               8,192    15,523,839    15,515,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/md0         51cfd42d-52c3-4a3c-8bb6-b280b5292e19   ext4                                     
/dev/md1         0bbc43ca-cda5-4a86-b1f3-a5c6e348c7d6   ext3                                     
/dev/md2         d09da6ba-057d-4a49-b88c-f4d4dc9280e4   ext3                                     
/dev/md3         b7783b29-1a6c-43b1-a980-09ccdeff8743   reiserfs                                 
/dev/sda1        f0393904-d951-8fb1-6764-a9db74b2fae3   linux_raid_member                               
/dev/sda2        3697dd6a-0d39-2d26-20f6-6bf77a18ce80   linux_raid_member                               
/dev/sda3        58faf240-35c5-ecb9-924a-4ab7a47063ed   linux_raid_member                               
/dev/sda4        46b018f2-531d-508d-d0c3-c8e399294ce1   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        f0393904-d951-8fb1-6764-a9db74b2fae3   linux_raid_member                               
/dev/sdb2        3697dd6a-0d39-2d26-20f6-6bf77a18ce80   linux_raid_member                               
/dev/sdb3        58faf240-35c5-ecb9-924a-4ab7a47063ed   linux_raid_member                               
/dev/sdb4        46b018f2-531d-508d-d0c3-c8e399294ce1   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        6332-3039                              vfat       IJOSH2                        
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/md0         /                        ext4       (rw,errors=remount-ro)
/dev/sdg1        /windows/ijosh           vfat       (rw,utf8,umask=007,gid=46)
/dev/md1         /home                    ext3       (rw)
/dev/md2         /var                     ext3       (rw)
/dev/md3         /tmp                     reiserfs   (rw)


=========================== md0/boot/grub/grub.cfg: ===========================

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
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
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
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-24-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
    linux    /boot/vmlinuz-2.6.32-24-server root=UUID=51cfd42d-52c3-4a3c-8bb6-b280b5292e19 ro   quiet
    initrd    /boot/initrd.img-2.6.32-24-server
}
menuentry 'Ubuntu, with Linux 2.6.32-24-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
    echo    'Loading Linux 2.6.32-24-server ...'
    linux    /boot/vmlinuz-2.6.32-24-server root=UUID=51cfd42d-52c3-4a3c-8bb6-b280b5292e19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 51cfd42d-52c3-4a3c-8bb6-b280b5292e19
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

================================ md0/etc/fstab: ================================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=51cfd42d-52c3-4a3c-8bb6-b280b5292e19 /               ext4    errors=remount-ro 0       1
# /home was on /dev/md1 during installation
UUID=0bbc43ca-cda5-4a86-b1f3-a5c6e348c7d6 /home           ext3    defaults        0       2
# /tmp was on /dev/md3 during installation
UUID=b7783b29-1a6c-43b1-a980-09ccdeff8743 /tmp            reiserfs defaults        0       2
# /var was on /dev/md2 during installation
UUID=d09da6ba-057d-4a49-b88c-f4d4dc9280e4 /var            ext3    defaults        0       2
# /windows/ijosh was on /dev/sdg1 during installation
UUID=6332-3039  /windows/ijosh  vfat    utf8,umask=007,gid=46 0       1

==================== md0: Location of files loaded by Grub: ====================


  30.2GB: boot/grub/core.img
  30.2GB: boot/grub/grub.cfg
    .1GB: boot/initrd.img-2.6.32-24-server
  30.1GB: boot/vmlinuz-2.6.32-24-server
    .1GB: initrd.img
  30.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf
```

-------------------------------------------------------------------------------------------------------

I posted it twice because I wanted it in direct reply to your post instead of in reply to my original post

I am not experienced with RAID & GRUB. I would wait until someone who has the experience comes along. By me posting this this will bump your thread back to the front chronoligically so it won't be buried .

---


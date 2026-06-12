---
title: "Can no longer boot from external or internal HDD, grub rescue prompt"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by craellson on 2010-05-26
Alright, In Win7 I shrunk the primary partition on my usb external drive. I booted from the 10.04 Install CD, and installed Ubuntu in the free space on the drive. I restarted after the installation, and grub took me to a boot screen, I booted Windows to make sure it worked. Then, I went back to Ubuntu and played around a bit. The only thing I can think I did was to copy a movie file into the Ubuntu partition to play it. I then shut down the system. Finally, I unplugged the external drive and tried to boot up, but all I got was a grub rescue prompt. I checked my BIOS boot order, tried manually booting from the internal HDD (which only has Windows) and the external, with no luck. Ubuntu is technically on the secondary partition on the external, but it booted fine before, so that shouldn't be an issue. I ran the boot info script as suggested:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc8: _________________________________________________________________________

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

/dev/sda1    *          2,048   312,578,047   312,576,000   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301885440 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             64 1,188,003,846 1,188,003,783   7 HPFS/NTFS
/dev/sdc2       1,188,005,886 2,930,276,351 1,742,270,466   5 Extended
/dev/sdc5       2,211,991,552 2,918,205,439   706,213,888  83 Linux
/dev/sdc6       2,918,207,488 2,930,276,351    12,068,864  82 Linux swap / Solaris
/dev/sdc7       1,188,005,888 2,199,920,639 1,011,914,752  83 Linux
/dev/sdc8       2,199,922,688 2,211,989,503    12,066,816  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7CC2B2C2C2B27FC6                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        08A0EC9AA0EC900C                       ntfs       Drive of DOOM                 
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        e2db587a-d941-464c-b18f-d82330a95739   ext4                                     
/dev/sdc6        945effa3-1175-4ac3-aa3f-31313105c842   swap                                     
/dev/sdc7        2fdb8914-0ff3-4655-848f-7e5cc7f2b182   ext4                                     
/dev/sdc8        82a5be41-b010-48cb-b907-4b34d758646a   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)
/dev/sdc5        /media/e2db587a-d941-464c-b18f-d82330a95739 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set e2db587a-d941-464c-b18f-d82330a95739
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
search --no-floppy --fs-uuid --set e2db587a-d941-464c-b18f-d82330a95739
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
    search --no-floppy --fs-uuid --set e2db587a-d941-464c-b18f-d82330a95739
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=e2db587a-d941-464c-b18f-d82330a95739 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e2db587a-d941-464c-b18f-d82330a95739
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=e2db587a-d941-464c-b18f-d82330a95739 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e2db587a-d941-464c-b18f-d82330a95739
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e2db587a-d941-464c-b18f-d82330a95739 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e2db587a-d941-464c-b18f-d82330a95739
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e2db587a-d941-464c-b18f-d82330a95739 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e2db587a-d941-464c-b18f-d82330a95739
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e2db587a-d941-464c-b18f-d82330a95739
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7cc2b2c2c2b27fc6
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=e2db587a-d941-464c-b18f-d82330a95739 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=945effa3-1175-4ac3-aa3f-31313105c842 none            swap    sw              0       0

=================== sdc5: Location of files loaded by Grub: ===================


1388.2GB: boot/grub/core.img
1366.8GB: boot/grub/grub.cfg
1388.2GB: boot/initrd.img-2.6.32-21-generic
1388.2GB: boot/initrd.img-2.6.32-22-generic
1388.2GB: boot/vmlinuz-2.6.32-21-generic
1388.2GB: boot/vmlinuz-2.6.32-22-generic
1388.2GB: initrd.img
1388.2GB: initrd.img.old
1388.2GB: vmlinuz
1388.2GB: vmlinuz.old

=========================== sdc7/boot/grub/grub.cfg: ===========================

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
set root='(hd1,7)'
search --no-floppy --fs-uuid --set 2fdb8914-0ff3-4655-848f-7e5cc7f2b182
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
set root='(hd1,7)'
search --no-floppy --fs-uuid --set 2fdb8914-0ff3-4655-848f-7e5cc7f2b182
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set 2fdb8914-0ff3-4655-848f-7e5cc7f2b182
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2fdb8914-0ff3-4655-848f-7e5cc7f2b182 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set 2fdb8914-0ff3-4655-848f-7e5cc7f2b182
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2fdb8914-0ff3-4655-848f-7e5cc7f2b182 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set 2fdb8914-0ff3-4655-848f-7e5cc7f2b182
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set 2fdb8914-0ff3-4655-848f-7e5cc7f2b182
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7cc2b2c2c2b27fc6
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sdc5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e2db587a-d941-464c-b18f-d82330a95739
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=e2db587a-d941-464c-b18f-d82330a95739 ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sdc5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e2db587a-d941-464c-b18f-d82330a95739
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=e2db587a-d941-464c-b18f-d82330a95739 ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdc5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e2db587a-d941-464c-b18f-d82330a95739
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e2db587a-d941-464c-b18f-d82330a95739 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdc5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e2db587a-d941-464c-b18f-d82330a95739
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e2db587a-d941-464c-b18f-d82330a95739 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc7 during installation
UUID=2fdb8914-0ff3-4655-848f-7e5cc7f2b182 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc8 during installation
UUID=82a5be41-b010-48cb-b907-4b34d758646a none            swap    sw              0       0

=================== sdc7: Location of files loaded by Grub: ===================


 612.7GB: boot/grub/core.img
 937.1GB: boot/grub/grub.cfg
 612.6GB: boot/initrd.img-2.6.32-21-generic
 612.6GB: boot/vmlinuz-2.6.32-21-generic
 612.6GB: initrd.img
 612.6GB: vmlinuz

```

I thought it was only installed on the external drive, but I guess not.
Any help is appreciated.

---

### Post by Peter09 on 2010-05-26
When you installed Ubuntu the details needed to Boot all your systems are placed in a directory in the Ubuntu partition - so even when you boot to windows Grub needs to go to the Ubuntu partion to find the necessary information to complete the boot.
 
When you removed the external drive you also removed the location Grub needs.

---

### Post by craellson on 2010-05-26
Right, but now even when I have the external drive plugged in, I still get the grub prompt. Additionally, without the external drive plugged in I can't boot either, and I get the grub prompt. If I'm getting the prompt, that means grub is on my internal drive somehow. So with or without the drive, I am getting the same response and cannot boot to Windows or Ubuntu.

---

### Post by craellson on 2010-05-26
I  could really use some help here, if anything to just get back to Windows at least.

---

### Post by craellson on 2010-05-26
Wait, it seems I've made another mistake. I had said that I deleted the old Ubuntu partition on my external drive. However, that's not the case. When I installed Ubuntu it actually split the remaining space on the drive, so now I have two 10.04 partitions and a Windows partition. In the installer I told it to delete the Ubuntu partition but I guess it didn't. Crap.

---

### Post by craellson on 2010-05-26
Please, I don't know what to do, anyone?

---

### Post by lkraemer on 2010-05-26
OK, a bit of information before you proceed.  Let's assume you have
a new Hard Drive, and you Boot from a Ubuntu LiveCD and install
Ubuntu.  Then you restart and remove the LiveCD and Ubuntu is running
from your Hard Drive.  Fine, but you decide to boot the LiveCD again
and delete the Ubuntu partition and the swap partition.  At that point
you restart after removing the LiveCD.  The Master Boot Record still
exists on your Hard Drive and you will see the exact message as
"grub recover >"  So, it just means the Boot process can't locat the
Initial Program Loader (IPL).

So, if Windows 7 was installed on your original Hard drive and you want
it back you need to restore the Win 7 MBR or replace it so Win 7 can boot.
Now, there is a Floppy/CDROM/USB Flash program that restored the XP
MBR called Supergrub, but I'm not current on what or how it works with
Win 7.  You can do some searching with Google for information on how to
replace the Win 7 MBR.  That will get your system booting back in Win 7
from the original Hard Drive.
Ref:
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)
[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Next I'd like to see you boot the Ubuntu LiveCD and then run Gparted
and take screenshots of all your Physical Hard Drives and USB Drives,
as it gives a graphic of the Partitions along with the mount points.

Once you get Win 7 booting from the Hard Drive, and can once again calm down,
and not make any more hasty decisions/mistakes, post the above information
and the pngs screenshots.

By then maybe some guru will chime in......otherwise we'll proceed.

Worst case, just keep booting the Ubuntu LiveCD until you get things on the 
road to recovery.  Just don't write to the Hard Drive or the External
USB Drive.

Your script gives good information, I just need to digest it a bit.

lk

---

### Post by Peter09 on 2010-05-26
What I would do is boot again from the live CD - without the external drive connected. Go through the install process again, but when it comes to the partitioner select manual partitioning.

Tread carefully from here.....

Delete all the Ubuntu partitions, leaving the NTFS partions (windows) well alone. Once you have deleted them you can tell the installer to use the spare space to install Ubuntu. With any luck you will end up with a dual boot system - windows and Ubuntu.

---

### Post by craellson on 2010-05-26
Great, thanks!

It seems I am able to boot normally (grub gives me the option to boot to Ubuntu or Windows) when I press the setup button when the BIOS is starting up. This allows the BIOS to recognize the external drive. Then, I have to boot from the internal drive, and I can choose either OS. Before your reply I managed to wipe the old Ubuntu installs and put in a new one, here's the new Boot Info:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   312,578,047   312,576,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301885440 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             64 1,188,003,846 1,188,003,783   7 HPFS/NTFS
/dev/sdb2       1,188,005,886 2,168,555,519   980,549,634   5 Extended
/dev/sdb5       1,188,005,888 1,191,993,343     3,987,456  82 Linux swap / Solaris
/dev/sdb6       1,191,995,392 2,168,555,519   976,560,128  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7CC2B2C2C2B27FC6                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        08A0EC9AA0EC900C                       ntfs       Drive of DOOM                 
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        57cf61cb-29a2-413a-84e3-7b8ce9d6470b   swap                                     
/dev/sdb6        28961485-1e64-4d9f-8be4-41354d568ca8   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/Drive of DOOM     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 28961485-1e64-4d9f-8be4-41354d568ca8
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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 28961485-1e64-4d9f-8be4-41354d568ca8
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 28961485-1e64-4d9f-8be4-41354d568ca8
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=28961485-1e64-4d9f-8be4-41354d568ca8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 28961485-1e64-4d9f-8be4-41354d568ca8
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=28961485-1e64-4d9f-8be4-41354d568ca8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 28961485-1e64-4d9f-8be4-41354d568ca8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 28961485-1e64-4d9f-8be4-41354d568ca8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7cc2b2c2c2b27fc6
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc6       /               ext4    errors=remount-ro 0       1
/dev/sdc5       none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


 934.7GB: boot/grub/core.img
 887.5GB: boot/grub/grub.cfg
 934.7GB: boot/initrd.img-2.6.32-21-generic
 934.7GB: boot/vmlinuz-2.6.32-21-generic
 934.7GB: initrd.img
 934.7GB: vmlinuz
```I didn't want to install Ubuntu on my laptop, only the external drive. At this point I'm only looking to remove Ubuntu and return to Windows, my friend will eventually be installing Ubuntu on my external drive.

Thanks again.

---

### Post by oldfred on 2010-05-26
You have your boot loaders reversed. You want the windows on sda and Ubuntu on the external.

I would reinstall Ubuntu's grub to the external. I am not sure why one listing showed it as sdc and the other as sdb?

Boot into ubuntu and from your Ubuntu install you can reinstall grub to the external. Double check whether it is sdc or sdb.

sudo dpkg-reconfigure grub-pc

If will give you several screens but the last will let you choose sda, sdb or sdc, just do not choose sda.

If you end up with issues you can alway reinstall from a liveCd.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


You can from Ubuntu install a generic boot loader that will boot windows.
sudo  apt-get install lilo
sudo lilo -M /dev/sda mbr

Or you can use a windows recovery disk and run fixMBR.

---


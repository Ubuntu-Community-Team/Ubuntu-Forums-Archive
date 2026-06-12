---
title: "Taking system from dual boot to ubuntu only"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by wingrider78 on 2010-06-29
Hello all, I have been dual booting winxp and ubuntu for quite some time now and have finally decided to get rid of xp altogether and just run it in virtualbox for the few things that I need it to run.

Here is the current setup that I have...

sda - winxp (250gb - ntfs obviously) on sata1
sdb - ubuntu 10.04 (250gb - ext4) on sata2
sdc - storage (1tb - ntfs - in external case)

all drives are SATA

I would like to remove sda out of the box, put sdb on sata1 and put sdc on sata2, and put sda in the external box for use later.

I know I can physically do the move, but I have no idea if it will mess with my fstab or grub or make my system unbootable...

Are there any precautionary steps to take to ensure that everything goes smoothly with the switch?

---

### Post by wilee-nilee on 2010-06-29
> **wingrider78 said:**
> Hello all, I have been dual booting winxp and ubuntu for quite some time now and have finally decided to get rid of xp altogether and just run it in virtualbox for the few things that I need it to run.

Here is the current setup that I have...

sda - winxp (250gb - ntfs obviously) on sata1
sdb - ubuntu 10.04 (250gb - ext4) on sata2
sdc - storage (1tb - ntfs - in external case)

all drives are SATA

I would like to remove sda out of the box, put sdb on sata1 and put sdc on sata2, and put sda in the external box for use later.

I know I can physically do the move, but I have no idea if it will mess with my fstab or grub or make my system unbootable...

Are there any precautionary steps to take to ensure that everything goes smoothly with the switch?

Post the bootscript on my signature in code tags as described. I suspect that the grub bootloader is in sda so we should just take a look at the whole setup.

---

### Post by wingrider78 on 2010-06-29
I just remembered, that I should also mention that I had already formatted the existing xp drive (sda) before I realized that once I restart, everything could be messed up.   Hopefully that isn't too much of an issue.  Here is the result of bootscript...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   482,396,159   482,394,112  83 Linux
/dev/sdb2         482,398,206   488,396,799     5,998,594   5 Extended
/dev/sdb5         482,398,208   488,396,799     5,998,592  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2A89C86204FAF9FA                       ntfs       250GBHDD                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5317eb89-2518-4d2b-a90f-5ec9750b4ba6   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        987d37df-47c0-418b-857c-dbc2a43fef80   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        183B47AC017F4E61                       ntfs       storagedrive                  
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw)
/dev/sda1        /media/250GBHDD          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/storagedrive      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 5317eb89-2518-4d2b-a90f-5ec9750b4ba6
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 5317eb89-2518-4d2b-a90f-5ec9750b4ba6
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
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5317eb89-2518-4d2b-a90f-5ec9750b4ba6
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5317eb89-2518-4d2b-a90f-5ec9750b4ba6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5317eb89-2518-4d2b-a90f-5ec9750b4ba6
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5317eb89-2518-4d2b-a90f-5ec9750b4ba6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5317eb89-2518-4d2b-a90f-5ec9750b4ba6
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5317eb89-2518-4d2b-a90f-5ec9750b4ba6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5317eb89-2518-4d2b-a90f-5ec9750b4ba6
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5317eb89-2518-4d2b-a90f-5ec9750b4ba6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5317eb89-2518-4d2b-a90f-5ec9750b4ba6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5317eb89-2518-4d2b-a90f-5ec9750b4ba6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b820bb7620bb3a68
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

/dev/fd0 /media/floppy0 vfat noauto 0 0
UUID=B820BB7620BB3A68 /media/DRIVE1 ntfs-3g users 0 0
UUID=5317eb89-2518-4d2b-a90f-5ec9750b4ba6 / ext4 defaults 0 1
UUID=987d37df-47c0-418b-857c-dbc2a43fef80 swap swap sw 0 0

=================== sdb1: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
 137.9GB: boot/grub/grub.cfg
  34.5GB: boot/initrd.img-2.6.32-21-generic
  36.5GB: boot/initrd.img-2.6.32-22-generic
    .1GB: boot/vmlinuz-2.6.32-21-generic
  36.5GB: boot/vmlinuz-2.6.32-22-generic
  36.5GB: initrd.img
  34.5GB: initrd.img.old
  36.5GB: vmlinuz
    .1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  f7 02 55 55 08 00 00 00  98 99 c4 09 00 00 00 00  |..UU............|
00000010  08 00 00 00 cf cf cf cf  cf cf cf cf 14 00 00 00  |................|
00000020  f7 02 55 55 08 00 00 00  88 62 c0 09 00 00 00 00  |..UU.....b......|
00000030  08 00 00 00 cf cf cf cf  cf cf cf cf 14 00 00 00  |................|
00000040  f7 02 55 55 08 00 00 00  00 00 00 00 68 6a bf 09  |..UU........hj..|
00000050  08 00 00 00 cf cf cf cf  10 00 00 00 14 00 00 00  |................|
00000060  f7 02 55 55 14 00 00 00  00 00 00 00 16 00 00 00  |..UU............|
00000070  48 2e c0 09 00 00 00 00  88 63 c5 09 14 00 00 00  |H........c......|
00000080  f7 02 55 55 14 00 00 00  04 00 00 00 00 00 00 00  |..UU............|
00000090  df df df df 00 00 00 00  e8 56 c0 09 14 00 00 00  |.........V......|
000000a0  f7 02 55 55 08 00 00 00  c8 30 c0 09 00 00 00 00  |..UU.....0......|
000000b0  08 00 00 00 cf cf cf cf  cf cf cf cf cf cf cf cf  |................|
000000c0  f7 02 55 55 08 00 00 00  00 00 00 00 08 28 c0 09  |..UU.........(..|
000000d0  08 00 00 00 cf cf cf cf  cf cf 12 00 00 00 00 00  |................|
000000e0  f7 02 55 55 08 00 00 00  a8 73 bf 09 00 00 00 00  |..UU.....s......|
000000f0  08 00 00 00 cf cf cf cf  10 00 00 00 cf cf cf cf  |................|
00000100  f7 02 55 55 08 00 00 00  e8 2c c2 09 00 00 00 00  |..UU.....,......|
00000110  08 00 00 00 cf cf cf cf  cf cf cf cf 14 00 00 00  |................|
00000120  f7 02 55 55 07 00 00 00  72 65 74 75 72 6e 00 07  |..UU....return..|
00000130  00 00 00 cf cf cf cf cf  10 00 00 00 14 00 00 00  |................|
00000140  f7 02 55 55 08 00 00 00  a8 86 c0 09 00 00 00 00  |..UU............|
00000150  08 00 00 00 cf cf cf cf  cf cf cf cf 14 00 00 00  |................|
00000160  f7 02 55 55 14 00 00 00  04 00 00 00 00 00 00 00  |..UU............|
00000170  df df df df 00 00 00 00  c8 d4 c4 09 14 00 00 00  |................|
00000180  f7 03 55 55 15 00 00 00  5f 5f 67 76 66 73 5f 6d  |..UU....__gvfs_m|
00000190  75 6c 74 69 70 6c 65 5f  75 72 69 73 00 15 00 00  |ultiple_uris....|
000001a0  00 cf cf cf cf cf cf cf  cf cf cf cf cf cf cf cf  |................|
000001b0  cf cf cf 2b 00 00 00 cf  cf cf cf cf cf cf 00 fe  |...+............|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 88 5b 00 00 00  |............[...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Seanlol on 2010-06-29
> **wingrider78 said:**
> Hello all, I have been dual booting winxp and ubuntu for quite some time now and have finally decided to get rid of xp altogether and just run it in virtualbox for the few things that I need it to run.

Here is the current setup that I have...

sda - winxp (250gb - ntfs obviously) on sata1
sdb - ubuntu 10.04 (250gb - ext4) on sata2
sdc - storage (1tb - ntfs - in external case)

all drives are SATA

I would like to remove sda out of the box, put sdb on sata1 and put sdc on sata2, and put sda in the external box for use later.

I know I can physically do the move, but I have no idea if it will mess with my fstab or grub or make my system unbootable...

Are there any precautionary steps to take to ensure that everything goes smoothly with the switch?

I just did something similar today. Create a backup, boot into the Live CD (you won't be able to unmount the swap file from Ubuntu) and GParted will let you delete the NTFS file system, then all you have to do is resize the ext4 file system to take up all the available space.

Note that resizing a partition takes a long time. Possibly 60+ minutes.

EDIT: Didn't see you wanted to keep the WinXP filesystem. (?) Disregard the above comments. You could always just do a system backup and move the drives around. If it doesn't harm the system, then you win. If it does, you can move the drives back into their original places and restore your system

---

### Post by wilee-nilee on 2010-06-29
So how is any of it booting, either the script is not reading correctly or you have no bootloaders in any of the three HD's mbr's. I see a unknown on sdb though. Is this a raid setup?

---

### Post by wilee-nilee on 2010-06-29
see next post

---

### Post by oldfred on 2010-06-30
You need to make sure you have grub installed to the sdb drive. But since both sda & sdb are 250GB it is difficult in BIOS to know which drive is which. Once you have moved Ubuntu drive to sda then in BIOS you need to select that 250GB drive as the boot drive.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub


If you are still running your system how did you boot?

To make sure it reinstalls to sda after it is moved.

sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

If reinstalling from liveCD but you will have to change to sdb or sda whichever drive is first:
Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by wingrider78 on 2010-06-30
> **wilee-nilee said:**
> So how is any of it booting, either the script is not reading correctly or you have no bootloaders in any of the three HD's mbr's. I see a unknown on sdb though. Is this a raid setup?

It is not a raid setup.  I doubt any of it will boot.  I haven't rebooted the system since formatting my winxp drive (sda)  Wanted to sort this issue out before rebooting since I figured that it wouldn't boot.

Whatever you are seeing on sdb is from my fresh install of lucid that I did when it came out.  I did a backup from jaunty, and did a clean install from livecd of lucid.  The install created the 3 partitions, main for lucid, the unknown you are seeing and a swap.

---

### Post by wingrider78 on 2010-06-30
> **oldfred said:**
> You need to make sure you have grub installed to the sdb drive. But since both sda & sdb are 250GB it is difficult in BIOS to know which drive is which. Once you have moved Ubuntu drive to sda then in BIOS you need to select that 250GB drive as the boot drive.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub


If you are still running your system how did you boot?

To make sure it reinstalls to sda after it is moved.

sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

If reinstalling from liveCD but you will have to change to sdb or sda whichever drive is first:
Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

Are you saying to move the drive first and then follow the steps you gave???  If so, I doubt that I'll be able to do anything once the power has been turned off and it needs to boot again...also, when I install grub to the linux drive, will I be installing to sdb, or to the actual partition where linux is, sdb1???

Here is the output of fdisk -l
```
Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bb88f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30028   241197056   83  Linux
/dev/sdb2           30028       30402     2999297    5  Extended
/dev/sdb5           30028       30402     2999296   82  Linux swap / Solaris

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007190b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007c0cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS

```

---

### Post by oldfred on 2010-06-30
I was not sure if you were in your system or not so I gave instructions to install from your working system or from a liveCD. Just follow the instructions to reinstall grub but use sdb (not sda in example given) & (since that is what it is now). You can rerun script if you want to confirm it has installed to the MBR.

Then switch drives & make sure you are booting from the 250GB drive with Ubuntu & grub. It should now be sda. The run the sudo dpkg-reconfigure grub-pc to make sure it knows it is sda.

---

### Post by wingrider78 on 2010-06-30
I just installed grub to sdb with no errors, re-ran the script and found that grub had in fact installed on sdb.  So I will try powering down and moving the drives around and see where we stand.  

Thanks for the help so far...

---

### Post by wingrider78 on 2010-06-30
Oldfred, your instructions were perfect...it went smoothly and there were no problems.  Thank you for the help.  Will mark as solved.

---


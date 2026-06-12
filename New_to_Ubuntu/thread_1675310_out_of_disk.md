---
title: "out of disk"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by tanaynet on 2011-01-25
i cant start my ubuntu karmic because of this error in grub

---

### Post by [Snc] on 2011-01-25
> **tanaynet said:**
> i cant start my ubuntu karmic because of this error in grub

Out of disk:


check this thread:
[http://ubuntuforums.org/showthread.php?t=1331730](http://ubuntuforums.org/showthread.php?t=1331730)

---

### Post by Rubi1200 on 2011-01-25
> **tanaynet said:**
> i cant start my ubuntu karmic because of this error in grub
Hi and welcome to the forums :)

If you expect people to help you, please provide more information.

1. are you booting with Windows?

2. is this a Wubi install?

3. what happened, to the best of your knowledge, to cause this?

The solution may be easy depending on what you tell us.

Thanks.

---

### Post by tanaynet on 2011-01-25
yes I have windows xp and ubuntu karmic 9.10 . I was copying some files(nearly 15 gb:p) to my ubuntu' desktop and it suddenly frozen.When I restart I got this error..I read everthing on the internet but I cant solve yet..


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbeacbeac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8355    67111506    7  HPFS/NTFS
/dev/sda2            8356       12828    35929372+   7  HPFS/NTFS
/dev/sda3           12829       16176    26892810    7  HPFS/NTFS
/dev/sda4           16177       19457    26354632+   5  Extended
/dev/sda5           16177       19316    25222018+  83  Linux
/dev/sda6           19317       19457     1132551   82  Linux swap / Solaris

---

### Post by tanaynet on 2011-01-25
Windows doesnt working too omg. it said that some system files are missing

---

### Post by Rubi1200 on 2011-01-25
Okay, so we need to see some more information to troubleshoot this.

Please do the following from a LiveCD or LiveUSB:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
 sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

The other command I need you to run from the terminal is this:
```
 df -Th
```

Thanks.

---

### Post by tanaynet on 2011-01-25
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbeacbeac

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   134,223,074   134,223,012   7 HPFS/NTFS
/dev/sda2         134,223,075   206,081,819    71,858,745   7 HPFS/NTFS
/dev/sda3         206,081,820   259,867,439    53,785,620   7 HPFS/NTFS
/dev/sda4         259,867,440   312,576,704    52,709,265   5 Extended
/dev/sda5         259,867,503   310,311,539    50,444,037  83 Linux
/dev/sda6         310,311,603   312,576,704     2,265,102  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        905CA9C25CA9A406                       ntfs                                     
/dev/sda2        7A14E92E14E8EE57                       ntfs       Tanay D                       
/dev/sda3        642C42F32C42BFB2                       ntfs       Ubuntu                        
/dev/sda5        a1b4fdeb-b8df-4732-8fe0-0bd1d63eea5b   ext4                                     
/dev/sda6        05deeb45-0ab0-4e17-a974-b998313b2f46   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda5        /media/sda5              ext4       (rw)
/dev/sda3        /media/Ubuntu            fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2        /media/Tanay D           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set a1b4fdeb-b8df-4732-8fe0-0bd1d63eea5b
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set a1b4fdeb-b8df-4732-8fe0-0bd1d63eea5b
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=a1b4fdeb-b8df-4732-8fe0-0bd1d63eea5b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set a1b4fdeb-b8df-4732-8fe0-0bd1d63eea5b
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=a1b4fdeb-b8df-4732-8fe0-0bd1d63eea5b ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set a1b4fdeb-b8df-4732-8fe0-0bd1d63eea5b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a1b4fdeb-b8df-4732-8fe0-0bd1d63eea5b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set a1b4fdeb-b8df-4732-8fe0-0bd1d63eea5b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a1b4fdeb-b8df-4732-8fe0-0bd1d63eea5b ro single 
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=a1b4fdeb-b8df-4732-8fe0-0bd1d63eea5b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=05deeb45-0ab0-4e17-a974-b998313b2f46 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 133.2GB: boot/grub/core.img
 133.5GB: boot/grub/grub.cfg
 133.7GB: boot/initrd.img-2.6.31-14-generic
 134.6GB: boot/initrd.img-2.6.31-22-generic
 133.7GB: boot/vmlinuz-2.6.31-14-generic
 134.2GB: boot/vmlinuz-2.6.31-22-generic
 134.6GB: initrd.img
 133.7GB: initrd.img.old
 134.2GB: vmlinuz
 133.7GB: vmlinuz.old
```

---

### Post by tanaynet on 2011-01-25
```
Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    359M   73M  287M  21% /
udev         tmpfs    359M  272K  359M   1% /dev
/dev/sr0   iso9660    690M  690M     0 100% /cdrom
/dev/loop0
          squashfs    668M  668M     0 100% /rofs
none         tmpfs    359M  228K  359M   1% /dev/shm
tmpfs        tmpfs    359M   60K  359M   1% /tmp
none         tmpfs    359M   88K  359M   1% /var/run
none         tmpfs    359M     0  359M   0% /var/lock
none         tmpfs    359M     0  359M   0% /lib/init/rw
/dev/sda5     ext4     24G  7,3G   16G  33% /media/sda5
/dev/sda3  fuseblk     26G   22G  4,5G  83% /media/Ubuntu
/dev/sda2  fuseblk     35G   34G  320M 100% /media/Tanay D

```

---

### Post by tanaynet on 2011-01-25
upupupupupupupupupu

---

### Post by Rubi1200 on 2011-01-25
Hi,
did you look at the results?

There is a problem with your Windows installation.

Try the approaches suggested in the results and see if you get any further.

---


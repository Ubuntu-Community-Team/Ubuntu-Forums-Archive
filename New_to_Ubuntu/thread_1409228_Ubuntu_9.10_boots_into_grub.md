---
title: "Ubuntu 9.10 boots into grub"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by xylude on 2010-02-17
I am running a dual boot Ubuntu 9.10/Win7. I did an update in ubuntu (not sure what updated) and after rebooting the system went directly into Grub. When I typed 'boot' it said that no kernel was loaded. I am totally new with ubuntu/linux, but I really need to get back in there to get my MySQL dumps and files from my /home folder. Can anyone help me?

---

### Post by -kg- on 2010-02-17
> **xylude said:**
> I am running a dual boot Ubuntu 9.10/Win7. I did an update in ubuntu (not sure what updated) and after rebooting the system went directly into Grub. When I typed 'boot' it said that no kernel was loaded. I am totally new with ubuntu/linux, but I really need to get back in there to get my MySQL dumps and files from my /home folder. Can anyone help me?

When you boot into Grub you shouldn't need to type anything in.  Depending on what OS you have set as default, it will boot into that OS after a short countdown period.  If you want to boot into an OS other than the default, you use the up/down arrows to highlight that OS and press <enter>.

You can abort that countdown into the default by pressing <enter>.  You shouldn't need to type anything into GRUB unless you're editing the entries for some reason.

---

### Post by undecim on 2010-02-17
What you say that you booted into grub, do you mean you were presented with a list of OS choices, or a "sh:grub>" prompt?

If you were given the prompt, where there any messages before the prompt?

---

### Post by chaanakya_chiraag on 2010-02-17
I'm not sure about your problem, but don't worry about your files - you can always fire up a LiveCD and copy the files to a Flash Drive :)

---

### Post by presence1960 on 2010-02-17
> **xylude said:**
> I am running a dual boot Ubuntu 9.10/Win7. I did an update in ubuntu (not sure what updated) and after rebooting the system went directly into Grub. When I typed 'boot' it said that no kernel was loaded. I am totally new with ubuntu/linux, but I really need to get back in there to get my MySQL dumps and files from my /home folder. Can anyone help me?

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by xylude on 2010-02-17
Also if it helps I installed using wubi.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   488,278,015   488,071,168   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000081

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   488,278,015   488,275,968   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe2ddb14

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       1c581d1a-a739-461a-a3cf-624860847f4f   ext4                                     
/dev/sda1        DCE486D4E486B076                       ntfs       System Reserved               
/dev/sda2        F2E88906E888CA75                       ntfs                                     
/dev/sdb1        34C0A7EDC0A7B410                       ntfs       Data                          
/dev/sdc1                                               vfat       HD-CELU2                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdc1        /media/HD-CELU2          vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set f2e88906e888ca75
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic-pae root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set f2e88906e888ca75
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic-pae root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-19-generic-pae
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set dce486d4e486b076
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


  16.8GB: boot/grub/grub.cfg
  16.8GB: boot/initrd.img-2.6.31-19-generic-pae
   2.7GB: boot/vmlinuz-2.6.31-19-generic-pae
  16.8GB: initrd.img
   2.7GB: vmlinuz
=============================== StdErr Messages: ===============================

umount: /media/F2E88906E888CA75: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

---


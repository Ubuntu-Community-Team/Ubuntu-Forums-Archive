---
title: "Cannot multi-boot to XP with GRUB2"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by yuler on 2010-12-23
I've a boot CD using GRUB4DOS that successfully boots to the XP partition.  However, GRUB2 on the system will not boot to the XP partition.  

I've a better understanding how GRUB works and what the commands after scoured the manuals and various websites on the subject, but am unable to troubleshoot the problem.

Here is the bootscript:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 12880720 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         24,576     4,218,879     4,194,304   7 HPFS/NTFS
/dev/sda2               2,048        24,575        22,528  83 Linux
/dev/sda3           4,220,926   976,773,119   972,552,194   5 Extended
/dev/sda5           4,220,928    67,135,487    62,914,560  83 Linux
/dev/sda6          67,137,536   119,566,335    52,428,800  82 Linux swap / Solaris
/dev/sda7         119,568,384   329,283,583   209,715,200   7 HPFS/NTFS
/dev/sda8         329,285,632   434,143,231   104,857,600   7 HPFS/NTFS
/dev/sda9         434,145,280   643,860,479   209,715,200   7 HPFS/NTFS
/dev/sda10        643,862,528   767,057,919   123,195,392  82 Linux swap / Solaris
/dev/sda11        767,059,968   976,773,119   209,713,152   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   320,159,384   320,143,320   f W95 Ext d (LBA)
/dev/sdb5              16,128   320,159,384   320,143,257   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       ef1abebf-8af9-4642-acc8-502286785770   swap                                     
/dev/sda11       372BEC693358883C                       ntfs       backup                        
/dev/sda1        A8D4B8BCD4B88E56                       ntfs       xp                            
/dev/sda2        9dd2845c-04c4-43df-a99f-088edf6bc2c1   ext4       boot                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        9c828ded-432e-4028-b090-0659ac21aa19   ext4       ubuntu                        
/dev/sda6        6169D9721131CAB2                       ntfs       winapps                       
/dev/sda7        474FFAF25A21D641                       ntfs       audio                         
/dev/sda8        5AE3AB3457AE7051                       ntfs       general                       
/dev/sda9        77A0E81F12D7963B                       ntfs       secure                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        465C89C95C89B3E9                       ntfs       160gb                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

============================= sda2/grub/grub.cfg: =============================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 22672a0a-841e-4f93-bb46-eecda829da30
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
set locale_dir=($root)/grub/locale
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda5 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a8d4b8bcd4b88e56
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

=================== sda2: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: vmlinuz-2.6.35-22-generic

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a8d4b8bcd4b88e56
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
UUID=9c828ded-432e-4028-b090-0659ac21aa19 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=ef1abebf-8af9-4642-acc8-502286785770 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   6.5GB: boot/grub/core.img
  15.4GB: boot/grub/grub.cfg
   4.9GB: boot/initrd.img-2.6.35-22-generic
   3.1GB: boot/initrd.img-2.6.35-23-generic
   5.6GB: boot/initrd.img-2.6.35-24-generic
   6.5GB: boot/vmlinuz-2.6.35-22-generic
   6.6GB: boot/vmlinuz-2.6.35-23-generic
   6.7GB: boot/vmlinuz-2.6.35-24-generic
   5.6GB: initrd.img
   3.1GB: initrd.img.old
   6.7GB: vmlinuz
   6.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
000001b0  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 00 bc  |................|
000001c0  77 06 83 fe ff ff 02 00  00 00 00 00 c0 03 00 fe  |w...............|
000001d0  ff ff 05 fe ff ff 95 00  c0 03 6d 07 20 03 00 00  |..........m. ...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```For comparison, here is the aforementioned GRUB menu along with the system GRUB2 entry:

```

### GRUB2 system, grub.cfg, unbootable
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a8d4b8bcd4b88e56
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###



### grub4dos (GRUB) @ CD, menu.lst, bootable
title ³ Boot from Hard Drive - Windows XP (NTLDR)        ³\n
find --set-root --ignore-floppies --ignore-cd /ntldr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /ntldr
chainloader /ntldr
savedefault --wait=2

```There are other problems I'd like to tackle as seen in the GRUB2 menu, but one thing (thread) at a time.  :)

---

### Post by mikewhatever on 2010-12-23
Can you describe exactly what happens. Are there any errors? Does the Windows splash screen appears?

---

### Post by yuler on 2010-12-23
The screen goes blank, cursor blinks in upper left.

---

### Post by garvinrick4 on 2010-12-23
#What is in sda2 a linux partition that grub was loaded into at one time?
#It is a awful small partition. (an old boot partition)
#If not using just go into gparted and right click on and get rid of. Can do in live CD (ubuntu install cd use try ubuntu)
#Put in live cd. with internet connection
```
sudo apt-get lilo
``````
sudo lilo -M /dev/sda mbr
```will say error ignore.
```
sudo reboot
```Will boot into Windows.
Put cd back in and use Live Cd
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```boot into ubuntu on HDD and:
```
sudo update-grub
```

---

### Post by yuler on 2010-12-24
Thanks for the analysis and extensive suggestion.  Before I delve into it, I should clarify what my intent with sda2 was before I delete it, in case there is a way to correct it and the instructions differ.

When I first setup Ubuntu some 60 days ago, I used the LiveCD to get onto the 'net and read about installation.  After using Gparted, XP was installed on sda1, then Ubuntu on sda5.

Unfamiliar with bootloaders (specifically GRUB2), I tried to [understand the process]("http://ubuntuforums.org/showthread.php?t=1195275") and surmised it was ideal to put GRUB on it's own partition.  Why?  If I wiped out or reinstalled Ubuntu on sda5, I wanted to make sure I wasn't affecting the bootloader in sda5, so I partitioned sda2 out of the first ~10mb of sda1, then rebooted into XP to run it's disk checker.

To be honest, I don't recall how I got GRUB2 on sda2, but it may be chronicled in another thread.  I may have wiped sda5, ran the LiveCD, and selected sda2 in the install process.  Regardless, it was unsuccessful until OldFred from ubuntuforums.com prescribed a fix that got GRUB2 working from sda5.

Having read the [GRUB2 documentation]("https://help.ubuntu.com/community/Grub2") further, I now understand GRUB2 generally automates configuration from templates stored in one location, and stores the resulting config files in another, with the noted exception that one could edit the config files directly.  

The idea was to have sda2 be the location for it's config files, in the case I altered the partition (e.g. sda5) that stores it's templates.

After combing through the GRUB2 docs to [understand the commands]("http://www.gnu.org/software/grub/manual/html_node/Command_002dline-and-menu-entry-commands.html#Command_002dline-and-menu-entry-commands") in my config file, I now realize the commands are fine, which leaves the old sda2 setup suspicious.  Ergo, I have to fix the sda2 problem to fix my XP boot problem.  Does that sound about right?  

If so, how do I correct sda2 to make it GRUB2 bootable?

---

### Post by garvinrick4 on 2010-12-24
#Yes it seems as though at one time the boot was loaded into sda2 instead of sda and the boot flag is now on Windows which is fine. When installing grub via live cd boot partition had to be mounted at that time with sda5 and grub installed in sda
Somewhere that got a bit out of sorts and it seems was not mounted and grub installed in sda2. 
#Getting windows booting and then getting grub2 into mbr of sda and then running update-grub to put windows in grub2 config files which puts it in boot menu is correct idea. 
#Do not really need a dedicated boot partition. Can mount the 2 and purge grub-common grub grub-pc if choose to get rid of old files and reinstall with the new if desired.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Other wise use sda1 to boot from as in previous post.
#oldfred around here and can be contacted if like working with him?
#much success and have a Merry Christmas and happy New Year.

---

### Post by oldfred on 2010-12-24
Oldfred is still around.

I do not recommend separate /boot partitions except for those with old computers with new drives that have to have the entire boot within the first 137GB. Also servers, RAID or LVM partitioning schemes may work better for a separate /boot but that is more advanced.

Most instructions for reinstalling grub often do not mention also mounting the /boot partition or just a a little footnote - also mount /boot. So it is a little more difficult to reinstall grub with a separate /boot.

Sometimes windows just needs a refresh. garvinrick4 has you installing the lilo bootloader and seeing if windows boots. If not you may need to run windows repairs. Then follow his instructions on reinstalling grub2.

---

### Post by |Eric| on 2010-12-24
i dont know if this is solved but here is a few comments

wow that a heck of a partition table ! :P 


i would go with the comment : systems should be self contained within the same partition . 
(unless your doing a Raid or some weird stuff) 
the fact that you have 11 partition is alarming 
on a dualboot setup i would use only primarys  
there may be issues with bigger system partitions 
usualy i allow 40gb for windows and 40 for linux then i add a swap and a Data partition at the end of it 

if you want to try many install you could do more that one install 
just make shure you use the mbr for installing grub 
once grub is working you can edit menu.lst to have proper entries at bootup .

---

### Post by yuler on 2010-12-24
Thanks for the explanation, folks.  

```

sudo apt-get lilo

E: Invalid operation lilo

```

Searched for the error phrase.  Found missing parameter: "install".

```

sudo apt-get install lilo

```The LILO configuration then said:

```

It seems to be your first LILO installation. 
It is absolutely necessary to run liloconfig(8) when you complete this process and execute /sbin/lilo after this.
LILO won't work if you don't do this.   

```

The message says "and execute".  Does this mean:

[LIST=1]
[*]"run liloconfig(8), then run sbin/lilo", or
[*]"run liloconfig(8), which is the name of the program when you run sbin/lilo". Is this the same as running "sudo lilo -M /dev/sda mbr"?
[/LIST]

---

### Post by oldfred on 2010-12-24
Using lilo as a windows boot loader all we want is the part of lilo that is loaded into the MBR. That part works just like windows in searching for the partition with the boot flag and jumping to the rest of the code in the partition boot sector. 
Since we want to boot windows we will just be jumping to the windows code in the partition boot sector and do not install any additional lilo code. Ignore the additional errors.

---

### Post by yuler on 2010-12-24
Thanks, Oldfred.  This is the output of the LILO MBR routine, in case I have trouble getting back.  

```

Unpacking lilo (from .../lilo_1%3a22.8-8ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-8ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian

```

```

sudo lilo -M /dev/sda mbr

Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.

```

I'm committed now.  Rebooting...

---

### Post by yuler on 2010-12-24
After rebooting and the BIOS check, the screen went blank with a cursor in the upper left - just like when selecting XP from the GRUB2 menu.

Booted to the LiveCD, followed the instructions.  Rebooted, got the GRUB2 menu.  Selected XP.  Screen went blank, cursor in upper left.

Rebooted to Ubuntu 10.10 from the hard drive.  At least I'm back.  :)

I don't know if anything has changed, but here's the bootscript result:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 12880720 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         24,576     4,218,879     4,194,304   7 HPFS/NTFS
/dev/sda2               2,048        24,575        22,528  83 Linux
/dev/sda3           4,220,926   976,773,119   972,552,194   5 Extended
/dev/sda5           4,220,928    67,135,487    62,914,560  83 Linux
/dev/sda6          67,137,536   119,566,335    52,428,800  82 Linux swap / Solaris
/dev/sda7         119,568,384   329,283,583   209,715,200   7 HPFS/NTFS
/dev/sda8         329,285,632   434,143,231   104,857,600   7 HPFS/NTFS
/dev/sda9         434,145,280   643,860,479   209,715,200   7 HPFS/NTFS
/dev/sda10        643,862,528   767,057,919   123,195,392  82 Linux swap / Solaris
/dev/sda11        767,059,968   976,773,119   209,713,152   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   320,159,384   320,143,320   f W95 Ext d (LBA)
/dev/sdb5              16,128   320,159,384   320,143,257   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       ef1abebf-8af9-4642-acc8-502286785770   swap                                     
/dev/sda11       372BEC693358883C                       ntfs       backup                        
/dev/sda1        A8D4B8BCD4B88E56                       ntfs       xp                            
/dev/sda2        9dd2845c-04c4-43df-a99f-088edf6bc2c1   ext4       boot                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        9c828ded-432e-4028-b090-0659ac21aa19   ext4       ubuntu                        
/dev/sda6        6169D9721131CAB2                       ntfs       winapps                       
/dev/sda7        474FFAF25A21D641                       ntfs       audio                         
/dev/sda8        5AE3AB3457AE7051                       ntfs       general                       
/dev/sda9        77A0E81F12D7963B                       ntfs       secure                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        465C89C95C89B3E9                       ntfs       160gb                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

============================= sda2/grub/grub.cfg: =============================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 22672a0a-841e-4f93-bb46-eecda829da30
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
set locale_dir=($root)/grub/locale
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda5 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a8d4b8bcd4b88e56
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

=================== sda2: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: vmlinuz-2.6.35-22-generic

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a8d4b8bcd4b88e56
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
UUID=9c828ded-432e-4028-b090-0659ac21aa19 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=ef1abebf-8af9-4642-acc8-502286785770 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   6.5GB: boot/grub/core.img
  13.3GB: boot/grub/grub.cfg
   4.9GB: boot/initrd.img-2.6.35-22-generic
   3.1GB: boot/initrd.img-2.6.35-23-generic
   5.6GB: boot/initrd.img-2.6.35-24-generic
   6.5GB: boot/vmlinuz-2.6.35-22-generic
   6.6GB: boot/vmlinuz-2.6.35-23-generic
   6.7GB: boot/vmlinuz-2.6.35-24-generic
   5.6GB: initrd.img
   3.1GB: initrd.img.old
   6.7GB: vmlinuz
   6.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
000001b0  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 00 bc  |................|
000001c0  77 06 83 fe ff ff 02 00  00 00 00 00 c0 03 00 fe  |w...............|
000001d0  ff ff 05 fe ff ff 95 00  c0 03 6d 07 20 03 00 00  |..........m. ...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by oldfred on 2010-12-25
I think all we proved was that it is not a grub issue, but a windows issue. Direct booting of windows gives the same error.

I would first try running chkdsk on the windows partition.

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If that does not work we can try all the windows fix commands. But do just the chkdsk as that has worked for some.

Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

A discussion about the Bootcfg command and its uses fix boot.ini
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

---

### Post by yuler on 2010-12-25
I tried all those Windows commands except for "FIXMBR  C:"  because I did not want to overwrite the MBR.   None of them fixed the problem.  

It's odd I can boot to XP from the GRUB4DOS CD, whose menu entry is listed in the first post, but not the system GRUB2.  There must be an overriding parameter.

Is it about time for an XP re-install, followed by a GRUB2 re-install?  Or are there other things I can try?  :)

---

### Post by oldfred on 2010-12-25
I have had my XP boot but not work in gparted. But after running chkdsk then gparted saw it. Did you run chkdsk until there were no errors?

If you ran all the windows fix commands I would think it should have everything it needs. All grub does is jump to the partition boot sector just like windows would. Not sure what else grub4dos would do as it is just a windows version of grub.

You could add to 40_custom a simple chainload entry and see if that works.
gksudo gedit /etc/grub.d/40_custom

# Chainload another bootloader
menuentry "Chainload partition sda1" {
set root=(hd0,1)
chainloader +1
}

then:
sudo update-grub

---

### Post by yuler on 2010-12-25
Thanks for taking a moment, especially on this holiday.  Sad to say, even those instructions did not work - no errors with  chkdsk /r, new chainload entry went to the blank screen with the cursor in the upper left corner.  

Quite the dilemma, isn't it?

---

### Post by oldfred on 2010-12-25
Your partition table still says windows is sda1, but it starts at sector 24576. Your linux boot starts at 2048, which is even the new formating. Windows XP & older Linux always used to start at sector 63. You can boot windows from any primary partition but I am wondering if there still is some confusion in the partition table vs. the NTFS boot sector which also has to have the correct start & end positions of the sector.

I saw where Herman tested booting XP from 2048 without any problem, so I am not sure if that is the issue or not.

I might try using testdisk to rebuild the boot sector. It has both a recover from a backup and a rebuild hidden somewhere. I have not used it so I do not know details but it is in the instructions.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I had this in my notes for someone with Vista and the XP/Vista boot sectors are somehow different, but I would think testdisk would know the difference.

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"

then press "q" a few times to quit testdisk, reboot and see whether you can boot into Vista.

---

### Post by yuler on 2010-12-25
By golly, you solved it!  Testdisk reported inconsistencies with the boot sector, and the Boot Sector Rebuild option fixed it.  Both entries in GRUB2 (XP, chainload) work.

Thank you, Oldfred!

---

### Post by oldfred on 2010-12-25
Glad that one worked, I was running out of suggestions.:)

---


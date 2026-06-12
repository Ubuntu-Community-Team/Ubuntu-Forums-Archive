---
title: "Adding Win 7 install to GRUB2 Gives &quot;BOOTMGR not found&quot;"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by Aetherith on 2011-03-24
I recently threw a second HDD into my laptop because I was tired of Windows misbehaving and installed Windows 7 on it.  Now on my original drive I have a happy dual boot of Windows 7 and Ubuntu 10.10 both of which still boot just fine from GRUB2.  What I would like to do is add the new Windows 7 install, residing on /dev/sdb1 (dev starts counting partitions from 1 not 0 right?) to the GRUB menu.  I've tried copying the entry used to load Windows on sda and tweaking the settings to what I think they should be but I've had no success.  When I select the option to boot the second Windows install I get a "BOOTMGR not found"  error.  I've cruised the forums and tried some solutions (os-prober only finds the Windows install on sda) but have had no luck.  Below is my GRUB entry for the second Windows install just in case that will be useful.

```
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    drivemap -s hd0 hd1
    search --no-floppy --fs-uuid --set 46245AD6245AC897
    chainloader +1
}
```

Suggestions?  Thank you.

---

### Post by oldfred on 2011-03-24
When you installed the second windows did you have the first windows installed. Windows always combines the boots to the first install with the boot flag (active partition). It literally moves the boot files from the second install to the first.

To see where everything is at.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Aetherith on 2011-03-24
Yes Windows install 1 (the one that will still boot) existed before Windows install 2.  Here is the output of that script.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   529,807,707   499,005,788   7 HPFS/NTFS
/dev/sda4         529,809,406   976,773,119   446,963,714   5 Extended
/dev/sda5         529,809,408   958,570,495   428,761,088  83 Linux
/dev/sda6         958,572,544   976,773,119    18,200,576  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C4F1-50E9                              vfat                                     
/dev/sda2        3230F62530F5F029                       ntfs       RECOVERY                      
/dev/sda3        9604FB7C04FB5E25                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        00214275-af62-434f-8981-cabd1d74707c   ext4                                     
/dev/sda6        26dc69d0-42fa-41e3-99a4-69babc3d6edd   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        46245AD6245AC897                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


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
search --no-floppy --fs-uuid --set 00214275-af62-434f-8981-cabd1d74707c
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 00214275-af62-434f-8981-cabd1d74707c
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 00214275-af62-434f-8981-cabd1d74707c
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=00214275-af62-434f-8981-cabd1d74707c ro  splash vga=791  quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 00214275-af62-434f-8981-cabd1d74707c
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=00214275-af62-434f-8981-cabd1d74707c ro single  splash vga=791
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 00214275-af62-434f-8981-cabd1d74707c
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=00214275-af62-434f-8981-cabd1d74707c ro  splash vga=791  quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 00214275-af62-434f-8981-cabd1d74707c
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=00214275-af62-434f-8981-cabd1d74707c ro single  splash vga=791
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 00214275-af62-434f-8981-cabd1d74707c
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=00214275-af62-434f-8981-cabd1d74707c ro  splash vga=791  quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 00214275-af62-434f-8981-cabd1d74707c
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=00214275-af62-434f-8981-cabd1d74707c ro single  splash vga=791
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 00214275-af62-434f-8981-cabd1d74707c
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=00214275-af62-434f-8981-cabd1d74707c ro  splash vga=791  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 00214275-af62-434f-8981-cabd1d74707c
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=00214275-af62-434f-8981-cabd1d74707c ro single  splash vga=791
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 00214275-af62-434f-8981-cabd1d74707c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 00214275-af62-434f-8981-cabd1d74707c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 3230f62530f5f029
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    #insmod part_msdos
    #insmod ntfs
    #set root='(hd1,msdos1)'
    #devicemap -s hd0 hd1
    #search --no-floppy --fs-uuid --set 46245AD6245AC897
    #chainloader +1

    ##Try something new
    devicemap -s hd0 hd1
    chainloader (hd1)+1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=00214275-af62-434f-8981-cabd1d74707c    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda3 :
UUID=9604FB7C04FB5E25    /media/OS    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda6 :
UUID=26dc69d0-42fa-41e3-99a4-69babc3d6edd    none    swap    sw    0    0



=================== sda5: Location of files loaded by Grub: ===================


 441.0GB: boot/grub/core.img
 413.5GB: boot/grub/grub.cfg
 285.7GB: boot/initrd.img-2.6.35-24-generic
 431.1GB: boot/initrd.img-2.6.35-25-generic
 437.7GB: boot/initrd.img-2.6.35-27-generic
 351.0GB: boot/initrd.img-2.6.35-28-generic
 441.2GB: boot/vmlinuz-2.6.35-24-generic
 441.2GB: boot/vmlinuz-2.6.35-25-generic
 441.4GB: boot/vmlinuz-2.6.35-27-generic
 441.4GB: boot/vmlinuz-2.6.35-28-generic
 351.0GB: initrd.img
 437.7GB: initrd.img.old
 441.4GB: vmlinuz
 441.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 60 8e 19 00 fe  |...........`....|
000001d0  ff ff 05 fe ff ff 02 60  8e 19 00 c0 15 01 00 00  |.......`........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2011-03-24
Windows needs three files to boot. 
These two often are installed in a separate boot partition. The standard install of windows creates a 100MB boot/recovery partition,
/bootmgr /Boot/BCD
Your main install or c: normally has this as part of all the windows files in /windows etc.
 /Windows/System32/winload.exe

Script only found one bootable partition and one with the main install. Did script miss the other install?

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by Aetherith on 2011-03-24
Ok I know for a fact that Windows Install 1 is on sda2 and that Windows Install 2 is on sdb1 (as that is the only partition on sdb).  It seems like the script detects this. (sda2 and sdb1 both have Boot marked)

Now the script detects the presence of /bootmgr and /Boot/BCD on sda2 and the presence of /Windows/System32/winload.exe on sdb1.  I seem to have a dead split of the files I need.

I am confused as to what you are suggesting I do.  It seems like my boot files have been moved from where they need to be in the 2nd install into the first, but I am unsure of how to fix that.  Do you mean I should use gparted to wipe sdb1, then set its boot flag, then reinstall Windows to it so that it believes it is installing standalone?

---

### Post by oldfred on 2011-03-25
You should not have to reinstall. You may just need to run repairs on the install in sdb. You can literally copy bootmgr, and maybe the BCD. The BCD is a hive like the windows registry but just has info on where the system is. You may be able to copy the BCD and then edit it with BCDEdit or download and use neogrubs easyBCD.

Does your install in sda2 have the full set of windows system files and the boot script did not see them for some reason. Boot flag is just used by the windows boot loader to know which partition to jump to. That is just the start of booting. Win7 installs with the separate 100MB boot/recovery partition have the boot flag on the 100MB partition. Grub does not use the boot flag.

[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---


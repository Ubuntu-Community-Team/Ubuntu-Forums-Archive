---
title: "Ubuntu 10.04 Not booting Properly"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by thewhiteeye on 2011-05-14
Hello People,
   I am facing an issue here. I have Ubuntu 10.04 installed on my machine. Recently due to power failure, my machine is not booting up properly. When I boot into ubuntu( I have dual boot XP & Ubuntu), A long data sheet scrolls and at the end the following comes

[B]Target filesystem doesn't have /sbin/init
No init found. Try passing init= bootarg


BusyBox v1.13.3 (Ubuntu 1:1.13.1-1ubuntu11) built-in shell (ash)

Enter 'help' for a list of built-in commands.

(initramfs) [/B]

 and the cursor blinks here.


  I have important data in this machine. Please help me with this issue.

If anyone can help me recover the data, that would be helpful, as it is a kind of urgent

Thanx in advance.

---

### Post by Rubi1200 on 2011-05-14
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by jtarin on 2011-05-14
You can also use the Live CD to CHROOT into your install and move your files to another drive or backup medium.

---

### Post by Hedgehog1 on 2011-05-14
+1 on posting the results from the boot_info_script script.



***The Hedge***

:KS

---

### Post by thewhiteeye on 2011-05-21
Here is the results of the boot info scripts: RESULTS.txt




```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 11 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Red Hat Enterprise Linux Server 
                       release 5.1 (Tikanga) Kernel on an
    Boot files:        /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 NTFS / exFAT / HPFS
/dev/sda2          40,965,811   312,498,175   271,532,365   f W95 Extended (LBA)
/dev/sda5          40,965,813    61,448,624    20,482,812   7 NTFS / exFAT / HPFS
/dev/sda6          61,448,688    62,476,784     1,028,097  83 Linux
/dev/sda7          62,476,848    82,959,659    20,482,812  83 Linux
/dev/sda8          82,959,723   103,442,534    20,482,812  83 Linux
/dev/sda9         103,442,598   113,675,939    10,233,342  83 Linux
/dev/sda10        113,676,003   121,869,089     8,193,087  82 Linux swap / Solaris
/dev/sda11        121,870,336   304,656,383   182,786,048  83 Linux
/dev/sda12        304,658,432   312,498,175     7,839,744  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FA2467C024677E8F                       ntfs       
/dev/sda10                                              swap       SWAP-sda10
/dev/sda11       89cac23d-a9e0-4377-a551-7e6ae213abac   ext4       
/dev/sda12       d1066f6a-41b0-4ea8-8eec-901fc605eeee   swap       
/dev/sda5        20E43E07E43DDFA8                       ntfs       
/dev/sda6        5fa9528a-5840-45a6-8f13-dc2a5e5acc6b   ext3       /boot1
/dev/sda7        18e044db-56f8-4d44-8890-8e4ebda85faa   ext3       /usr
/dev/sda8        d823c1dc-bafd-4bca-8d3c-71912c3351b6   ext3       /
/dev/sda9        3e9e37e5-177b-4254-af5c-5433c702e8a3   ext3       /home

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

============================= sda6/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,5)
#          kernel /vmlinuz-version ro root=/dev/sda8
#          initrd /initrd-version.img
#boot=/dev/sda
default=1
timeout=5
splashimage=(hd0,5)/grub/splash.xpm.gz
hiddenmenu
title Red Hat Enterprise Linux Server (2.6.18-8.el5xen)
    root (hd0,5)
    kernel /xen.gz-2.6.18-8.el5
    module /vmlinuz-2.6.18-8.el5xen ro root=LABEL=/ rhgb quiet
    module /initrd-2.6.18-8.el5xen.img
title Red Hat Enterprise Linux Server (2.6.18-53.el5)
    root (hd0,5)
    kernel /vmlinuz-2.6.18-53.el5 ro root=LABEL=/ rhgb quiet
    initrd /initrd-2.6.18-53.el5.img
title Other
    rootnoverify (hd0,0)
    chainloader +1
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  29.370851517 = 31.536711680   grub/grub.conf                                 1
  29.370851517 = 31.536711680   grub/menu.lst                                  1
  29.368500710 = 31.534187520   grub/stage2                                    2
  29.330353737 = 31.493227520   initrd-2.6.18-53.el5.img                      10
  29.336009979 = 31.499300864   initrd-2.6.18-8.el5xen.img                    11
  29.334205627 = 31.497363456   vmlinuz-2.6.18-53.el5                          8
  29.327843666 = 31.490532352   vmlinuz-2.6.18-8.el5xen                        9

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
LABEL=/                 /                       ext3    defaults        1 1
LABEL=/home             /home                   ext3    defaults        1 2
LABEL=/usr              /usr                    ext3    defaults        1 2
LABEL=/boot1            /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
LABEL=SWAP-sda10        swap                    swap    defaults        0 0
--------------------------------------------------------------------------------

========================== sda11/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,11)'
search --no-floppy --fs-uuid --set 89cac23d-a9e0-4377-a551-7e6ae213abac
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
set root='(hd0,11)'
search --no-floppy --fs-uuid --set 89cac23d-a9e0-4377-a551-7e6ae213abac
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 89cac23d-a9e0-4377-a551-7e6ae213abac
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=89cac23d-a9e0-4377-a551-7e6ae213abac ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 89cac23d-a9e0-4377-a551-7e6ae213abac
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=89cac23d-a9e0-4377-a551-7e6ae213abac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 89cac23d-a9e0-4377-a551-7e6ae213abac
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=89cac23d-a9e0-4377-a551-7e6ae213abac ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 89cac23d-a9e0-4377-a551-7e6ae213abac
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=89cac23d-a9e0-4377-a551-7e6ae213abac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 89cac23d-a9e0-4377-a551-7e6ae213abac
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=89cac23d-a9e0-4377-a551-7e6ae213abac ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 89cac23d-a9e0-4377-a551-7e6ae213abac
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=89cac23d-a9e0-4377-a551-7e6ae213abac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 89cac23d-a9e0-4377-a551-7e6ae213abac
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=89cac23d-a9e0-4377-a551-7e6ae213abac ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 89cac23d-a9e0-4377-a551-7e6ae213abac
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=89cac23d-a9e0-4377-a551-7e6ae213abac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 89cac23d-a9e0-4377-a551-7e6ae213abac
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=89cac23d-a9e0-4377-a551-7e6ae213abac ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 89cac23d-a9e0-4377-a551-7e6ae213abac
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=89cac23d-a9e0-4377-a551-7e6ae213abac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 89cac23d-a9e0-4377-a551-7e6ae213abac
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 89cac23d-a9e0-4377-a551-7e6ae213abac
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fa2467c024677e8f
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda11/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=89cac23d-a9e0-4377-a551-7e6ae213abac /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda12 during installation
UUID=d1066f6a-41b0-4ea8-8eec-901fc605eeee none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda11: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 106.248073578 = 114.083000320  boot/grub/core.img                             1
  74.589595795 = 80.089968640   boot/grub/grub.cfg                             1
 106.264556885 = 114.100699136  boot/initrd.img-2.6.32-21-generic              1
 108.235141754 = 116.216598528  boot/initrd.img-2.6.32-24-generic              1
 108.181900024 = 116.159430656  boot/initrd.img-2.6.32-25-generic              1
 108.189323425 = 116.167401472  boot/initrd.img-2.6.32-26-generic              1
 110.159744263 = 118.283124736  boot/initrd.img-2.6.32-27-generic              1
 106.243495941 = 114.078085120  boot/vmlinuz-2.6.32-21-generic                 1
 108.226196289 = 116.206993408  boot/vmlinuz-2.6.32-24-generic                 1
 108.174480438 = 116.151463936  boot/vmlinuz-2.6.32-25-generic                 1
 108.218776703 = 116.199026688  boot/vmlinuz-2.6.32-26-generic                 1
 108.193084717 = 116.171440128  boot/vmlinuz-2.6.32-27-generic                 1
 110.159744263 = 118.283124736  initrd.img                                     1
 108.189323425 = 116.167401472  initrd.img.old                                 1
 108.193084717 = 116.171440128  vmlinuz                                        1
 108.218776703 = 116.199026688  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda10

00000000  00 78 30 30 00 78 30 30  00 78 30 30 00 78 30 30  |.x00.x00.x00.x00|
*
00000200
```

---

### Post by Rubi1200 on 2011-05-21
A quick look at the results doesn't suggest anything immediately wrong.

Have you tried booting into either recovery mode or an older kernel? Does the problem still exist when you do?

The other thing to try is this:
When the computer starts highlight the first entry for Ubuntu and press "c" to drop to a grub> prompt.

Type the following commands and Enter after each one:

 
```
set prefix=(hd0,11)/boot/grub
set root=(hd0,11)
insmod linux
linux /vmlinuz root=/dev/sda11 ro
initrd /initrd.img 
boot
```If this gets you booted, run```
 sudo update-grub
``` in the terminal and hopefully the issue will be resolved.

If not, at least use a LiveCD to rescue the important data before anything else.

---

### Post by thewhiteeye on 2011-05-21
Dear Rubi1200,
   I did what you suggested. It worked like a charm. Thank you very much.

I had also tried booting through live CD and trying to backup the data. But it would not let me do it. It would not let me open the /home partition. Can anyone suggest what to do in that case.

Thanks again.

---

### Post by Rubi1200 on 2011-05-21
Excellent! I am really pleased this worked for you :-)

You ran the update-grub command back in Ubuntu right? That is what I meant of course. And you can now restart etc. and boot into Ubuntu normally?

If yes, great.

Is your /home partition encrypted or did you change the permissions for it?

That could explain what happened.

In any event, if you believe the problem has been resolved, please mark this Solved using the Thread Tools near the top of the page.

---

### Post by thewhiteeye on 2011-05-21
Dear Rubi1200,
    Well now booting through the Live CD, it does give me access to my data in the home folder.
 
 Earlier, what I had done was that i booted using ubuntu 10.10 live CD. But when I booted through 10.04, I was successful.

And I did run the update-grub command. And I can boot in to Ubuntu normally.

---


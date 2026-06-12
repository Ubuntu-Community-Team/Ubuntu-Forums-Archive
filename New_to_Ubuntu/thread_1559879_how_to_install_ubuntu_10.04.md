---
title: "how to install ubuntu 10.04"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by adi2huh on 2010-08-24
[SIZE=7]:D:D:D  hey, please anybody help me upgrade my 9.10 to Ubuntu 10.04??[/SIZE]
[SIZE=7]also i wan't to know the procedure of freshly installing it with windows........ thanks![/SIZE]

---

### Post by kaldor on 2010-08-24
Hey there,

A word of advice from me (and many others) is to NOT upgrade an existing Ubuntu install, but back up your files and do a clean installation.

To dual boot with Windows, you do it the same way as you did with 9.10.

Back ups are a must! Anything could go wrong ;)

This link may help:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Scroll down to "Install Ubuntu after Windows" and have a read.

Enjoy :)

---

### Post by Rubi1200 on 2010-08-24
> **kaldor said:**
> Hey there,

A word of advice from me (and many others) is to NOT upgrade an existing Ubuntu install, but back up your files and do a clean installation.

To dual boot with Windows, you do it the same way as you did with 9.10.

Back ups are a must! Anything could go wrong ;)
Enjoy :)
+1
Not much to add; this is great advice and you will not go wrong following it.

Good luck!

---

### Post by adi2huh on 2010-08-24
But, I hav already 3 of windows versions and 2 of Ubuntu releases on my System!
Then I u suggested, if I prefer a clean installation then many things may go wrong with all other installed O.S.!
IS THAT REALLY SO RISKY TO UPGRADE OLDER VERSION???? I MEAN WAT KIND OF PROBLEMS R HAPPENING WITH OTHERS WHO HAD UPGRADED IT????

---

### Post by Rubi1200 on 2010-08-24
> **adi2huh said:**
> But, I hav already 3 of windows versions and 2 of Ubuntu releases on my System!
Then I u suggested, if I prefer a clean installation then many things may go wrong with all other installed O.S.!
IS THAT REALLY SO RISKY TO UPGRADE OLDER VERSION???? I MEAN WAT KIND OF PROBLEMS R HAPPENING WITH OTHERS WHO HAD UPGRADED IT????

In order for us to get a better view of your setup, I suggest you post either a screenshot of your partitions from the LiveCD (using GParted) or post the results of the bootscript (link at the bottom of my post).

---

### Post by julio_cortez on 2010-08-24
> **adi2huh said:**
> I MEAN WAT KIND OF PROBLEMS R HAPPENING WITH OTHERS WHO HAD UPGRADED IT????
Broken fglrx driver, for example. Thanks Heaven I knew what to do to get it running again, but before finding out that I was aware of what to do there has been a moment of pain..
Once restarted the system and logged into Kubuntu, however, I noticed that some little things weren't supposed to be like they were, so I went for the reinstall.

> **adi2huh said:**
> Then I u suggested, if I prefer a clean installation then many things  may go wrong with all other installed O.S.!
I don't know what it is your case but I re-installed Linux twice (first, reinstall of Kubuntu 10.04 after the upgrade from 9.10 I told before.. Then replacement of Kubuntu with Ubuntu last week) on a dual boot with Windows 7 and both the times things went flawlessly..

---

### Post by linux-hack on 2010-08-24
> **kaldor said:**
> Hey there,

A word of advice from me (and many others) is to NOT upgrade an existing Ubuntu install, but back up your files and do a clean installation.

To dual boot with Windows, you do it the same way as you did with 9.10.

Back ups are a must! Anything could go wrong ;)

This link may help:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Scroll down to "Install Ubuntu after Windows" and have a read.

Enjoy :)

+2 It is the best way to change to a new system . ;)

---

### Post by kaldor on 2010-08-24
You've got your comp loaded :)

I view upgrades as a server-only feature. It went very smooth on my personal backup box. 

But for desktop users, I think Shuttleworth is smoking too much crack if he is recommending upgrades ;)

---

### Post by adi2huh on 2010-08-24
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004e6c7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     66,075,345   275,787,854   209,712,510   7 HPFS/NTFS
/dev/sda2         275,787,855 1,953,520,064 1,677,732,210   5 Extended
/dev/sda5         275,787,918   695,212,874   419,424,957   7 HPFS/NTFS
/dev/sda6         695,212,938 1,114,653,959   419,441,022   7 HPFS/NTFS
/dev/sda7       1,114,654,023 1,534,078,979   419,424,957   7 HPFS/NTFS
/dev/sda8       1,534,079,043 1,953,520,064   419,441,022   7 HPFS/NTFS
/dev/sda3                  63     4,000,184     4,000,122  82 Linux swap / Solaris
/dev/sda4           4,000,185    66,075,344    62,075,160  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08140813

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *     27,262,305    71,296,469    44,034,165   7 HPFS/NTFS
/dev/sdb2                  63     2,104,514     2,104,452  82 Linux swap / Solaris
/dev/sdb3           2,104,515    27,262,304    25,157,790  83 Linux
/dev/sdb4          71,296,470   312,576,704   241,280,235   5 Extended
/dev/sdb5          71,296,533   197,133,614   125,837,082   7 HPFS/NTFS
/dev/sdb6         197,133,678   312,576,704   115,443,027   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        394EC10B694C1649                       ntfs       Windows 7 O.S                 
/dev/sda3        93f35946-de86-4639-ba61-b69b09caa496   swap                                     
/dev/sda4        6893f4d2-cecb-4ea8-848f-821a84a0560a   ext4                                     
/dev/sda5        240636666758AE4C                       ntfs       Softwares                     
/dev/sda6        3F70E58B50AA3F8E                       ntfs       Games                         
/dev/sda7        49B3ABE3302775EF                       ntfs       Multimedia                    
/dev/sda8        533F89A90E9C8B99                       ntfs       Logical Study                 
/dev/sdb1        14901DCA901DB36A                       ntfs                                     
/dev/sdb2        6cf2b7d5-87b3-4724-8cdc-70c839c0773c   swap                                     
/dev/sdb3        02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b   ext4                                     
/dev/sdb5        28F8E202277C6D69                       ntfs                                     
/dev/sdb6        7586DFA11BECE63E                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/sda1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/sda5              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /media/sda6              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7        /media/sda7              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8        /media/sda8              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/sdb1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb3        /media/sdb3              ext4       (rw)
/dev/sdb5        /media/sdb5              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb6        /media/sdb6              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda4/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=6893f4d2-cecb-4ea8-848f-821a84a0560a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6893f4d2-cecb-4ea8-848f-821a84a0560a

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        6893f4d2-cecb-4ea8-848f-821a84a0560a
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=6893f4d2-cecb-4ea8-848f-821a84a0560a ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        6893f4d2-cecb-4ea8-848f-821a84a0560a
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=6893f4d2-cecb-4ea8-848f-821a84a0560a ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        6893f4d2-cecb-4ea8-848f-821a84a0560a
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=6893f4d2-cecb-4ea8-848f-821a84a0560a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        6893f4d2-cecb-4ea8-848f-821a84a0560a
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=6893f4d2-cecb-4ea8-848f-821a84a0560a ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.28-14-generic
uuid        6893f4d2-cecb-4ea8-848f-821a84a0560a
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=6893f4d2-cecb-4ea8-848f-821a84a0560a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode)
uuid        6893f4d2-cecb-4ea8-848f-821a84a0560a
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=6893f4d2-cecb-4ea8-848f-821a84a0560a ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.10, kernel 2.6.28-13-generic
uuid        6893f4d2-cecb-4ea8-848f-821a84a0560a
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=6893f4d2-cecb-4ea8-848f-821a84a0560a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.10, kernel 2.6.28-13-generic (recovery mode)
uuid        6893f4d2-cecb-4ea8-848f-821a84a0560a
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=6893f4d2-cecb-4ea8-848f-821a84a0560a ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Chainload into GRUB 2
root        6893f4d2-cecb-4ea8-848f-821a84a0560a
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        6893f4d2-cecb-4ea8-848f-821a84a0560a
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root=(hd0,4)
search --no-floppy --fs-uuid --set 6893f4d2-cecb-4ea8-848f-821a84a0560a
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 6893f4d2-cecb-4ea8-848f-821a84a0560a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6893f4d2-cecb-4ea8-848f-821a84a0560a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 6893f4d2-cecb-4ea8-848f-821a84a0560a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6893f4d2-cecb-4ea8-848f-821a84a0560a ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 394ec10b694c1649
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sdb3)" {
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sdb3)" {
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro single
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sdb3)" {
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sdb3)" {
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (on /dev/sdb3)" {
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode) (on /dev/sdb3)" {
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro single
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-14-generic (on /dev/sdb3)" {
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro quiet splash
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode) (on /dev/sdb3)" {
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro single
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-13-generic (on /dev/sdb3)" {
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro quiet splash
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-13-generic (recovery mode) (on /dev/sdb3)" {
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro single
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Chainload into GRUB 2 (on /dev/sdb3)" {
    linux /boot/grub/core.img 
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sdb3)" {
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults               0  0  
# / was on /dev/sda4 during installation
UUID=6893f4d2-cecb-4ea8-848f-821a84a0560a  /              ext4         errors=remount-ro      0  1  
# swap was on /dev/sda3 during installation
UUID=93f35946-de86-4639-ba61-b69b09caa496  none           swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/sda1                                  /media/sda1    ntfs         force                  0  0  
/dev/sda5                                  /media/sda5    ntfs         force                  0  0  
/dev/sda6                                  /media/sda6    ntfs         force                  0  0  
/dev/sda7                                  /media/sda7    ntfs         force                  0  0  
/dev/sda8                                  /media/sda8    ntfs         force                  0  0  
/dev/sdb2                                  /media/sdb2    swap         defaults               0  0  
/dev/sdb1                                  /media/sdb1    ntfs         force                  0  0  
/dev/sdb3                                  /media/sdb3    ext4         defaults               0  0  
/dev/sdb5                                  /media/sdb5    ntfs         force                  0  0  
/dev/sdb6                                  /media/sdb6    ntfs         force                  0  0  

=================== sda4: Location of files loaded by Grub: ===================


  10.5GB: boot/grub/core.img
  10.6GB: boot/grub/grub.cfg
   3.8GB: boot/grub/menu.lst
   3.8GB: boot/initrd.img-2.6.28-13-generic
   3.8GB: boot/initrd.img-2.6.28-14-generic
   3.8GB: boot/initrd.img-2.6.28-16-generic
   3.8GB: boot/initrd.img-2.6.31-14-generic
   2.8GB: boot/vmlinuz-2.6.28-13-generic
   2.9GB: boot/vmlinuz-2.6.28-14-generic
   3.0GB: boot/vmlinuz-2.6.28-16-generic
   2.6GB: boot/vmlinuz-2.6.31-14-generic
   3.8GB: initrd.img
   3.8GB: initrd.img.old
   3.0GB: vmlinuz
   2.9GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sdb3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.28-14-generic
uuid        02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode)
uuid        02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.10, kernel 2.6.28-13-generic
uuid        02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.10, kernel 2.6.28-13-generic (recovery mode)
uuid        02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Chainload into GRUB 2
root        02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root=(hd0,3)
search --no-floppy --fs-uuid --set 02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 14901dca901db36a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults               0  0  
# / was on /dev/sda3 during installation
UUID=02b98aa1-78c8-4f6d-8ab3-4bd80b031f5b  /              ext4         errors=remount-ro      0  1  
# swap was on /dev/sda2 during installation
UUID=6cf2b7d5-87b3-4724-8cdc-70c839c0773c  none           swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/sda1                                  /media/sda1    ntfs         force                  0  0  
/dev/sda5                                  /media/sda5    ntfs         force                  0  0  
/dev/sda6                                  /media/sda6    ntfs         force                  0  0  

=================== sdb3: Location of files loaded by Grub: ===================


   3.4GB: boot/grub/core.img
   3.4GB: boot/grub/grub.cfg
   9.6GB: boot/grub/menu.lst
  10.9GB: boot/initrd.img-2.6.28-13-generic
  10.9GB: boot/initrd.img-2.6.28-14-generic
  13.9GB: boot/initrd.img-2.6.28-16-generic
  10.9GB: boot/initrd.img-2.6.31-14-generic
   5.4GB: boot/initrd.img-2.6.31-17-generic
   9.8GB: boot/vmlinuz-2.6.28-13-generic
   9.9GB: boot/vmlinuz-2.6.28-14-generic
   9.9GB: boot/vmlinuz-2.6.28-16-generic
   3.2GB: boot/vmlinuz-2.6.31-14-generic
   9.8GB: boot/vmlinuz-2.6.31-17-generic
   5.4GB: initrd.img
  13.9GB: initrd.img.old
   9.8GB: vmlinuz
   9.9GB: vmlinuz.old

---


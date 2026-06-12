---
title: "grub question"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by davy51 on 2010-09-02
To begin with I am relatively new to linux
I have tried ubuntu before but never stuck with it but now have decided to make it work and get rid of windows

Ok my problem is grub doesnt show on startup

I tried the live cd to install it but it wouldnt install
So I installed it within my installed ubuntu 10.04

It shows being installed and when checked from inside the os it shows both my os,s in a dual boot

At startup I have tried clicking escape,shift and C nothing happens it doesnt so 
I have read and followed the directions for grub on the net but nothing seems to work still no grub showing

When I check the grub folder it does show menu.lst and also a backup for it

I have read it is hidden by default so I need to know how to make it default show at startup

Thanks for all replies ahead of time

---

### Post by wilbbe01 on 2010-09-02
> **davy51 said:**
> To begin with I am relatively new to linux
I have tried ubuntu before but never stuck with it but now have decided to make it work and get rid of windows

Ok my problem is grub doesnt show on startup

I tried the live cd to install it but it wouldnt install
So I installed it within my installed ubuntu 10.04

It shows being installed and when checked from inside the os it shows both my os,s in a dual boot

At startup I have tried clicking escape,shift and C nothing happens it doesnt so 
I have read and followed the directions for grub on the net but nothing seems to work still no grub showing

When I check the grub folder it does show menu.lst and also a backup for it

I have read it is hidden by default so I need to know how to make it default show at startup

Thanks for all replies ahead of time

It's been a while but it sounds an awful lot like you might have multiple drives or something, and Grub may be on one which you're not telling your computer to boot off of.  Did you check in the bios to see for sure?  Or don't you have multiple drives which could be causing this?

---

### Post by wojox on 2010-09-02
What version are you using? Lucid doesn't have a menu.lst.

---

### Post by davy51 on 2010-09-02
I do have two seperate drives one has ubuntu 10.04 on the main drive and fedora on the slave drive
In bios I am booting to the main drive
But when I switch bios to boot to the slave drive it automaticly boots to fedora without a grub also

Grub 2 from what I have read gives a menu.lst   when installed I could be wrong

---

### Post by oldfred on 2010-09-03
Grub legacy 0.97 uses menu.lst. Grub2 uses grub.cfg which you do not directly edit but edit other files and run sudo update-grub to rewrite grub.cfg.

To see where everything is at:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by davy51 on 2010-09-03
ok this is what I got

```

```                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 543282 
    on boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sdb. Stage2 looks on partition #1 for /grub/grub.conf.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 222580376 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   228,429,823   228,427,776  83 Linux
/dev/sda2         228,431,870   234,440,703     6,008,834   5 Extended
/dev/sda5         228,431,872   234,440,703     6,008,832  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    80,292,869    80,292,807  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1e819523-ee93-465e-9681-c70c2e09c8ca   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0ed04c72-76fd-46b2-8054-e601eea4603d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        446b0360-245e-4ee9-98ac-a4d2a2bce424   ext4       41gb                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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

---

### Post by oldfred on 2010-09-03
You have grub2 in the MBR of sda and grub legacy 0.97 in the MBR of sdb.

Which drive are you using to boot and have you tried booting from both?

Sometimes grub and grub2 do not get along together and it usually is best to totally uninstall both and reinstall grub2.

kansasnoob has combined multiple lines into one with && to make it easy to copy & paste for chroot:
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

kansasnoob's change sda1 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

# new for lucid & karmic 
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

sudo -i
apt-get update
apt-get upgrade
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda
# possibly this also
dpkg-reconfigure grub-pc
#Exit by pressing CTRL-d.

---

### Post by davy51 on 2010-09-03
Sorry guys dont know what I did wrong but none of the above show grub on startup
I deleted Fedore from my slave drive and reformated it in ext4

I deleted all grub and reinstalled grub2

I folowed directions for all three setups and changed the location of grub to all threee locations for each procedure 

Grub doesnt want to show

this is what I get as a final


```

```    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 543282 
    on boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sdb. Stage2 looks on partition #1 for /grub/grub.conf.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 222580400 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   228,429,823   228,427,776  83 Linux
/dev/sda2         228,431,870   234,440,703     6,008,834   5 Extended
/dev/sda5         228,431,872   234,440,703     6,008,832  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    80,292,869    80,292,807  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1e819523-ee93-465e-9681-c70c2e09c8ca   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0ed04c72-76fd-46b2-8054-e601eea4603d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        446b0360-245e-4ee9-98ac-a4d2a2bce424   ext4       41gb                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1e819523-ee93-465e-9681-c70c2e09c8ca
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1e819523-ee93-465e-9681-c70c2e09c8ca
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1e819523-ee93-465e-9681-c70c2e09c8ca
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1e819523-ee93-465e-9681-c70c2e09c8ca ro splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1e819523-ee93-465e-9681-c70c2e09c8ca
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1e819523-ee93-465e-9681-c70c2e09c8ca ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1e819523-ee93-465e-9681-c70c2e09c8ca
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1e819523-ee93-465e-9681-c70c2e09c8ca ro splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1e819523-ee93-465e-9681-c70c2e09c8ca
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1e819523-ee93-465e-9681-c70c2e09c8ca ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1e819523-ee93-465e-9681-c70c2e09c8ca
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1e819523-ee93-465e-9681-c70c2e09c8ca
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0ed04c72-76fd-46b2-8054-e601eea4603d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 113.9GB: boot/grub/core.img
 114.0GB: boot/grub/grub.cfg
 113.9GB: boot/initrd.img-2.6.32-21-generic
 114.5GB: boot/initrd.img-2.6.32-24-generic
 113.9GB: boot/vmlinuz-2.6.32-21-generic
 114.4GB: boot/vmlinuz-2.6.32-24-generic
 114.5GB: initrd.img
 113.9GB: initrd.img.old
 114.4GB: vmlinuz
 113.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  66 ff ff 6a 5b ff ff 79  66 ff ff 79 66 ff ff 79  |f..j[..yf..yf..y|
00000010  66 ff ff 79 66 ff ff 79  66 ff ff 79 66 ff ff 79  |f..yf..yf..yf..y|
00000020  66 ff ff 79 66 ff ff 79  66 ff ff 70 64 ff fe 79  |f..yf..yf..pd..y|
00000030  66 ff f3 77 65 ff cd 67  58 ff 84 41 37 ff 56 29  |f..we..gX..A7.V)|
00000040  23 ff 49 23 1d ff 47 22  1c ff 48 22 1d ff 52 25  |#.I#..G"..H"..R%|
00000050  20 ff 77 3b 32 ff cb 65  57 ff f6 78 66 ff ff 79  | .w;2..eW..xf..y|
00000060  66 ff ff 79 66 ff ff 79  66 ff ff 79 66 ff ff 79  |f..yf..yf..yf..y|
00000070  66 ff ff 72 63 ff ff 79  66 ff ff 79 66 ff ff 79  |f..rc..yf..yf..y|
00000080  66 ff ff 79 66 ff ff 79  66 ff ff 79 66 ff ff 79  |f..yf..yf..yf..y|
00000090  66 ff ff 79 66 ff ff 79  66 ff ff 73 64 ff ff 79  |f..yf..yf..sd..y|
000000a0  66 ff ff 79 66 ff ff 79  66 ff ff 79 66 ff ff 79  |f..yf..yf..yf..y|
000000b0  66 ff ff 79 66 ff ff 79  66 ff ff 79 66 ff ff 72  |f..yf..yf..yf..r|
000000c0  64 ff ff 76 63 ff ff 61  52 ff ff 52 40 ff ff 52  |d..vc..aR..R@..R|
000000d0  40 ff ff 52 40 ff ff 52  40 ff ff 52 40 ff ff 52  |@..R@..R@..R@..R|
000000e0  40 ff ff 36 24 ff ff 52  40 ff ff 52 40 ff ff 52  |@..6$..R@..R@..R|
000000f0  40 ff ff 52 40 ff ff 52  40 ff ff 52 40 ff ff 52  |@..R@..R@..R@..R|
*
00000110  40 ff ff 75 64 ff ff 79  66 ff ff 79 66 ff ff 79  |@..ud..yf..yf..y|
00000120  66 ff ff 79 66 ff ff 79  66 ff ff 79 66 ff ff 6d  |f..yf..yf..yf..m|
00000130  60 ff ff 79 66 ff ff 68  58 ff ff 52 40 ff ff 52  |`..yf..hX..R@..R|
00000140  40 ff ff 52 40 ff ff 52  40 ff ff 52 40 ff ff 52  |@..R@..R@..R@..R|
00000150  40 ff ef 36 2a ff ff 52  40 ff ff 52 40 ff ff 52  |@..6*..R@..R@..R|
00000160  40 ff ff 52 40 ff ff 52  40 ff ff 52 40 ff ff 52  |@..R@..R@..R@..R|
00000170  40 ff ff 52 40 ff ec 39  2c ff ff 52 40 ff ff 68  |@..R@..9,..R@..h|
00000180  58 ff ff 79 66 ff ff 79  66 ff ff 79 66 ff ff 79  |X..yf..yf..yf..y|
00000190  66 ff ff 79 66 ff ff 79  66 ff ff 79 66 ff ff 5f  |f..yf..yf..yf.._|
000001a0  4e ff ff 79 66 ff ff 79  66 ff ff 79 66 ff ff 79  |N..yf..yf..yf..y|
000001b0  66 ff ff 79 66 ff ff 79  66 ff ff 79 66 ff 00 fe  |f..yf..yf..yf...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 b0 5b 00 00 00  |............[...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by oldfred on 2010-09-03
If you only have Ubuntu installed, you will not get a grub menu.  You can force a menu with grub2 by holding down the shift key from BIOS boot until menu appears. 

If you are getting past grub then you may have other issues. If you get the grub menu try recovery mode and/or try e for edit the grub menu and change the kernel from splash quiet to nomodeset.

---

### Post by davy51 on 2010-09-03
Thank you for all the help

Guess thats why i dont get a grub now lol

Ill try the edit  it might help when i go back to a dual boot


Thanks again oldfred

---


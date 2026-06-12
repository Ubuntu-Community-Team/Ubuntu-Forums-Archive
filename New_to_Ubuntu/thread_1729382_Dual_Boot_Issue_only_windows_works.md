---
title: "Dual Boot Issue: only windows works"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by nabeelsadiq on 2011-04-14
ok so, i was having issues with my windows so i got ubuntu and selected the dual boot option. Every time i started the computer it would give me the option to launch ubuntu or windows. so today, just for the hell of it, i picked windows and then i restarted the computer. Now i dont have the option to select ubuntu, it just goes straight to windows. any help will be greatly appreciated

---

### Post by lmarmisa on 2011-04-14
Try to hold the shift key to display the menu during boot. If your Ubuntu version is 9.04 or older press ESC during boot.

---

### Post by nabeelsadiq on 2011-04-14
no luck. it just took me to the setup menu
thanks

---

### Post by wilee-nilee on 2011-04-14
Click on the bootscript link in my signature, follow the instructions to generate a text file. Come back to the thread, open a reply click on the (#) in the reply panel to generate code tags paste all the text from the generated file between.

---

### Post by nabeelsadiq on 2011-04-14
well i cant launch ubuntu right now
should i do this while running ubuntu from a live cd?

---

### Post by lmarmisa on 2011-04-14
Yes. Please boot into a Ubuntu Live CD and run Boot Info Script.

---

### Post by wilee-nilee on 2011-04-14
> **nabeelsadiq said:**
> well i cant launch ubuntu right now
should i do this while running ubuntu from a live cd?

Yeah that works just fine, notice the instructions for the code tags as well in the original post this is important in that without them; the text is much more difficult to read, thanks.;)

---

### Post by nabeelsadiq on 2011-04-14
```

``` Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   510,527,611   510,527,549   7 HPFS/NTFS
/dev/sda2         510,529,534   976,773,119   466,243,586   5 Extended
/dev/sda5         510,529,536   970,819,583   460,290,048  83 Linux
/dev/sda6         970,821,632   976,773,119     5,951,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A8FC5D3EFC5D0848                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        10e54faf-0324-4cb6-9431-c55ad73ddd60   ext4                                     
/dev/sda6        c327b53b-97c0-40d6-a294-f3c3fb71e0aa   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 10e54faf-0324-4cb6-9431-c55ad73ddd60
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 10e54faf-0324-4cb6-9431-c55ad73ddd60
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10e54faf-0324-4cb6-9431-c55ad73ddd60
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=10e54faf-0324-4cb6-9431-c55ad73ddd60 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10e54faf-0324-4cb6-9431-c55ad73ddd60
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=10e54faf-0324-4cb6-9431-c55ad73ddd60 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10e54faf-0324-4cb6-9431-c55ad73ddd60
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=10e54faf-0324-4cb6-9431-c55ad73ddd60 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10e54faf-0324-4cb6-9431-c55ad73ddd60
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=10e54faf-0324-4cb6-9431-c55ad73ddd60 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10e54faf-0324-4cb6-9431-c55ad73ddd60
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=10e54faf-0324-4cb6-9431-c55ad73ddd60 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10e54faf-0324-4cb6-9431-c55ad73ddd60
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=10e54faf-0324-4cb6-9431-c55ad73ddd60 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10e54faf-0324-4cb6-9431-c55ad73ddd60
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10e54faf-0324-4cb6-9431-c55ad73ddd60
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a8fc5d3efc5d0848
    drivemap -s (hd0) ${root}
    chainloader +1
}
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=10e54faf-0324-4cb6-9431-c55ad73ddd60 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c327b53b-97c0-40d6-a294-f3c3fb71e0aa none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 403.2GB: boot/grub/core.img
 356.1GB: boot/grub/grub.cfg
 403.2GB: boot/initrd.img-2.6.32-21-generic
 404.0GB: boot/initrd.img-2.6.32-27-generic
 403.4GB: boot/initrd.img-2.6.32-28-generic
 261.5GB: boot/vmlinuz-2.6.32-21-generic
 403.2GB: boot/vmlinuz-2.6.32-27-generic
 403.4GB: boot/vmlinuz-2.6.32-28-generic
 403.4GB: initrd.img
 404.0GB: initrd.img.old
 403.4GB: vmlinuz
 403.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  c4 8e 03 00 d3 8e 03 00  e2 8e 03 00 f1 8e 03 00  |................|
00000010  00 8f 03 00 0f 8f 03 00  1e 8f 03 00 2d 8f 03 00  |............-...|
00000020  3c 8f 03 00 5f 8f 03 00  76 8f 03 00 85 8f 03 00  |<..._...v.......|
00000030  9c 8f 03 00 b3 8f 03 00  cd 8f 03 00 e4 8f 03 00  |................|
00000040  fb 8f 03 00 14 90 03 00  23 90 03 00 42 90 03 00  |........#...B...|
00000050  51 90 03 00 74 90 03 00  8b 90 03 00 a5 90 03 00  |Q...t...........|
00000060  be 90 03 00 d5 90 03 00  e4 90 03 00 07 91 03 00  |................|
00000070  16 91 03 00 25 91 03 00  3c 91 03 00 53 91 03 00  |....%...<...S...|
00000080  6a 91 03 00 81 91 03 00  a4 91 03 00 b3 91 03 00  |j...............|
00000090  d2 91 03 00 ec 91 03 00  03 92 03 00 1a 92 03 00  |................|
000000a0  31 92 03 00 48 92 03 00  5f 92 03 00 76 92 03 00  |1...H..._...v...|
000000b0  8d 92 03 00 a4 92 03 00  be 92 03 00 d5 92 03 00  |................|
000000c0  ec 92 03 00 03 93 03 00  1a 93 03 00 33 93 03 00  |............3...|
000000d0  42 93 03 00 63 93 03 00  72 93 03 00 93 93 03 00  |B...c...r.......|
000000e0  a2 93 03 00 c3 93 03 00  d2 93 03 00 f3 93 03 00  |................|
000000f0  0a 94 03 00 21 94 03 00  38 94 03 00 4f 94 03 00  |....!...8...O...|
00000100  5e 94 03 00 6d 94 03 00  7c 94 03 00 8b 94 03 00  |^...m...|.......|
00000110  9a 94 03 00 a9 94 03 00  b8 94 03 00 c7 94 03 00  |................|
00000120  d6 94 03 00 e5 94 03 00  f4 94 03 00 03 95 03 00  |................|
00000130  22 95 03 00 3c 95 03 00  63 95 03 00 7d 95 03 00  |"...<...c...}...|
00000140  94 95 03 00 ad 95 03 00  e4 95 03 00 03 96 03 00  |................|
00000150  4a 96 03 00 61 96 03 00  7b 96 03 00 9a 96 03 00  |J...a...{.......|
00000160  d1 96 03 00 10 97 03 00  27 97 03 00 4c 97 03 00  |........'...L...|
00000170  71 97 03 00 88 97 03 00  97 97 03 00 a6 97 03 00  |q...............|
00000180  bf 97 03 00 d6 97 03 00  e5 97 03 00 f4 97 03 00  |................|
00000190  03 98 03 00 1a 98 03 00  34 98 03 00 43 98 03 00  |........4...C...|
000001a0  68 98 03 00 77 98 03 00  8e 98 03 00 b5 98 03 00  |h...w...........|
000001b0  c4 98 03 00 de 98 03 00  f5 98 03 00 0e 99 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 78 6f 1b 00 fe  |...........xo...|
000001d0  ff ff 05 fe ff ff 02 78  6f 1b 00 d8 5a 00 00 00  |.......xo...Z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by nabeelsadiq on 2011-04-14
well hopefully i did that right
and hopefully that gibirish makes sense to you
thanks for the help

---

### Post by lmarmisa on 2011-04-15
The Master Boot Record of your hard drive has stored the Windows XP loader. There is also something strange in relation with the extended partition /dev/sda2.

I recommend this procedure for reinstalling GRUB.

Boot into an Ubuntu Live CD, open a terminal and type theses commands:

```

sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
grub-install /dev/sda
grub-install --recheck /dev/sda
exit
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt
sudo reboot

```

After reboot type:

```

sudo update-grub

```

---

### Post by Mark Phelps on 2011-04-15
> **nabeelsadiq said:**
> ok so, i was having issues with my windows so i got ubuntu and selected the dual boot option. Every time i started the computer it would give me the option to launch ubuntu or windows. 
From the presence of wubildr, it looks like you did a Wubi installation -- and later, did a separate partition installation.  Is that right?

> so today, just for the hell of it, i picked windows and then i restarted the computer. 
Now i dont have the option to select ubuntu, it just goes straight to windows. any help will be greatly appreciated

If you replaced the Wubi version with a separate version, it might have revised the Windows boot menu to remove the Ubuntu entry.

Having two versions of Ubuntu is really going to hose up your PC big time.

---


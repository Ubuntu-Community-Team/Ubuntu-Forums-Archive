---
title: "Can't boot after upgrades"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by Pikachuu on 2010-08-12
I'm dualbooting Windows 7 and Lucid Lynx on my machine, a HP TouchSmart tx2. I just went into Lucid and let the Update Manager update all my components, and when I rebooted, it refuses to go past the proprietary splash screen. Hitting Esc to enter boot options also causes the machine to become unresponsive after changing the message on the splash to "Esc to pause". I think it might have been because I messed up with grub installation again.

When I upgraded to Lucid Lynx I sped through the installation process and just skipped the installation of grub, which caused an inability to boot and I had to go in using a LiveCD, fix things, and get back to my previous system.

This time the grub-pc prompt came up again, so I went through it slowly. It recommended that I install grub on all the partitions that were available if I wasn't sure which one the boot partition was (which I wasn't), so I went ahead.

After that I ran a script to update some drivers for my touchscreen and pen (I doubt this affected the reboot) then let it reboot.

I came back after 15 minutes to find the HP splash screen waiting for me and unresponsive. So that was when I realised I had a problem, tried to get into the BIOs, got out my LiveCD and hoped that it would boot in. It hasn't worked yet, so I would like to request some help...

---

### Post by Rubi1200 on 2010-08-12
Since you have the LiveCD, please boot the computer and choose to try in live mode.

Then click on the link at the bottom of my post and follow the instructions there.

Post the results back here and please wrap the text with the # tag.

Thanks.

By the way, this is almost certainly the problem:

> It recommended that I install grub on all the partitions that were available if I wasn't sure which one the boot partition was (which I wasn't), so I went ahead.

But we need to see the results of the bootscript just to make sure.

---

### Post by Pikachuu on 2010-08-12
That's precisely the problem... Even the LiveCD does not work. If I could go in through the LiveCD I could have pulled the fix I used last time. It won't go past the boot and I can't even get into the BIOs. Bamboozling.

To clarify, the boot screen I'm referring to is the one that comes out whenever you boot a proprietary computer where the manufacturer's brand name comes up and where you would press the button to get into the BIOs. Yeah.

---

### Post by Rubi1200 on 2010-08-12
I assume you have tried a forced reboot?

Not the most elegant way to do things, but sometimes...

---

### Post by Pikachuu on 2010-08-12
Yeah I happen to have, lots.

I feel very silly now, because after detaching my iPod and my Nexus One from my machine, it boots. D'oh.

Should I go and uninstall grub from the partitions I put them in, or is it safe to leave them lying around?

---

### Post by Rubi1200 on 2010-08-12
Since you have played around a bit with things, I still suggest you post the results of the bootscript from my previous post before making any changes.

It won't take long and helps us make sure there are no other problems lurking around.

---

### Post by scrooge_74 on 2010-08-12
You dont need to uninstall any partitions, just dont have any of those devices hook at boot time, in fact go to bios and check booting order, you probably have USB devices before hard drives

---

### Post by Pikachuu on 2010-08-12
Here's my boot info script.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 500431406 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /grldr

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   396,900,334   396,900,272   7 HPFS/NTFS
/dev/sda2         396,900,352   499,408,895   102,508,544   7 HPFS/NTFS
/dev/sda3         499,412,655   601,682,444   102,269,790   5 Extended
/dev/sda5         499,412,718   597,425,219    98,012,502  83 Linux
/dev/sda6         597,425,283   601,682,444     4,257,162  82 Linux swap / Solaris
/dev/sda4         601,698,304   625,135,615    23,437,312   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________
Note: sector size is 4096 (not 512)

Disk /dev/sdd: 7971 MB, 7971016704 bytes
35 heads, 41 sectors/track, 1356 cylinders, total 1946049 sectors
Units = sectors of 1 * 4096 = 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63     1,946,047     1,945,985   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        186E502653755E4E                       ntfs                                     
/dev/sda2        48A205C1A205B50A                       ntfs       Pikachu                       
/dev/sda3: PTTYPE="dos" 
/dev/sda4        7C429BA9429B66A4                       ntfs       RECOVERY                      
/dev/sda5        dde437f8-6eba-436c-a4f9-77f487d1d925   ext4                                     
/dev/sda6        c9f7f65c-cda5-4a7e-8ca0-241cd6592a29   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdd1        3141-5926                              vfat       PIKACHU IPO                   
/dev/sdd         A88B-3652                              vfat       iPod                          
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/Pikachu           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1        /media/PIKACHU IPO       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


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
set default="${saved_entry}"
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
search --no-floppy --fs-uuid --set dde437f8-6eba-436c-a4f9-77f487d1d925
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
search --no-floppy --fs-uuid --set dde437f8-6eba-436c-a4f9-77f487d1d925
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set dde437f8-6eba-436c-a4f9-77f487d1d925
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=dde437f8-6eba-436c-a4f9-77f487d1d925 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set dde437f8-6eba-436c-a4f9-77f487d1d925
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=dde437f8-6eba-436c-a4f9-77f487d1d925 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set dde437f8-6eba-436c-a4f9-77f487d1d925
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=dde437f8-6eba-436c-a4f9-77f487d1d925 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set dde437f8-6eba-436c-a4f9-77f487d1d925
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=dde437f8-6eba-436c-a4f9-77f487d1d925 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set dde437f8-6eba-436c-a4f9-77f487d1d925
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=dde437f8-6eba-436c-a4f9-77f487d1d925 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set dde437f8-6eba-436c-a4f9-77f487d1d925
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=dde437f8-6eba-436c-a4f9-77f487d1d925 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set dde437f8-6eba-436c-a4f9-77f487d1d925
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=dde437f8-6eba-436c-a4f9-77f487d1d925 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set dde437f8-6eba-436c-a4f9-77f487d1d925
    echo    'Loading Linux 2.6.31-22-generic ...'
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=dde437f8-6eba-436c-a4f9-77f487d1d925 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set dde437f8-6eba-436c-a4f9-77f487d1d925
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set dde437f8-6eba-436c-a4f9-77f487d1d925
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    savedefault
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 186e502653755e4e
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    savedefault
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 7c429ba9429b66a4
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
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=dde437f8-6eba-436c-a4f9-77f487d1d925 / ext4 errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=c9f7f65c-cda5-4a7e-8ca0-241cd6592a29 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_SG.UTF-8 0 0
/dev/sda2 /media/Pikachu ntfs-3g defaults,locale=en_SG.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


 256.2GB: boot/grub/core.img
 258.9GB: boot/grub/grub.cfg
 261.6GB: boot/initrd.img-2.6.31-22-generic
 263.9GB: boot/initrd.img-2.6.32-22-generic
 270.7GB: boot/initrd.img-2.6.32-23-generic
 271.0GB: boot/initrd.img-2.6.32-24-generic
 265.6GB: boot/vmlinuz-2.6.31-22-generic
 267.3GB: boot/vmlinuz-2.6.32-22-generic
 299.6GB: boot/vmlinuz-2.6.32-23-generic
 264.3GB: boot/vmlinuz-2.6.32-24-generic
 271.0GB: initrd.img
 270.7GB: initrd.img.old
 264.3GB: vmlinuz
 299.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 10 04 00 02  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  c0 b1 1d 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 52 36 8b a8 69  50 6f 64 00 4d 45 20 20  |..)R6..iPod.ME  |
00000050  20 20 46 41 54 33 32 20  20 20 00 c9 8e d1 bc f4  |  FAT32   ......|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 41 70  |..............Ap|
000001b0  70 6c 65 20 69 50 6f 64  20 20 20 20 20 20 00 01  |ple iPod      ..|
000001c0  01 00 0b 22 29 79 3f 00  00 00 81 b1 1d 00 00 00  |...")y?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdd1

00000000  eb 3c 90 2a 55 4f 4b 4a  49 48 43 00 10 04 20 00  |.<.*UOKJIHC... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  7e b1 1d 00 db 01 00 00  00 00 00 00 02 00 00 00  |~...............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 26 59 41 31 49  50 4f 44 20 20 20 20 20  |..)&YA1IPOD     |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 5b 7c ac  |  FAT32   ...[|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 7b  7b 7e 7e 7c 20 53 20 54  |.......{{~~| S T|
00000080  20 4f 20 50 20 7c 20 54  68 69 73 20 69 73 20 41  | O P | This is A|
00000090  70 70 6c 65 20 69 50 6f  64 20 6e 6f 74 20 61 20  |pple iPod not a |
000000a0  62 6f 6f 74 61 62 6c 65  20 64 69 73 6b 2e 50 6c  |bootable disk.Pl|
000000b0  65 61 73 65 20 74 72 79  20 61 67 61 69 6e 20 2e  |ease try again .|
000000c0  2e 2e 20 00 00 00 00 00  00 00 00 00 00 00 00 00  |.. .............|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc 
```

Thanks very much for your help, Rubi and scrooge. Incidentally I did enter my BIOs and check my boot order (as well as swap my internal hard disk above the DVD-drive since I forgot to swap it back the last time I used the LiveCD) and my internal hard disk was above the USB drives in boot order. Strange.

---

### Post by Rubi1200 on 2010-08-12
As far as I can tell everything looks normal, except for this:

> Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 500431406 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.

Anyway, the usual answer is to reinstall GRUB2 from the LiveCD.

[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling)

If you need more help, let us know.

---

### Post by Pikachuu on 2010-08-12
I think I should be fine from here. I'll reinstall grub2 when I have time since my computer is running fine now. Thanks very much for your help rubi.

---


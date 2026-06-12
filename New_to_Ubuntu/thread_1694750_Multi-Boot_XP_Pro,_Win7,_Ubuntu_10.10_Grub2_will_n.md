---
title: "Multi-Boot XP Pro, Win7, Ubuntu 10.10 Grub2 will not install right (Need Help)"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by John4582 on 2011-02-24
[IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG] [SIZE=5]Solved Solved Solved Solved[/SIZE] [IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG] 

First of all I want to **Thank** you **_Oldfred_ & _you Quackers_ **again for all your help and sticking with me.

[SIZE=5][COLOR=Red]See Post #79 on Page 8 for cause and solution [/COLOR][/SIZE][COLOR=Red]
[/COLOR]
HI all, I am New to Ubuntu and this is my first experience with any Linux OS. I am fairly computer literate but I just do not understand why Grub2 will not install right. I have tried both installing Grub2 to the MBR and SDA5 where Ubuntu is installed & using EasyBCD (my preferred way) to boot Ubuntu with no Luck. Same result no matter how I install Ubuntu and I always use the Advance option when I tell Ubuntu how/where to install.

**ubuntu@ubuntu:~$ sudo fdisk -l**

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00272e2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      208054   104859184+   7  HPFS/NTFS
/dev/sda2          208055      416109   104859720    7  HPFS/NTFS
/dev/sda3          624465     2907021  1150408728    7  HPFS/NTFS
/dev/sda4          416110      624464   105010859    f  W95 Ext'd (LBA)
/dev/sda5          416110      477062    30720250   83  Linux
/dev/sda6          477063      620302    72192928+  83  Linux
/dev/sda7          620303      624464     2097616+  82  Linux swap / Solaris

Partition table entries are not in disk order

**Boot Info Script 0.55 Text Follows**

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 428555164 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,718,431   209,718,369   7 HPFS/NTFS
/dev/sda2         209,718,432   419,437,871   209,719,440   7 HPFS/NTFS
/dev/sda3         629,459,712 2,930,277,167 2,300,817,456   7 HPFS/NTFS
/dev/sda4         419,437,994   629,459,711   210,021,718   f W95 Ext d (LBA)
/dev/sda5         419,437,996   480,878,495    61,440,500  83 Linux
/dev/sda6         480,878,559   625,264,415   144,385,857  83 Linux
/dev/sda7         625,264,479   629,459,711     4,195,233  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6664413B64410F6D                       ntfs       HP_PAVILION                   
/dev/sda2        01CBCEB6C382A580                       ntfs       Win7                          
/dev/sda3        0478C00D78BFFF82                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        e61ee3b6-506d-4229-be2a-bb99a18ef2ca   ext4                                     
/dev/sda6        912f3105-7575-4df5-be60-29a9c0d0a5fe   ext4                                     
/dev/sda7        f7196ef2-e5bb-43ac-be73-b8cbfc071bee   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /FASTDETECT /USEPMTIMER /NOEXECUTE=OPTIN 
c:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS 

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
search --no-floppy --fs-uuid --set e61ee3b6-506d-4229-be2a-bb99a18ef2ca
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set e61ee3b6-506d-4229-be2a-bb99a18ef2ca
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e61ee3b6-506d-4229-be2a-bb99a18ef2ca
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=e61ee3b6-506d-4229-be2a-bb99a18ef2ca ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e61ee3b6-506d-4229-be2a-bb99a18ef2ca
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=e61ee3b6-506d-4229-be2a-bb99a18ef2ca ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e61ee3b6-506d-4229-be2a-bb99a18ef2ca
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e61ee3b6-506d-4229-be2a-bb99a18ef2ca
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6664413b64410f6d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 01cbceb6c382a580
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
UUID=e61ee3b6-506d-4229-be2a-bb99a18ef2ca /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=912f3105-7575-4df5-be60-29a9c0d0a5fe /home           ext4    defaults        0       2
/dev/sda7       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 219.4GB: boot/grub/core.img
 234.3GB: boot/grub/grub.cfg
 226.2GB: boot/initrd.img-2.6.35-25-generic-pae
 219.3GB: boot/vmlinuz-2.6.35-25-generic-pae
 226.2GB: initrd.img
 219.3GB: vmlinuz
```Thanks in advance - Any help would be greatly appreciated.

---

### Post by mukhcech on 2011-02-24
Hi I am using window 7 and ubuntu desktop version on my laptop acer 5730Z.The problem is I tried giving my bootloader to windows using easyBCD.but things went outta my control.naw I lost the ubuntu buh I gat just the window bootloader now.How do i restall it plz it is urgent.thanks:guitar::lolflag:

---

### Post by John4582 on 2011-02-26
First let say sorry for the long post but I believe that this problem may be a Grub2 issue and I am willing to work with anyone to verify what is going on. Only I can not leave my computer where it will only boot via Live CD for very long. I can repeat everything I did in this post as I am getting good at installing Ubuntu LOL.

Hopefully someone can give me some guidance. I have deleted the Ubuntu partitions and reinstalled everything several times with basically the same results.

1. I booted the Ubuntu Live CD 10.10

2. I used **GParted **to create 3 partitions within the my 100 GB Extended partition sda4.[INDENT]sda5 20 GB Ext4 
sda6 76 GB Ext4
sda7 4 GB Ext4[/INDENT]3. I opened a **Terminal** and executed the following:
```
ubuntu@ubuntu:~$ **sudo fdisk -l**

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00272e2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      208054   104859184+   7  HPFS/NTFS
/dev/sda2          208055      416109   104859720    7  HPFS/NTFS
/dev/sda3          624465     2907021  1150408728    7  HPFS/NTFS
/dev/sda4          416110      624464   105010920    f  W95 Ext'd (LBA)
/dev/sda5          416110      457760    20992072+  83  Linux
/dev/sda6          457761      616237    79872376+  83  Linux
/dev/sda7          616238      624464     4146376+  83  Linux

Partition table entries are not in disk order
**And**
ubuntu@ubuntu:~$ **df -Th**
Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    1.4G   49M  1.4G   4% /
none      devtmpfs    1.4G  324K  1.4G   1% /dev
/dev/sr0   iso9660    694M  694M     0 100% /cdrom
/dev/loop0
          squashfs    661M  661M     0 100% /rofs
none         tmpfs    1.4G  104K  1.4G   1% /dev/shm
tmpfs        tmpfs    1.4G   72K  1.4G   1% /tmp
none         tmpfs    1.4G   92K  1.4G   1% /var/run
none         tmpfs    1.4G  4.0K  1.4G   1% /var/lock
/dev/sda3  fuseblk    1.1T  379G  719G  35% /media/Data
ubuntu@ubuntu:~$ 

```4. I copied the **boot_info_script55.sh** to my Desktop and executed the following:
**sudo bash ~/Desktop/boot_info_script*.sh**
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,718,431   209,718,369   7 HPFS/NTFS
/dev/sda2         209,718,432   419,437,871   209,719,440   7 HPFS/NTFS
/dev/sda3         629,459,712 2,930,277,167 2,300,817,456   7 HPFS/NTFS
/dev/sda4         419,437,872   629,459,711   210,021,840   f W95 Ext d (LBA)
/dev/sda5         419,437,935   461,422,079    41,984,145  83 Linux
/dev/sda6         461,422,143   621,166,895   159,744,753  83 Linux
/dev/sda7         621,166,959   629,459,711     8,292,753  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6664413B64410F6D                       ntfs       HP_PAVILION                   
/dev/sda2        01CBCEB6C382A580                       ntfs       Win7                          
/dev/sda3        0478C00D78BFFF82                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        99466822-de80-4152-8496-801c25c05fb4   ext4                                     
/dev/sda6        2eff2ab1-c9f5-4238-8d8f-8ed93386db73   ext4                                     
/dev/sda7        bba20a9e-e6ad-4c88-bf63-4ae6b20ba4db   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /FASTDETECT /USEPMTIMER /NOEXECUTE=OPTIN
c:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  3e 0a e3 22 ef 23 d0 95  fc 6d db b5 43 d8 b4 6d  |>..".#...m..C..m|
00000010  8c 9f 40 20 01 20 66 84  04 24 91 e1 29 53 40 3b  |..@ . f..$..)S@;|
00000020  44 35 91 d8 95 8d 1b e2  39 05 45 bf 99 17 84 73  |D5......9.E....s|
00000030  3e 60 dc f6 d3 78 2a c1  fd e7 a6 7b 8a 2b 70 2b  |>`...x*....{.+p+|
00000040  22 ba b5 ee 40 e0 6c e7  66 ce 94 53 65 4d 7b bf  |"...@.l.f..SeM{.|
00000050  48 ca d1 a4 65 7f 64 40  7a 0c c9 f3 87 62 a9 84  |H...e.d@z....b..|
00000060  72 d6 23 b8 69 75 e5 a9  6f 71 fb 84 49 12 31 0d  |r.#.iu..oq..I.1.|
00000070  e5 7b a9 f4 01 f1 12 c4  8f 44 ac 66 a3 c3 89 6d  |.{.......D.f...m|
00000080  45 a0 be 82 ef 5f 9c 43  50 46 7f 28 bc fd 82 69  |E...._.CPF.(...i|
00000090  c9 ec 68 d2 7c 37 ee 8f  5c 55 93 cf b5 29 df 89  |..h.|7..\U...)..|
000000a0  e3 42 c1 fb d2 99 2d 04  6c 13 59 8d 83 03 33 15  |.B....-.l.Y...3.|
000000b0  0a ee ec 40 1c 43 fa 83  53 a0 ec cf 7f 7f d6 1f  |...@.C..S.......|
000000c0  a3 48 cc 7a 56 97 be b2  39 86 99 a6 0d 0d 85 4d  |.H.zV...9......M|
000000d0  09 5b 6b ee 2d 85 1b cc  f9 eb c5 1f c7 5a f9 1f  |.[k.-........Z..|
000000e0  b3 df a9 30 8c 07 de d9  7e c0 ee e2 35 9e 47 f1  |...0....~...5.G.|
000000f0  14 a9 b8 0e b4 3c f6 fd  1b 2d 35 d4 39 bb c2 dc  |.....<...-5.9...|
00000100  7f 09 43 2c 3a 77 83 71  4a 96 a1 98 fc ed 7a b1  |..C,:w.qJ.....z.|
00000110  b6 a5 20 73 0d 19 79 bf  df 0a e5 d2 f5 f7 b6 1f  |.. s..y.........|
00000120  40 b6 c1 1a b3 b3 28 42  86 75 ef fd cd f4 a2 f4  |@.....(B.u......|
00000130  bb f5 b5 ef 29 f8 97 81  34 80 f9 50 22 d3 3f e2  |....)...4..P".?.|
00000140  78 5c a4 22 18 43 7a 01  8d c5 7d c8 55 eb ec 04  |x\.".Cz...}.U...|
00000150  67 b8 b9 6e 7c 1b 78 54  d5 0e 4d 0c 60 b5 14 b7  |g..n|.xT..M.`...|
00000160  4a fa 7d 53 17 e4 14 79  e5 77 9d f0 da 9a 8c 77  |J.}S...y.w.....w|
00000170  3c da 02 bf 27 b9 b3 e8  96 73 50 24 03 62 ad a6  |<...'....sP$.b..|
00000180  b3 4c 72 1c f6 5a 97 f0  9f c0 af 78 a0 df 22 c0  |.Lr..Z.....x..".|
00000190  e8 73 e4 45 b3 c1 e0 d3  75 d2 b0 9e 27 f0 66 0e  |.s.E....u...'.f.|
000001a0  3c d9 ef 6e c2 8a de 56  22 6f 46 bf 76 60 26 bf  |<..n...V"oF.v`&.|
000001b0  50 b1 d0 5a 2d 49 2c 0a  d9 d9 e7 ff a5 24 00 0f  |P..Z-I,......$..|
000001c0  ff ff 83 0f ff ff 3f 00  00 00 91 a0 80 02 00 fe  |......?.........|
000001d0  ff ff 05 fe ff ff d0 a0  80 02 30 83 85 09 00 00  |..........0.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```5. I double clicked on the **Install Ubuntu 10.10** icon and followed the instructions for installing Ubuntu.

6. I chose the custom/advance mode as where to install Ubuntu.[INDENT]sda5 20 GB Ext4 "/"
sda6 76 GB Ext4 "/home"
sda7 4 GB Ext4   "swap"[/INDENT][INDENT]also I installed Gurb2 to sda MBR
also I **installed 3rd Party** software but this time chose NOT to install **Update**.
then let the install complete and restarted[/INDENT]7. On restart I was greeted with the same  **error: no such partition Grub rescue->** as always.

8. Typed ls and pressed Enter and the following was the output:[INDENT](hd0) (hd0,msdos1) (hd0,msdos2) (hd0,msdos3) (fd0)
Note: I think the following applies[/INDENT][INDENT](hd0) = 1.5 TB HDD
(hd0,msdos1) = XP Pro
(hd0,msdos1) = Win7 Pro
(hd0,msdos1) = Data (shared by all OS's)
(fd0) = Floppy or DVD/CD/RW[/INDENT]9. I also checked the BIOS and do NOT believe that the **error: no such partition **is in anyway related to my system BIOS as you can see below everything about my HDD is being reported correctly.


 10. I booted back into the Ubuntu Live CD 10.10

11. I opened a **Terminal** and executed the following:
```
ubuntu@ubuntu:~$ grub-install -v
grub-install (GRUB) 1.98+20100804-5ubuntu3
ubuntu@ubuntu:~$ **sudo fdisk -l**

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00272e2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      208054   104859184+   7  HPFS/NTFS
/dev/sda2          208055      416109   104859720    7  HPFS/NTFS
/dev/sda3          624465     2907021  1150408728    7  HPFS/NTFS
/dev/sda4          416110      624464   105010889+   f  W95 Ext'd (LBA)
/dev/sda5          416110      457760    20992072+  83  Linux
/dev/sda6          457761      616237    79872376+  83  Linux
/dev/sda7          616238      624464     4146376+  82  Linux swap / Solaris

Partition table entries are not in disk order
**And**
ubuntu@ubuntu:~$ **df -Th**
Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    1.4G   49M  1.4G   4% /
none      devtmpfs    1.4G  324K  1.4G   1% /dev
/dev/sr0   iso9660    694M  694M     0 100% /cdrom
/dev/loop0
          squashfs    661M  661M     0 100% /rofs
none         tmpfs    1.4G  104K  1.4G   1% /dev/shm
tmpfs        tmpfs    1.4G   80K  1.4G   1% /tmp
none         tmpfs    1.4G   92K  1.4G   1% /var/run
none         tmpfs    1.4G  4.0K  1.4G   1% /var/lock
/dev/sda3  fuseblk    1.1T  379G  719G  35% /media/Data
ubuntu@ubuntu:~$ 
```11. I copied the **boot_info_script55.sh** to my Desktop and executed the following:
**sudo bash ~/Desktop/boot_info_script*.sh**
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,718,431   209,718,369   7 HPFS/NTFS
/dev/sda2         209,718,432   419,437,871   209,719,440   7 HPFS/NTFS
/dev/sda3         629,459,712 2,930,277,167 2,300,817,456   7 HPFS/NTFS
/dev/sda4         419,437,933   629,459,711   210,021,779   f W95 Ext d (LBA)
/dev/sda5         419,437,935   461,422,079    41,984,145  83 Linux
/dev/sda6         461,422,143   621,166,895   159,744,753  83 Linux
/dev/sda7         621,166,959   629,459,711     8,292,753  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6664413B64410F6D                       ntfs       HP_PAVILION                   
/dev/sda2        01CBCEB6C382A580                       ntfs       Win7                          
/dev/sda3        0478C00D78BFFF82                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        87550683-e128-479d-bc7a-42177d701eb6   ext4                                     
/dev/sda6        a1c5d813-9b19-421d-8d01-bf61624d8425   ext4                                     
/dev/sda7        bec48c13-4575-413f-a64f-5f1455e27e5e   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /FASTDETECT /USEPMTIMER /NOEXECUTE=OPTIN
c:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS

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
search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=87550683-e128-479d-bc7a-42177d701eb6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=87550683-e128-479d-bc7a-42177d701eb6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6664413b64410f6d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 01cbceb6c382a580
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
UUID=87550683-e128-479d-bc7a-42177d701eb6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=a1c5d813-9b19-421d-8d01-bf61624d8425 /home           ext4    defaults        0       2
/dev/sda7       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 234.7GB: boot/grub/core.img
 232.1GB: boot/grub/grub.cfg
 215.8GB: boot/initrd.img-2.6.35-25-generic-pae
 234.7GB: boot/vmlinuz-2.6.35-25-generic-pae
 215.8GB: initrd.img
 234.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ee 68 85 41 71 c4 83 4d  0a 3e 53 71 57 3f 92 48  |.h.Aq..M.>SqW?.H|
00000010  af 55 cd 73 b5 dc a0 a0  6c 8f 20 9a 41 0a 16 2a  |.U.s....l. .A..*|
00000020  e2 45 3e 83 6d 17 12 ac  cb d9 77 0a 1f aa 64 ac  |.E>.m.....w...d.|
00000030  67 e8 66 ec 27 2e 14 af  b6 21 5d c8 f2 30 32 0e  |g.f.'....!]..02.|
00000040  95 89 ad 4a 4a da d2 4f  90 a9 92 00 5f 86 bf 5a  |...JJ..O...._..Z|
00000050  49 f6 85 d0 d6 fc a2 7d  66 f8 bb 49 ad f0 18 80  |I......}f..I....|
00000060  3f 00 fa bc 50 0a 4f 8b  fd 31 62 de 8b 40 02 5d  |?...P.O..1b..@.]|
00000070  de 52 f0 f1 1c d0 0a 60  ae 30 24 54 6d 3c f6 90  |.R.....`.0$Tm<..|
00000080  66 9e 0a 46 36 bb 90 29  d3 89 bb b9 fb d6 f4 92  |f..F6..)........|
00000090  f0 1c ed 83 48 27 f0 ec  9a 1d 5d 59 a7 36 47 04  |....H'....]Y.6G.|
000000a0  4f 0b 6c 46 3d ec 3a 87  20 41 48 b5 ea 02 5d 97  |O.lF=.:. AH...].|
000000b0  ce c0 e6 ab 8e 22 f2 40  f0 f8 6d 19 e8 0f 47 32  |.....".@..m...G2|
000000c0  47 ae 2e 44 a3 54 cc 03  ac e1 7c e3 36 e9 0e 56  |G..D.T....|.6..V|
000000d0  9d d1 99 11 4a a4 83 18  1c f0 c5 74 bf 18 45 46  |....J......t..EF|
000000e0  73 21 14 0b d5 1a 0f 41  01 28 11 15 20 e7 d9 3f  |s!.....A.(.. ..?|
000000f0  77 9d 85 61 02 e9 86 8b  26 29 a5 1d b3 06 7d b6  |w..a....&)....}.|
00000100  74 d9 12 23 44 9f ed 0c  b0 34 c0 9a 20 21 6d e2  |t..#D....4.. !m.|
00000110  1b 09 fd f9 ca c4 c6 d0  c3 72 ee a2 8c 8f 48 c2  |.........r....H.|
00000120  a3 71 8d 7a fd b0 c0 cc  61 d4 21 9a 9e 40 f7 45  |.q.z....a.!..@.E|
00000130  5b 72 de 6a f9 37 3c 50  b7 20 d3 e6 30 ff ee 68  |[r.j.7<P. ..0..h|
00000140  db 1e 0b 4d df e1 fc 2f  a6 7f 47 5d 29 40 79 73  |...M.../..G])@ys|
00000150  5b f7 7c 54 85 4c 4f ab  a7 db ec 96 ae 26 f1 af  |[.|T.LO......&..|
00000160  a5 cb 95 4f 63 74 9e 02  d5 cb 0e 42 f0 69 24 38  |...Oct.....B.i$8|
00000170  94 30 08 43 94 f2 a2 46  84 12 82 39 11 82 f7 4e  |.0.C...F...9...N|
00000180  3a d7 d2 de d6 20 e9 01  c8 e1 9d 50 2c 40 c0 58  |:.... .....P,@.X|
00000190  21 e4 bb 28 a9 e9 24 3a  91 ac 90 33 ce 08 e6 c3  |!..(..$:...3....|
000001a0  fb 8d 73 e4 46 4a c9 e6  81 4e ad e6 b4 87 5f 10  |..s.FJ...N...._.|
000001b0  36 7f fc 8d ed 01 10 ff  b7 4f dc 0c 46 da 00 0f  |6........O..F...|
000001c0  ff ff 83 0f ff ff 02 00  00 00 91 a0 80 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff 93 a0  80 02 30 83 85 09 00 00  |..........0.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```Additional Hardware Information:[INDENT]CPU AMD PhenomQuad Core 9850 2.5 GHz
Gigabyte MB
Memory - 4096 MB 2 x 2 GB
HDD - Seagate 1.5 TB 7200 RPM
ATI integrated 4200 Video
Realtek integrated 10/100/1000 Gigabit Ethernet  [/INDENT]Thanks in advance - Any and all help will be  greatly appreciated

---

### Post by amsterdamharu on 2011-02-26
It looks like this time the boot info script is not complaining about grub looking in the wrong sector for core.img.

You still get a grub rescue prompt when you boot?

You can boot off the live CD and then try the following commands:[FONT=monospace]

[/FONT]```
sudo mount /dev/sda5 /mnt
# chroot in to mnt
sudo mount --bind /dev/ /mnt/dev
sudo chroot /mnt
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts
export HOME=/root
export LC_ALL=C
apt-get install --reinstall grub-pc
 grub-install /dev/sda
update-grub
# clean up an un-chroot
umount /proc # if this doesn't work try umount -lf /proc
umount /sys
umount /dev/pts
exit
sudo umount /mnt/dev
sudo umount /mnt

```

---

### Post by John4582 on 2011-02-26
> **amsterdamharu said:**
> It looks like this time the boot info  script is not complaining about grub looking in the wrong sector for  core.img.

Yes it looks like Grub is in the right place now, No complaints during install based on the boot_info_script.

> 
You still get a grub rescue prompt when you boot?I applied the steps via Terminal like you suggested and Yes I'm still getting the grub rescue prompt "**error: no such partition Grub rescue->**" on reboot with the following after I type "**ls**" at the [B]Grub rescue-> prompt.
[/B][INDENT]**(hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (fd0)**

For  some reason on boot-up Grub2 doesn't see the Ubuntu/Linux partition.  This has been the case from day one and It doesn't matter how I install  it, although I've only tried the Custom/Advance installing Ubuntu in the  extended partition.
[/INDENT]> 
 You can boot off the live CD and then try the following commands:Yes I can boot from the Live CD. I built the computer on a Gigabyte  GA-MA785GM-US2H (rev. 3.3) Motherboard which allows you to press F12 on  boot-up and then you can boot from just about any Media.

My computer is less then 3 month old and I built it so I could   multi-boot xp win7 & Ubuntu. Just about everything is new. XP and   Win7 has been running with no problems at all from day one. 
 
There's a BIOS update "F12" and I'm at "F11" because the F12 update only  addresses audio noise issue while running ET6 (EasyTune 6) in Win7 which I don't do  so I chose not to update it which is what Gigabyte recommends.

There's is a Note as to the chipset drivers on the Gigabyte web site related to Linux, it reads as follows:[INDENT]Due to different Linux support condition provided by chipset vendors,  please download Linux driver from chipset vendors' website or 3rd party  website.
[/INDENT][INDENT]I haven't looked for any special  chipset drivers for Linux because I haven't experienced any problems  while running the Try Ubuntu via the Live CD. Also it seams to me that  if everything is being reported to Ubuntu/Grub2 during the install it  should be available during boot-up.

Also when I type "**ls**" at the Grub Rescue prompt and Grub displays ->[INDENT] [B](hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (fd0)
[/B][/INDENT]it's  coming from Grub2. I say this because as far as I know Grub is the only  Application that refers to partitions as msdosX where X is the  partition number. (I may be wrong here)

Also Grub is apparently getting the BIOS  information because Grub knows it's booting from the HDD because Grub knows  about all the partitions except its own so Grub must be getting the HDD  ID/Location, also Grub knows I have (fd0) installed which is my 3.5"  floppy I believe, could be the DVD/CD/RW I guess.
[/INDENT]Anyway hopefully with help from this forum We / I can resolve this issue.

The following is the latest Terminal session text and Results.txt from boot_info_script after applying your suggestions.

```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev/ /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# mount -t proc none /proc
root@ubuntu:/# mount -t sysfs none /sys
root@ubuntu:/# mount -t devpts none /dev/pts
root@ubuntu:/# export HOME=/root
root@ubuntu:/# export LC_ALL=C
root@ubuntu:/# apt-get install --reinstall grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 264 not upgraded.
Need to get 759kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/main grub-pc i386 1.98+20100804-5ubuntu3 [759kB]
Fetched 759kB in 2s (375kB/s)   
Preconfiguring packages ...
(Reading database ... 133786 files and directories currently installed.)
Preparing to replace grub-pc 1.98+20100804-5ubuntu3 (using .../grub-pc_1.98+20100804-5ubuntu3_i386.deb) ...
Unpacking replacement grub-pc ...
Processing triggers for man-db ...
Setting up grub-pc (1.98+20100804-5ubuntu3) ...
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-25-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/Data: No such file or directory
ls: cannot access /media/Data: No such file or directory
ls: cannot access /media/Data: No such file or directory
ls: cannot access /media/Data: No such file or directory
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-25-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/Data: No such file or directory
ls: cannot access /media/Data: No such file or directory
ls: cannot access /media/Data: No such file or directory
ls: cannot access /media/Data: No such file or directory
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
root@ubuntu:/# umount /proc # if this doesn't work try umount -lf /proc
root@ubuntu:/# umount /sys
root@ubuntu:/# umount /dev/pts
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev
ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$ 

******************************************************************************************
******************************************************************************************
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,718,431   209,718,369   7 HPFS/NTFS
/dev/sda2         209,718,432   419,437,871   209,719,440   7 HPFS/NTFS
/dev/sda3         629,459,712 2,930,277,167 2,300,817,456   7 HPFS/NTFS
/dev/sda4         419,437,933   629,459,711   210,021,779   f W95 Ext d (LBA)
/dev/sda5         419,437,935   461,422,079    41,984,145  83 Linux
/dev/sda6         461,422,143   621,166,895   159,744,753  83 Linux
/dev/sda7         621,166,959   629,459,711     8,292,753  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6664413B64410F6D                       ntfs       HP_PAVILION                   
/dev/sda2        01CBCEB6C382A580                       ntfs       Win7                          
/dev/sda3        0478C00D78BFFF82                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        87550683-e128-479d-bc7a-42177d701eb6   ext4                                     
/dev/sda6        a1c5d813-9b19-421d-8d01-bf61624d8425   ext4                                     
/dev/sda7        bec48c13-4575-413f-a64f-5f1455e27e5e   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /FASTDETECT /USEPMTIMER /NOEXECUTE=OPTIN 
c:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS 

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
search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=87550683-e128-479d-bc7a-42177d701eb6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=87550683-e128-479d-bc7a-42177d701eb6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6664413b64410f6d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 01cbceb6c382a580
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
UUID=87550683-e128-479d-bc7a-42177d701eb6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=a1c5d813-9b19-421d-8d01-bf61624d8425 /home           ext4    defaults        0       2
/dev/sda7       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 234.2GB: boot/grub/core.img
 232.1GB: boot/grub/grub.cfg
 215.8GB: boot/initrd.img-2.6.35-25-generic-pae
 234.7GB: boot/vmlinuz-2.6.35-25-generic-pae
 215.8GB: initrd.img
 234.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ee 68 85 41 71 c4 83 4d  0a 3e 53 71 57 3f 92 48  |.h.Aq..M.>SqW?.H|
00000010  af 55 cd 73 b5 dc a0 a0  6c 8f 20 9a 41 0a 16 2a  |.U.s....l. .A..*|
00000020  e2 45 3e 83 6d 17 12 ac  cb d9 77 0a 1f aa 64 ac  |.E>.m.....w...d.|
00000030  67 e8 66 ec 27 2e 14 af  b6 21 5d c8 f2 30 32 0e  |g.f.'....!]..02.|
00000040  95 89 ad 4a 4a da d2 4f  90 a9 92 00 5f 86 bf 5a  |...JJ..O...._..Z|
00000050  49 f6 85 d0 d6 fc a2 7d  66 f8 bb 49 ad f0 18 80  |I......}f..I....|
00000060  3f 00 fa bc 50 0a 4f 8b  fd 31 62 de 8b 40 02 5d  |?...P.O..1b..@.]|
00000070  de 52 f0 f1 1c d0 0a 60  ae 30 24 54 6d 3c f6 90  |.R.....`.0$Tm<..|
00000080  66 9e 0a 46 36 bb 90 29  d3 89 bb b9 fb d6 f4 92  |f..F6..)........|
00000090  f0 1c ed 83 48 27 f0 ec  9a 1d 5d 59 a7 36 47 04  |....H'....]Y.6G.|
000000a0  4f 0b 6c 46 3d ec 3a 87  20 41 48 b5 ea 02 5d 97  |O.lF=.:. AH...].|
000000b0  ce c0 e6 ab 8e 22 f2 40  f0 f8 6d 19 e8 0f 47 32  |.....".@..m...G2|
000000c0  47 ae 2e 44 a3 54 cc 03  ac e1 7c e3 36 e9 0e 56  |G..D.T....|.6..V|
000000d0  9d d1 99 11 4a a4 83 18  1c f0 c5 74 bf 18 45 46  |....J......t..EF|
000000e0  73 21 14 0b d5 1a 0f 41  01 28 11 15 20 e7 d9 3f  |s!.....A.(.. ..?|
000000f0  77 9d 85 61 02 e9 86 8b  26 29 a5 1d b3 06 7d b6  |w..a....&)....}.|
00000100  74 d9 12 23 44 9f ed 0c  b0 34 c0 9a 20 21 6d e2  |t..#D....4.. !m.|
00000110  1b 09 fd f9 ca c4 c6 d0  c3 72 ee a2 8c 8f 48 c2  |.........r....H.|
00000120  a3 71 8d 7a fd b0 c0 cc  61 d4 21 9a 9e 40 f7 45  |.q.z....a.!..@.E|
00000130  5b 72 de 6a f9 37 3c 50  b7 20 d3 e6 30 ff ee 68  |[r.j.7<P. ..0..h|
00000140  db 1e 0b 4d df e1 fc 2f  a6 7f 47 5d 29 40 79 73  |...M.../..G])@ys|
00000150  5b f7 7c 54 85 4c 4f ab  a7 db ec 96 ae 26 f1 af  |[.|T.LO......&..|
00000160  a5 cb 95 4f 63 74 9e 02  d5 cb 0e 42 f0 69 24 38  |...Oct.....B.i$8|
00000170  94 30 08 43 94 f2 a2 46  84 12 82 39 11 82 f7 4e  |.0.C...F...9...N|
00000180  3a d7 d2 de d6 20 e9 01  c8 e1 9d 50 2c 40 c0 58  |:.... .....P,@.X|
00000190  21 e4 bb 28 a9 e9 24 3a  91 ac 90 33 ce 08 e6 c3  |!..(..$:...3....|
000001a0  fb 8d 73 e4 46 4a c9 e6  81 4e ad e6 b4 87 5f 10  |..s.FJ...N...._.|
000001b0  36 7f fc 8d ed 01 10 ff  b7 4f dc 0c 46 da 00 0f  |6........O..F...|
000001c0  ff ff 83 0f ff ff 02 00  00 00 91 a0 80 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff 93 a0  80 02 30 83 85 09 00 00  |..........0.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by Quackers on 2011-02-26
You've been busy!
Please boot from the live cd and open a terminal and copy/paste these commands in, one line at a time, pressing enter after each line.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
You will notice a difference in the second command to the one you've been trying.

Unfortunately, due to your multiple tries, it may be necessary to purge and then re-install grub, if the above commands don't have any effect.
See how it goes :-)

---

### Post by John4582 on 2011-02-26
Should I update Grub before rebooting?[FONT=monospace]

Not sure how to get to root from a terminal and update Grub.
[/FONT]

---

### Post by Quackers on 2011-02-26
You don't need root to update grub. Also, you can't update grub from a live cd desktop. Just reboot and see what appears in the grub menu.

---

### Post by John4582 on 2011-02-26
Ok, Thanks Quackers, be right back after boot.

---

### Post by Quackers on 2011-02-26
No problem, here's hoping :-)
It should actually boot direct into Ubuntu, with any luck!

---

### Post by John4582 on 2011-02-26
Same results and the boot_info_script looks the same. ????

---

### Post by Quackers on 2011-02-26
Can you post the new script output please? Thanks.
I think we'll go for a purge/re-install once I've had a look.

---

### Post by John4582 on 2011-02-26
I don't mind purging Grub and reinstalling it, I've done it before using Method 3 in the Grub rescue help. 

One other thing, I had to delete the Ubuntu partitions and recreate them with different sizes in order to get Grub to install and look in the right location for the boot files. So I don't know if purging and reinstalling again will cause any problems which will cause having to delete the partitions and recreating them but at this point I'm willing to try just about anything as long as Ubuntu is on it's own partition.

Thanks again for the help

---

### Post by John4582 on 2011-02-26
Here's the new script text.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,718,431   209,718,369   7 HPFS/NTFS
/dev/sda2         209,718,432   419,437,871   209,719,440   7 HPFS/NTFS
/dev/sda3         629,459,712 2,930,277,167 2,300,817,456   7 HPFS/NTFS
/dev/sda4         419,437,933   629,459,711   210,021,779   f W95 Ext d (LBA)
/dev/sda5         419,437,935   461,422,079    41,984,145  83 Linux
/dev/sda6         461,422,143   621,166,895   159,744,753  83 Linux
/dev/sda7         621,166,959   629,459,711     8,292,753  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6664413B64410F6D                       ntfs       HP_PAVILION                   
/dev/sda2        01CBCEB6C382A580                       ntfs       Win7                          
/dev/sda3        0478C00D78BFFF82                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        87550683-e128-479d-bc7a-42177d701eb6   ext4                                     
/dev/sda6        a1c5d813-9b19-421d-8d01-bf61624d8425   ext4                                     
/dev/sda7        bec48c13-4575-413f-a64f-5f1455e27e5e   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /FASTDETECT /USEPMTIMER /NOEXECUTE=OPTIN 
c:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS 

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
search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=87550683-e128-479d-bc7a-42177d701eb6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=87550683-e128-479d-bc7a-42177d701eb6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6664413b64410f6d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 01cbceb6c382a580
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
UUID=87550683-e128-479d-bc7a-42177d701eb6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=a1c5d813-9b19-421d-8d01-bf61624d8425 /home           ext4    defaults        0       2
/dev/sda7       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 234.2GB: boot/grub/core.img
 232.1GB: boot/grub/grub.cfg
 215.8GB: boot/initrd.img-2.6.35-25-generic-pae
 234.7GB: boot/vmlinuz-2.6.35-25-generic-pae
 215.8GB: initrd.img
 234.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ee 68 85 41 71 c4 83 4d  0a 3e 53 71 57 3f 92 48  |.h.Aq..M.>SqW?.H|
00000010  af 55 cd 73 b5 dc a0 a0  6c 8f 20 9a 41 0a 16 2a  |.U.s....l. .A..*|
00000020  e2 45 3e 83 6d 17 12 ac  cb d9 77 0a 1f aa 64 ac  |.E>.m.....w...d.|
00000030  67 e8 66 ec 27 2e 14 af  b6 21 5d c8 f2 30 32 0e  |g.f.'....!]..02.|
00000040  95 89 ad 4a 4a da d2 4f  90 a9 92 00 5f 86 bf 5a  |...JJ..O...._..Z|
00000050  49 f6 85 d0 d6 fc a2 7d  66 f8 bb 49 ad f0 18 80  |I......}f..I....|
00000060  3f 00 fa bc 50 0a 4f 8b  fd 31 62 de 8b 40 02 5d  |?...P.O..1b..@.]|
00000070  de 52 f0 f1 1c d0 0a 60  ae 30 24 54 6d 3c f6 90  |.R.....`.0$Tm<..|
00000080  66 9e 0a 46 36 bb 90 29  d3 89 bb b9 fb d6 f4 92  |f..F6..)........|
00000090  f0 1c ed 83 48 27 f0 ec  9a 1d 5d 59 a7 36 47 04  |....H'....]Y.6G.|
000000a0  4f 0b 6c 46 3d ec 3a 87  20 41 48 b5 ea 02 5d 97  |O.lF=.:. AH...].|
000000b0  ce c0 e6 ab 8e 22 f2 40  f0 f8 6d 19 e8 0f 47 32  |.....".@..m...G2|
000000c0  47 ae 2e 44 a3 54 cc 03  ac e1 7c e3 36 e9 0e 56  |G..D.T....|.6..V|
000000d0  9d d1 99 11 4a a4 83 18  1c f0 c5 74 bf 18 45 46  |....J......t..EF|
000000e0  73 21 14 0b d5 1a 0f 41  01 28 11 15 20 e7 d9 3f  |s!.....A.(.. ..?|
000000f0  77 9d 85 61 02 e9 86 8b  26 29 a5 1d b3 06 7d b6  |w..a....&)....}.|
00000100  74 d9 12 23 44 9f ed 0c  b0 34 c0 9a 20 21 6d e2  |t..#D....4.. !m.|
00000110  1b 09 fd f9 ca c4 c6 d0  c3 72 ee a2 8c 8f 48 c2  |.........r....H.|
00000120  a3 71 8d 7a fd b0 c0 cc  61 d4 21 9a 9e 40 f7 45  |.q.z....a.!..@.E|
00000130  5b 72 de 6a f9 37 3c 50  b7 20 d3 e6 30 ff ee 68  |[r.j.7<P. ..0..h|
00000140  db 1e 0b 4d df e1 fc 2f  a6 7f 47 5d 29 40 79 73  |...M.../..G])@ys|
00000150  5b f7 7c 54 85 4c 4f ab  a7 db ec 96 ae 26 f1 af  |[.|T.LO......&..|
00000160  a5 cb 95 4f 63 74 9e 02  d5 cb 0e 42 f0 69 24 38  |...Oct.....B.i$8|
00000170  94 30 08 43 94 f2 a2 46  84 12 82 39 11 82 f7 4e  |.0.C...F...9...N|
00000180  3a d7 d2 de d6 20 e9 01  c8 e1 9d 50 2c 40 c0 58  |:.... .....P,@.X|
00000190  21 e4 bb 28 a9 e9 24 3a  91 ac 90 33 ce 08 e6 c3  |!..(..$:...3....|
000001a0  fb 8d 73 e4 46 4a c9 e6  81 4e ad e6 b4 87 5f 10  |..s.FJ...N...._.|
000001b0  36 7f fc 8d ed 01 10 ff  b7 4f dc 0c 46 da 00 0f  |6........O..F...|
000001c0  ff ff 83 0f ff ff 02 00  00 00 91 a0 80 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff 93 a0  80 02 30 83 85 09 00 00  |..........0.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200 
```

Thanks

---

### Post by Quackers on 2011-02-26
There's a slightly shorter method than that now. Post the new script output please.
The re-created partitions shouldn't be a problem now.
One other possibility springs to mind. How old is the computer and its motherboard? Have you ever seen any limitation in the bios of 137GB?

---

### Post by John4582 on 2011-02-26
The computer is less than 3 months old. I built it so I could install and multi-boot Ubuntu. I also tried 10.04 LTS with the same results.

The exact MB is GA-MA785GM-US2H (rev. 3.3) BIOS version F11 (other Hardware listed in the post) 

No matter what I do when I reboot I end up at the **Grub rescue **prompt with **error: no such partition**. 

When I type "**ls**" at the **Grub rescue-> **prompt I get the following.[B](hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (fd0)

[/B]Ubuntu 10.10 is installed on **sda5 **or as far as Grub2 is concerned I think it's** (hd0, msdos5) **which at boot is not seen by Grub2[B]. ????

[/B]As far as limitation in the bios of 137GB, No, this is the latest rev of this board. Also I searched and other user are using this MB except I think theirs' is a (rev 1.1) an earlier version.

---

### Post by Quackers on 2011-02-26
Ok, we can try purging/re-installing grub using the commands below from the live cd desktop.
My concern is that msdos5 is not being seen. That's odd.

Please copy/paste each line separately into the terminal and press enter after each line.
Please make sure that you have a working internet connection first!
```
sudo mkdir /mnt/temp
sudo mount /dev/sda5 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo chroot /mnt/temp
```

Then please go here
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
and follow sections 2 to 8 in the Why Chroot section of that guide.
** At No7 just use the first command, not the second.

Good luck :-)

---

### Post by John4582 on 2011-02-26
I actually have sent PM about this issue to someone that is using the same MB but I've not heard back from them yet. Their user ID is  "lifeform23".

---

### Post by John4582 on 2011-02-26
Here a copy of the Terminal session and the script before I reboot. 

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# apt-get update
Hit http://us.archive.ubuntu.com maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Get:1 http://extras.ubuntu.com maverick Release.gpg [72B]
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en           
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Hit http://extras.ubuntu.com maverick Release                        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Hit http://security.ubuntu.com maverick-security/main Sources
Hit http://extras.ubuntu.com maverick/main Sources
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release
Hit http://us.archive.ubuntu.com maverick-updates Release                      
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources    
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://extras.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/main Sources
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Fetched 72B in 1s (59B/s)
Reading package lists... Done
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following package was automatically installed and is no longer required:
  linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 264 not upgraded.
After this operation, 5,804kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 133785 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 264 not upgraded.
Need to get 1,445kB/2,204kB of archives.
After this operation, 5,804kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/main grub-common i386 1.98+20100804-5ubuntu3 [1,445kB]
Fetched 1,445kB in 2s (579kB/s)        
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 133506 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98+20100804-5ubuntu3_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98+20100804-5ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up grub-common (1.98+20100804-5ubuntu3) ...
Setting up grub-pc (1.98+20100804-5ubuntu3) ...

Creating config file /etc/default/grub with new version
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-25-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/Data: No such file or directory
ls: cannot access /media/Data: No such file or directory
ls: cannot access /media/Data: No such file or directory
ls: cannot access /media/Data: No such file or directory
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-25-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/Data: No such file or directory
ls: cannot access /media/Data: No such file or directory
ls: cannot access /media/Data: No such file or directory
ls: cannot access /media/Data: No such file or directory
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
ubuntu@ubuntu:~$ 
```

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,718,431   209,718,369   7 HPFS/NTFS
/dev/sda2         209,718,432   419,437,871   209,719,440   7 HPFS/NTFS
/dev/sda3         629,459,712 2,930,277,167 2,300,817,456   7 HPFS/NTFS
/dev/sda4         419,437,933   629,459,711   210,021,779   f W95 Ext d (LBA)
/dev/sda5         419,437,935   461,422,079    41,984,145  83 Linux
/dev/sda6         461,422,143   621,166,895   159,744,753  83 Linux
/dev/sda7         621,166,959   629,459,711     8,292,753  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6664413B64410F6D                       ntfs       HP_PAVILION                   
/dev/sda2        01CBCEB6C382A580                       ntfs       Win7                          
/dev/sda3        0478C00D78BFFF82                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        87550683-e128-479d-bc7a-42177d701eb6   ext4                                     
/dev/sda6        a1c5d813-9b19-421d-8d01-bf61624d8425   ext4                                     
/dev/sda7        bec48c13-4575-413f-a64f-5f1455e27e5e   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /mnt/temp                ext4       (rw)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /FASTDETECT /USEPMTIMER /NOEXECUTE=OPTIN 
c:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS 

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
search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=87550683-e128-479d-bc7a-42177d701eb6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=87550683-e128-479d-bc7a-42177d701eb6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 87550683-e128-479d-bc7a-42177d701eb6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6664413b64410f6d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 01cbceb6c382a580
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
UUID=87550683-e128-479d-bc7a-42177d701eb6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=a1c5d813-9b19-421d-8d01-bf61624d8425 /home           ext4    defaults        0       2
/dev/sda7       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 217.1GB: boot/grub/core.img
 232.1GB: boot/grub/grub.cfg
 215.8GB: boot/initrd.img-2.6.35-25-generic-pae
 234.7GB: boot/vmlinuz-2.6.35-25-generic-pae
 215.8GB: initrd.img
 234.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ee 68 85 41 71 c4 83 4d  0a 3e 53 71 57 3f 92 48  |.h.Aq..M.>SqW?.H|
00000010  af 55 cd 73 b5 dc a0 a0  6c 8f 20 9a 41 0a 16 2a  |.U.s....l. .A..*|
00000020  e2 45 3e 83 6d 17 12 ac  cb d9 77 0a 1f aa 64 ac  |.E>.m.....w...d.|
00000030  67 e8 66 ec 27 2e 14 af  b6 21 5d c8 f2 30 32 0e  |g.f.'....!]..02.|
00000040  95 89 ad 4a 4a da d2 4f  90 a9 92 00 5f 86 bf 5a  |...JJ..O...._..Z|
00000050  49 f6 85 d0 d6 fc a2 7d  66 f8 bb 49 ad f0 18 80  |I......}f..I....|
00000060  3f 00 fa bc 50 0a 4f 8b  fd 31 62 de 8b 40 02 5d  |?...P.O..1b..@.]|
00000070  de 52 f0 f1 1c d0 0a 60  ae 30 24 54 6d 3c f6 90  |.R.....`.0$Tm<..|
00000080  66 9e 0a 46 36 bb 90 29  d3 89 bb b9 fb d6 f4 92  |f..F6..)........|
00000090  f0 1c ed 83 48 27 f0 ec  9a 1d 5d 59 a7 36 47 04  |....H'....]Y.6G.|
000000a0  4f 0b 6c 46 3d ec 3a 87  20 41 48 b5 ea 02 5d 97  |O.lF=.:. AH...].|
000000b0  ce c0 e6 ab 8e 22 f2 40  f0 f8 6d 19 e8 0f 47 32  |.....".@..m...G2|
000000c0  47 ae 2e 44 a3 54 cc 03  ac e1 7c e3 36 e9 0e 56  |G..D.T....|.6..V|
000000d0  9d d1 99 11 4a a4 83 18  1c f0 c5 74 bf 18 45 46  |....J......t..EF|
000000e0  73 21 14 0b d5 1a 0f 41  01 28 11 15 20 e7 d9 3f  |s!.....A.(.. ..?|
000000f0  77 9d 85 61 02 e9 86 8b  26 29 a5 1d b3 06 7d b6  |w..a....&)....}.|
00000100  74 d9 12 23 44 9f ed 0c  b0 34 c0 9a 20 21 6d e2  |t..#D....4.. !m.|
00000110  1b 09 fd f9 ca c4 c6 d0  c3 72 ee a2 8c 8f 48 c2  |.........r....H.|
00000120  a3 71 8d 7a fd b0 c0 cc  61 d4 21 9a 9e 40 f7 45  |.q.z....a.!..@.E|
00000130  5b 72 de 6a f9 37 3c 50  b7 20 d3 e6 30 ff ee 68  |[r.j.7<P. ..0..h|
00000140  db 1e 0b 4d df e1 fc 2f  a6 7f 47 5d 29 40 79 73  |...M.../..G])@ys|
00000150  5b f7 7c 54 85 4c 4f ab  a7 db ec 96 ae 26 f1 af  |[.|T.LO......&..|
00000160  a5 cb 95 4f 63 74 9e 02  d5 cb 0e 42 f0 69 24 38  |...Oct.....B.i$8|
00000170  94 30 08 43 94 f2 a2 46  84 12 82 39 11 82 f7 4e  |.0.C...F...9...N|
00000180  3a d7 d2 de d6 20 e9 01  c8 e1 9d 50 2c 40 c0 58  |:.... .....P,@.X|
00000190  21 e4 bb 28 a9 e9 24 3a  91 ac 90 33 ce 08 e6 c3  |!..(..$:...3....|
000001a0  fb 8d 73 e4 46 4a c9 e6  81 4e ad e6 b4 87 5f 10  |..s.FJ...N...._.|
000001b0  36 7f fc 8d ed 01 10 ff  b7 4f dc 0c 46 da 00 0f  |6........O..F...|
000001c0  ff ff 83 0f ff ff 02 00  00 00 91 a0 80 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff 93 a0  80 02 30 83 85 09 00 00  |..........0.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

Thanks again, I'm rebooting so be back in about 5 to 10 minutes.

---

### Post by Quackers on 2011-02-26
Ok, let's hope for good things :-)

---

### Post by John4582 on 2011-02-26
Same O same O. 

The script look about the same, should I post it?

Another thought is do you think I should try to purge Grub2 and revert to Grub 0.97. I think that's the version prior to Grub2. Just to see if it's a Gurb2 issue. Only thing I not sure how to do it or if Ubuntu 10.10 will boot with the old Grub.

Thanks again

---

### Post by Quackers on 2011-02-26
I thought it was taking a while :-(
No, grub legacy won't help, I think.
So you are still getting the error - no such partition? What does it show with "ls" at the grub rescue prompt? The same thing?

---

### Post by John4582 on 2011-02-26
Yes, for some reason Grub doesn't see (hd0,msdos5). **????**

---

### Post by John4582 on 2011-02-26
Do you think I should download and install an earlier version of Ubuntu that uses legacy Grub?

---

### Post by Quackers on 2011-02-26
The only thing that springs to my mind is a bios limit. 137GB seems a likely possibility, in that boot files installed after 137GB into the disc are not seen by bios. This means a separate boot partition needs to be created for those files, but nearer the beginning of the disc.
I have no experience with this problem, but I know a man who does :-)
I'll pm him and ask for suggestions. He may come up with another idea entirely.
I don't know if he's online at the moment, so any reply may not be immediate.
I would not do anything further with grub2 for the moment.

Edit, No, but do you have a spare disc or usb drive that you can install Ubuntu to. That might go some way to confirming my suspicions.

---

### Post by John4582 on 2011-02-26
Yes, I have 2 1TB drives that have backups on them that I was using while was reorganising my 1.5TB drive in prep for Ubuntu and Win7 which is basically the same as the 1.5TB drive (Seagate) except that their 5900 RPM instead of 7200 RPM drives. I bought them because I plan on building a Ubuntu Server 10.04 LTS after/if I get my new desktop working with Ubuntu ?.? version. I will work on cleaning one of them completely then giving Ubuntu the total drive to install on.

Both drives are mounted in my desktop they're just not connected so I will have to go off line for a bit to connect them to power and data cables. I took them off-line in order to give Grub less to think about in it's decision making process.

---

### Post by Quackers on 2011-02-26
I suspect that it will work ok if the installation is earlier in the disc.

Edit  You will need to install grub to the mbr of the new drive (possibly sdb, rather than sda) and change the bios to boot from that drive before your other hard drive.

---

### Post by John4582 on 2011-02-26
Do you think I should move my installations around and put Ubuntu first on the disk? I'm not sure it makes a difference because Grub see (hd0,msdos3) which is last on the disk now. The difference between them is that xp, win7 and data are on primary partitions and Ubuntu is on a Extended partition. Which will still be (hd0,msdos5) no matter where it is located on the drive.

---

### Post by Quackers on 2011-02-26
Note the edit in my last post.
It may come to a total re-install, with a new small boot partition, to get around the limit (if there is one). The fresh install (with grub properly installed to the new drive) will give us a clue.

---

### Post by John4582 on 2011-02-26
Yes I seen your earlier post and I can and will do that but it will probably take the rest of the day so I will be off line for awhile. 

Did you see my earlier post?
> The computer is less than 3 months old. I built it so I could install  and multi-boot Ubuntu. I also tried 10.04 LTS with the same results.

The exact MB is GA-MA785GM-US2H (rev. 3.3) BIOS version F11 (other Hardware listed in the post) 

No matter what I do when I reboot I end up at the **Grub rescue **prompt with **error: no such partition**. 

When I type "**ls**" at the **Grub rescue-> **prompt I get the following.[B](hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (fd0)

[/B]Ubuntu 10.10 is installed on **sda5 **or as far as Grub2 is concerned I think it's** (hd0, msdos5) **which at boot is not seen by Grub2[B]. ????

[/B]As far as limitation in the bios of 137GB, No, this is the latest rev  of this board. Also I searched and other user are using this MB except I  think theirs' is a (rev 1.1) an earlier version. This is why I believe it is a Grub issue, not a hardware issue.

---

### Post by oldfred on 2011-02-26
If it is a new system, it should not be the BIOS 137GB limit. But it may be some setting in BIOS. Everything I see in boot script looks ok, and it is very strange the grub on booting cannot see sda5. It does not boot and the ls command does not show it.

I have saved comments from others with issues, see if any apply:
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
core unlocker feature on asus m4a87td usb3 was causing the problem
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happened to set it on)

Generally AHCI should work. It worked for me but then I could not boot XP as I had not added the new driver.
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.

---

### Post by Quackers on 2011-02-26
Yes, I saw that post, and understand what you said. It's just that the only thing that explains it not recognising sda5, to my mind, is a bios limit that stops the recognition of boot files installed after that limit. There are 2 limits, as I understand it. On older systems it was 8GB I think, whilst on newer systems the limit was 137GB for some reason. There can also be a problem with large drives too. 
Of course, I could be on the wrong tack completely - it's happened before :-)

Aha, the cavalry arrived :-) Thanks oldfred!

---

### Post by John4582 on 2011-02-26
Hi Oldfred,
My MB has a fairly robust BIOS so I can load the **"Fail Safe Setting"** and see what happens. I don't have any raid and never have with this computer. I don't have bitlocker on this computer that I know of. I don't believe AHCI is activated I have the BIOS set to Native IDE. Most of the settings in the BIOS is set to AUTO in most cases. As for changing newer BIOS SATA from 6 Gbs to a 3Gbs, I believe mine is set to 3Gbs.

Thanks for your help.

---

### Post by John4582 on 2011-02-26
I also thought about a BIOS issue but this rev of my MB was released mid 2010 I believe so the limits as to drives shouldn't exist. ???

I think I should take your suggestion and try another drive and give Ubuntu the whole drive and see what happens.

---

### Post by Quackers on 2011-02-26
AHCI may be worth a try first.

---

### Post by John4582 on 2011-02-26
> AHCI may be worth a try first.

Are you saying to install/activate ACHI??? I would think that that would only make things worst. ????

---

### Post by oldfred on 2011-02-26
On my system with a 3 year old motherboard, AHCI worked just fine for Ubuntu, but I did not have AHCI driver for XP.

I have seen several users with 1 or 2TB drives where they allocated the entire drive to / (root) and had issues. I believe in small root partitions and large /home or /data partitions, just to keep the files most used together on the drive. Less work for hard drive, not really any speed improvement you can see. The real limits on a desktop are how fast you can type or download from Internet. If compiling lots of code then an SSD makes a huge difference.  I do not compile but reboot different versions, so I am thinking about an SSD for next upgrade.

---

### Post by Quackers on 2011-02-26
On a previous system of mine I could change from and to AHCI without a problem. However with another I could not. All I can say is heed any warnings if you try it, and make sure your backups work.

---

### Post by John4582 on 2011-02-26
> **oldfred said:**
> If it is a new system, it should not be the BIOS 137GB limit. But it may be some setting in BIOS. Everything I see in boot script looks ok, and it is very strange the grub on booting cannot see sda5. It does not boot and the ls command does not show it.

NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
not have AHCI driver.

As far as NTFS partition needs chkdsk, gparted has no problem seeing the drive and all the partitions, even now after Ubuntu is installed.

---

### Post by John4582 on 2011-02-26
> **Quackers said:**
> On a previous system of mine I could change from and to AHCI without a problem. However with another I could not. All I can say is heed any warnings if you try it, and make sure your backups work.

I had the same problem as Oldfred did with AHCI & XP when I first booted after the new computer build that's why I changed the BIOS to Native IDE because I didn't think I really needed AHCI. 

I confused now, I would think that enabling AHCI would add another layer to the Grub install which is not necessary at this point since every thing else is working ok.

Really Guys I appreciate the help, please don't desert me. The following is a link to the MB I'm working with:
[http://www.gigabyte.com/products/product-page.aspx?pid=3447#ov](http://www.gigabyte.com/products/product-page.aspx?pid=3447#ov)

---

### Post by Quackers on 2011-02-26
I don't think grub will care whether AHCI is enabled or not. I don't think grub is the problem. Oldfred has a point though, in that a driver (or a registry edit) may be required to boot XP after enabling AHCI.

---

### Post by John4582 on 2011-02-26
> **oldfred said:**
> On my system with a 3 year old motherboard, AHCI worked just fine for Ubuntu, but I did not have AHCI driver for XP.

I have seen several users with 1 or 2TB drives where they allocated the entire drive to / (root) and had issues. I believe in small root partitions and large /home or /data partitions, just to keep the files most used together on the drive. Less work for hard drive, not really any speed improvement you can see. The real limits on a desktop are how fast you can type or download from Internet. If compiling lots of code then an SSD makes a huge difference.  I do not compile but reboot different versions, so I am thinking about an SSD for next upgrade.

I agree, the following is the way my drive is right now.

sda1 100GB XP OS (primary)
sda2 100GB Win7 OS  (primary)
sda3 1+TB Data  (primary) **shared by all OSs including Ubuntu**.
sda4 extended partition
[INDENT]sda5 20 GB Ext4
sda6 76 GB Ext4
sda7 4 GB Ext4
[/INDENT]

---

### Post by John4582 on 2011-02-26
> **Quackers said:**
> I don't think grub will care whether AHCI is enabled or not. I don't think grub is the problem. Oldfred has a point though, in that a driver (or a registry edit) may be required to boot XP after enabling AHCI.

Oldfred is right that's why I enabled Native IDE so I didn't need to locate and install drivers AHCI for XP.

---

### Post by John4582 on 2011-02-26
What every I do I would like to do it without having to boot back into either windows OS because I would have to overwrite the MBR in order to get back into windows.

---

### Post by Quackers on 2011-02-26
I would first try installing to another drive, as discussed previously, if you don't have the necessary driver for XP. At least that way the original main hard drive is untouched for the moment. But remember to install grub to the new HDD, not sda, and also change the bios to boot from the usb HDD before booting the new drive.

---

### Post by John4582 on 2011-02-26
> **Quackers said:**
> I would first try installing to another drive, as discussed previously, if you don't have the necessary driver for XP. At least that way the original main hard drive is untouched for the moment. But remember to install grub to the new HDD, not sda, and also change the bios to boot from the usb HDD before booting the new drive.

??? change the bios to boot from the usb HDD before booting the new drive, I'm not using a USB and never have to boot anything from USB. Only the Live CD / other CD like Ultimate Boot CD. 

If I go to another drive I would make a small root, a smaller swap, and a large home partition and maybe copy the XP partition so I can have a primary (XP) and a Logical drive for Ubuntu.

First getting XP to boot then installing Ubuntu. This way I can take the current drive out of the picture while at the same time keeping the Primary and Logical drive configuration.

I may even try the activating the BIOS "Fail Safe" configuration first just to see if it make any difference to Grub.

---

### Post by oldfred on 2011-02-26
We have had some weird things like a CD in CD drive and on booting it wants to run chkdsk on CD. Sometimes BIOS has floppy enabled and you do not have a floppy so it gets lost. 

Some have been able to get to menu. And then they edit out search line.

To avoid some of the boot issues you may want to try Supergrub. I have not used it since grub legacy days and he did not have a grub2 version for a while. Now he does and I understand it works pretty well. Just be sure to get to new version.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

---

### Post by Quackers on 2011-02-26
If you do that, and then Ubuntu won't boot, you will be in the same position you are in now, and know no more. I suggested installing Ubuntu to another drive (usb or whatever) to see if UIbuntu then boots (after changing the boot order in the bios so that the new drive boots before the present drive. If it boots, well ok, if it doesn't boot and has the same error message as you get now, then there is something else causing it.

---

### Post by John4582 on 2011-02-26
> **oldfred said:**
> We have had some weird things like a CD in CD drive and on booting it wants to run chkdsk on CD. Sometimes BIOS has floppy enabled and you do not have a floppy so it gets lost. 

Some have been able to get to menu. And then they edit out search line.

To avoid some of the boot issues you may want to try Supergrub. I have not used it since grub legacy days and he did not have a grub2 version for a while. Now he does and I understand it works pretty well. Just be sure to get to new version.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

I do have a 3.5" floppy and the BIOS hits everything just to make sure they're there but I only have a first boot item and a second boot item in case the BIOS fails to find a boot-able item in the first location it will try the second. I can however set just about anything as boot-able but only two items at a time. Right now the BIOS is set to HDD 0 first then if fails to find a boot-able item it tries the CDROM. I can use the F12 key to boot from just any source that's available to the computer.

---

### Post by John4582 on 2011-02-26
> **Quackers said:**
> If you do that, and then Ubuntu won't boot, you will be in the same position you are in now, and know no more. I suggested installing Ubuntu to another drive (usb or whatever) to see if UIbuntu then boots (after changing the boot order in the bios so that the new drive boots before the present drive. If it boots, well ok, if it doesn't boot and has the same error message as you get now, then there is something else causing it.

I have a 2GB USB stick but I'm not sure if I could load and boot Ubuntu from it as it's several years old and a cheep one at that.

---

### Post by Quackers on 2011-02-26
2GB would be too small for an Ubuntu installation. It would fail to install.

---

### Post by oldfred on 2011-02-26
Do you have another mode beside native IDE. that may be putting into the mode where it cannot read the rest of the drive. Does it boot in AHCI mode?


Some more notes that I saved from others:
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

---

### Post by John4582 on 2011-02-26
I almost forgot, I do have a 80GB 2.5" SATA drive in a dual bay dock connected via eSATE port on my Desktop that I can power up and copy the data to my 1.5TB drive then format it and try installing Ubuntu there. At least I think the BIOS will boot from the eSATA dock.

---

### Post by John4582 on 2011-02-26
> **oldfred said:**
> Do you have another mode beside native IDE. that may be putting into the mode where it cannot read the rest of the drive. Does it boot in AHCI mode?


Some more notes that I saved from others:
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).


I'll have to check, but I think I have three options in the BIOS. That RAID (multiple vision of RAID), AHCI, and Native IDE.

I do have a 3.5" floppy drive and would be happy to install the drivers if I knew where to get them even if it mean start from scratch with Ubuntu.

Thank you guys again for your help.

---

### Post by John4582 on 2011-02-26
That's what I thought. Did you see my other post about the eSATA dock?

---

### Post by Quackers on 2011-02-26
Yes. You will need to make sure you can boot that from bios though. I thought you said you had a backup drive you could maybe use?

---

### Post by John4582 on 2011-02-26
> **Quackers said:**
> Yes. You will need to make sure you can boot that from bios though. I thought you said you had a backup drive you could maybe use?

I do, I just think that it will be faster and safer as to data loss if I use the eSATA doc. 50GB of data to move verses almost 400GB. And yes I'm 99% sure I can boot from it.

---

### Post by Quackers on 2011-02-26
50GB of data to move? Why? Just install Ubuntu and see if it boots.

---

### Post by John4582 on 2011-02-26
At this point I think I will use the rest of the day trying some of the things we've talked about then post back here when/if I find a solution.

Plan:

First try the BIOS setting to see if I can solve the issue with the BIOS.

Then if that doesn't work try the 80GB drive in the eSATA dock (this would eliminate the 137GB possible issue with the BIOS).

If That doesn't work move the 400GB of data off the 1TB drive, format it, and start from scratch.

I think that this is the best plan of attack in order to find the best solution that others can also use.

Really thanks allot guys for the help.

---

### Post by Quackers on 2011-02-26
You are definitely welcome.
If you format and start again, won't you end up with partitions in the same places, and maybe the same problem?

---

### Post by John4582 on 2011-02-26
> **Quackers said:**
> 50GB of data to move? Why? Just install Ubuntu and see if it boots.

I would be worried about losing the data because it has a NTFS file system and I/Ubuntu would need an Ext4 file system. Also it had XP on it at one time and still has a MBR on it that I think I should wipe clean.

Another thing I just thought about is that I used Seagate Tools to format and ready the 1.5TB and both 1TB drives for uses. 
Then used a Seagate Tools to clone XP on the 1.5TB drive.

---

### Post by John4582 on 2011-02-26
> **Quackers said:**
> You are definitely welcome.
If you format and start again, won't you end up with partitions in the same places, and maybe the same problem?

I don't think so because I will be using a different drive with only one Primary and a Logical partition with Ubuntu in it. Plus a different MBR.

Another thing I might try is taking my current 1.5TB (drive I'm trying to boot now) and booting into my Ultimate Boot CD and fixing my MBR so windows will boot again then boot the Ubuntu Live CD and purge Grub again and reinstall it to make sure that they're nothing left in the MBR that may be causing this issue. I say this because at one point Grub complained about FlexNet in sector 32 which no longer is showing up in the script file. I may even try this first, what you think.

---

### Post by John4582 on 2011-02-26
As much as I would like to get my system working with Ubuntu, I'm really trying to find a solution that will/can work for other people if possible which can only be done by identifying the real issue not just implementing a workaround.

---

### Post by John4582 on 2011-02-26
> **oldfred said:**
> Do you have another mode beside native IDE. that may be putting into the mode where it cannot read the rest of the drive. Does it boot in AHCI mode?


Some more notes that I saved from others:
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).
  
**First** of all I want to **thank both of you guys** for all the help and sticking with me.

**Second**, I want you to know that I **booted up from the HDD** and I'm **running off the HDD Ubuntu 10.10 **OS **right now**.

**Oldfred** was right on, it was the **SATA Native IDE** setting that **hosed Grub**. I had to set the **OnChip SATA Type** to **AHCI** in order to boot using Grub. As for the **OnChip SATA Port 4/5 Type** setting it **doesn**'t have any **affect** on **Grub**, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.

As for XP, well XP is hosed until I find the ACHI drivers for XP and install them.

Which will require:[INDENT]Going into have BIOS and changing the OnChip SATA Type back to Native IDE
Modifying the MBR so I can boot into XP
Installing the AHCI drivers for XP and testing to make sure they work
Then booting back into Ubuntu via the Live CD and reinstalling Grub back into the MBR in the root of sda.
[/INDENT]I think we can call this one Solved.

Once again Thank You, Thank You, Thank both of You very much.

One more thing. Do either one of you know where to document this solution so it will be easily found by others with a smiler issue? Reason I ask is, I almost went for the /boot partition which might/might not have work and changing the BIOS (if the option exist) is much easier, safer, and known to work. Also once I find the drivers I can post a link to them in case someone else needs them or maybe Ubuntu can host them in their hardware drivers for multi-boot people.

---

### Post by Quackers on 2011-02-27
Interesting, thanks for the feedback, and well done :-)
If you mark the thread as solved, using the Thread Tools near the top of the page, it will help people when searching. If you find the drivers just post a link in here.

---

### Post by oldfred on 2011-02-27
If you have different settings for different sets of ports plug the XP drive in to either ports 4/5 and set those ports to IDE mode.

---

### Post by John4582 on 2011-02-27
First I want to thank you Quackers and Oldfred for all your help. 
 
I used the Thread Tool and marked it solved only because we identified the issue. I still can't Multi-Boot my installed version of XP, Win7, and a new install of Ubuntu 10.10 unless I want to reinstall both XP & Win7 first. ????  Grub will not boot anything unless I have SATA set to AHCI in the BIOS and XP & Win7 wont boot unless I have SATA set to IDE.
 
I know, it makes no since to me either. Apparently if you install windows with SATA in IDE mode you can't just flip the mode back to AHCI without installing the AHCI drivers, totally understandable, makes since to me, you need drivers. Issue is that the drivers for AHCI need to be installed when the system is installed, not sure why but OK, I don't build OS's I just install and use them. 
 
What has me hosed is, that when you install windows you either install it with SATA set in the BIOS to IDE, AHCI or RAID. OK, the problem for me anyway is, at least for an XP install, if I understand it right both AHCI & RAID needs the drivers on a floppy, SATA has to be set in the BIOS to AHCI or RAID and you have to press the F6 key during the install in order to install the drivers. Needless to say, my XP install was done with SATA set to IDE mode, therefore when I installed Win7 I left SATA set to IDE because I thought that really didn't need AHCI or RAID because I've used windows since 1985, yes back when you spent a lot of time at the MSDOS prompt, and I've never needed either AHCI or RAID, until now.?????

Question - Do either one of you know if the Ubuntu install keeps a log file and if so how/where can I open it so I can try to determine what is causing this issue? 
 
Now the part that's really confusing to me. 
 
    1. If you install Grub with SATA set to IDE mode in the BIOS and everything installs with no complaints/warnings from the installer about SATA being set to IDE mode, then why wont Grub boot up with SATA set to IDE mode in the BIOS???? 

    2. Why do I have to change the SATA setting in the BIOS to AHIC after install in order for Grub to see the Logical partitions so Grub can boot, while at the same time causing Windows NOT to boot???? 

    3. Am I the only person that has Windows installed in primary partitions and Ubuntu installed in a Logical partitions with SATA set to IDE during the Windows OS's installation so I can't install & boot Grub without reinstalling the Windows OS's????

---

### Post by John4582 on 2011-02-27
> **oldfred said:**
> If you have different settings for different sets of ports plug the XP drive in to either ports 4/5 and set those ports to IDE mode.

I do have different settings for different sets of ports but XP, Win7, Data, and Ubuntu are all on the same drive and I don't want to use another 1TB drive just because Grub2 needs SATA set to AHCI in the BIOS.

If there's no other solution I guess I will have to find another Linux system that doesn't use Grub2. I deleted the Ubuntu partitions about a hour ago and reinstalled it without booting to the Try Ubuntu frist and after it finished a lot of IO errors scrolled on the screen and Grub still wont boot without SATA set to AHCI in the BIOS.????

---

### Post by oldfred on 2011-02-27
I think we are back to what quacker's originally thought ( and i assumed it was new so it did not apply) of the 137GB BIOS limit on old computers. 
If you install either a separate small boot partition or the full system partition within the limit then there is no issue. Many of us just install a small windows system partition and a small Ubuntu system / partition and keep data in shared NTFS for windows data and either /home or a separate /data. 

If you want to create a small /boot partition within the 137GB limit or a full Ubuntu / (root) partition of 20GB inside the 137GB limit that would test the theory. 

I did find with google many sites with instructions on installing the drivers after the fact for windows XP. I thought win7 worked automatically, but do not have win7.

HOWTO: enable AHCI mode after installing Windows 
However, in the real world the performance difference isn't huge.
[http://forums.pcper.com/showthread.php?t=444831](http://forums.pcper.com/showthread.php?t=444831)
Also Google search on xp  - ahci after install

---

### Post by John4582 on 2011-02-27
> **oldfred said:**
> I think we are back to what quacker's originally thought ( and i assumed it was new so it did not apply) of the 137GB BIOS limit on old computers. 

My computer is new, less than 3 months old; the motherboard I have is a Gigabyte GA-MA785GM-US2H (rev. 3.3) and if I not mistaken was released mid 2010. The HDD I'm using is a Seagate Barracuda 7200.11 SATA 3Gb/s 32MB Cache 1.5-TB Hard Drive. The CPU is an AMD Phenom X4 9850 2.5 GHz. The memory is Crucial 2 X 2GB DDR2 800MHz for a total of 4096MB. Based on these specs I think we can rule out the 137GB limit unless it a Grub limit.

> **oldfred said:**
> If you install either a separate small boot partition or the full system partition within the limit then there is no issue. Many of us just install a small windows system partition and a small Ubuntu system / partition and keep data in shared NTFS for windows data and either /home or a separate /data.

If you want to create a small /boot partition within the 137GB limit or a full Ubuntu / (root) partition of 20GB inside the 137GB limit that would test the theory.  

Not sure what you are trying to say here.????
My current HDD partitions are as Follows:

[LIST]
[*]             hd0                               -> 1.5 TB
[LIST]
[*]                      XP Pro                                   -> 100 GB partition
[*]                      Win7 Pro                             -> 100 GB partiton
[*]                      Ubuntu                                    -> 100.15 GB extended partition
[LIST]
[*]              "/"                                  -> 19.09 GB extended partition
[*]                                        "/home                   -> 77.30 GB extended partition
[*]                                          Linux-swap   -> 3.75 GB extended partition
[/LIST]
 
[*]     Data                                               -> 1.07 TB
[/LIST]
 
[/LIST]
Thanks again guys

---

### Post by John4582 on 2011-02-27
> **oldfred said:**
> HOWTO: enable AHCI mode after installing Windows 
However, in the real world the performance difference isn't huge.
[http://forums.pcper.com/showthread.php?t=444831](http://forums.pcper.com/showthread.php?t=444831)
Also Google search on xp  - ahci after install

I search the Internet too which at first it sounded like a possible solution except for one thing, my AHCI drivers are by ATI which like everything else AMD dose, its hard to back-door their drivers.

---

### Post by Zyzzy on 2011-03-01
The same problem here. I have installed Windows XP with IDE mode. After installing new Ubuntu 10.10, grub2 is not working, displaying "Unknown filesystem" and going to rescue console. 
When I change IDE mode to AHCI in BIOS, grub is working and I am able to boot Ubuntu, but not XP, it goes to bluescreen during boot (unless AHCI drivers are installed, i presume). 

> **oldfred said:**
> I think we are back to what quacker's originally  thought ( and i assumed it was new so it did not apply) of the 137GB  BIOS limit on old computers. 
If you install either a separate small boot partition or the full system  partition within the limit then there is no issue. Many of us just  install a small windows system partition and a small Ubuntu system /  partition and keep data in shared NTFS for windows data and either /home  or a separate /data. 

I have 500GB SATA disk:
1. partition - 64GiB - Win XP
2. partition - 64GiB - Ubuntu
3. partition - 32GiB - empty (reserved for other OS) 
4. partition - logical

So I don't think that this problem is about 137GB limit, because both WinXP and Ubuntu partitions fits into this 137GB limit (accurately). Don't know why grub2 is not able to work with IDE mode.

System: MB Gigabyte GA-MA770-UD3, AMD Phenom II X4, 2GB RAM, 500GB Samsung SpinPoint

---

### Post by John4582 on 2011-03-01
> **Zyzzy said:**
> The same problem here. I have nstalled Windows XP with IDE mode. After installing new Ubuntu 10.10, grub2 is not working, displaying "Unknown filesystem" and going to rescue console. 
When I change IDE mode to AHCI in BIOS, grub is working and I am able to boot Ubuntu, but not XP, it goes to bluescreen during boot (unless AHCI drivers are installed, i presume). 

I have 500GB SATA disk:

First, if you are get an Unknown filesystem error then you might be having another problem because the error I'm getting is "error: no such partition", although setting SATA to AHCI in the BIOS resolves both errors so the same solution may fix both our problems. **(Please post back here if you find a solution to your problem)** and I will keep this Thread update with all my findings. It might help to document your Build specs i.e. MB, CPU, HDD, Partitions size and type, and OS(s) unless you have it documented in another post, the at least put a link to that post in this post and I'll update your post with my finding.

I'm still working on this issue. I have 2 1TB SATA Seagate HDD cleared off, 1 Formatted as an Extended Partition and the other as a Primary Partition. Also a 80 GB FUJITSU MHV2080BH PL ATA Drive in an external SATA Dock connected to my Desktop (Looks like a internal drive to the BIOS) which I plan on testing with formatted first as an Extended Partition partition and if that doesn't work I will format it as a Primary partition try that. I planing on spending as much time as I can over the next few days to get to the bottom of what is causing this issue. 

Like I said earlier:
> 
1. If you install Grub with SATA set to IDE mode in the BIOS and  everything installs with no complaints/warnings from the installer about  SATA being set to IDE mode, then why wont Grub boot up with SATA set to  IDE mode in the BIOS???? 

    2. Why do I have to change the SATA setting in the BIOS to AHIC  after install in order for Grub to see the Logical partitions so Grub  can boot, while at the same time causing Windows NOT to boot???? 

    3. Am I the only person that has Windows installed in primary  partitions and Ubuntu installed in a Logical partitions with SATA set to  IDE during the Windows OS's installation so I can't install & boot  Grub without reinstalling the Windows OS's????     I've also written Gigabyte (the MFG of my MB, which is a GA-MA785GM-US2H (rev. 3.3) released mid 2010 I think but I've not heard back from them yet.

---

### Post by John4582 on 2011-03-01
Zyzzy also NOTE.

> **John4582 said:**
> I do have different settings for different sets of ports but XP, Win7, Data, and Ubuntu are all on the same drive and I don't want to use another 1TB drive just because Grub2 needs SATA set to AHCI in the BIOS.

If there's no other solution I guess I will have to find another Linux system that doesn't use Grub2. I deleted the Ubuntu partitions about a hour ago and reinstalled it without booting to the Try Ubuntu frist and after it finished a lot of IO errors scrolled on the screen and Grub still wont boot without SATA set to AHCI in the BIOS.????

Note the last sentence above.
> **I deleted the Ubuntu partitions** about a hour ago and **reinstalled **it ** without** **booting **to the **Try Ubuntu frist** and after it finished a **lot of  IO errors scrolled on the screen** and Grub still wont boot without SATA  set to AHCI in the BIOS.????This leads me to believe something in the Gurb2 is not being setup/defined right/correctly, I could be wrong since we are both using Gigabyte MB's . Also I should clarify that the error scrolled after clicking restart and not during the install. No errors if installing while in the **Try Ubuntu **then clicking restart after install.

---

### Post by Zyzzy on 2011-03-01
> **John4582 said:**
> First, if you are get an Unknown filesystem error then you might be having another problem because the error I'm getting is "error: no such partition", although setting SATA to AHCI in the BIOS resolves both errors so the same solution may fix both our problems. **(Please post back here if you find a solution to your problem)**
Of course, if I know the solution, I will write here. But I can't give it much time now... :-( For now, I'm working in Win XP after fixing MBR with WinXP CD. 

Yes, solution may be the same. Although errors are different, symptoms are very similar. With my previous post, I just want to tell it doesn't seem to me that the problem is caused by 137GB limit.

I have tried to install Ubuntu only after booting from LiveCD->Try Ubuntu first. No errors, everything looks to be OK. When it doesn't work, I reinslalled choosing the destination for grub to sda2 (my ext4 partition with Ububtu), but no change... Boot Info Script gives me this "error" - the same as yours in first post:
"**Grub 2 is installed in the boot sector of sda2 and looks at sector ... of the same hard drive for core.img, but core.img can not be found at this location.**"

In rescue console, ls command also produces this output: 
**(hd0) (hd0,msdos1) (hd0,msdos2) (hd0,msdos3)**

> I planing on spending as much time as I can over the next few days to get to the bottom of what is causing this issue. 
I am not Linux guru, so you will be my "Hero of the day" if you can solve this issue :-)

---

### Post by Zyzzy on 2011-03-01
Maybe, changing **Access mode** from **Auto** to **Large** on IDE disk in BIOS is the key... ???

---

### Post by John4582 on 2011-03-01
Results of first test:
 
 After install Results:[INDENT]    Press the F12 key to access BIOS boot device and selected -> + Hard Drive -> 80GB drive Ubuntu is installed on.
Grub2 booted -> Selected Ubuntu and Ubuntu booted up no problems identified.
Rebooted without applying update via Update Manager.
Press the F12 key to access BIOS boot device and selected -> + Hard Drive -> 80GB
Grub2 booted -> Selected Windows 7 -> Windows 7 -> Win7 booted up up no problems identified.
Rebooted
[/INDENT][INDENT]    Press the F12 key to access BIOS boot device and selected -> + Hard Drive -> 80GB drive Ubuntu is installed on.
Grub2 booted -> Selected Windows 7 -> Windows 7 -> Earlier Vision Of Windows -> Windows XP Media Center 2005[INDENT]**Note: System beeped and rebooted **(Not sure what the problems is – ignored).
[/INDENT]Rebooted
Let the BIOS default HDD with XP/Win7old/Win7D/Data
Selected Windows 7 booted up no problems identified.
Rebooted
Let the BIOS default HDD with XP/Win7old/Win7D/Data
Selected Windows 7 -> Earlier Vision Of Windows -> Windows XP Media Center 2005 booted up no problems identified.
Rebooted
Press the F12 key to access BIOS boot device and selected -> + Hard Drive -> 80GB drive Ubuntu is installed on.
Grub2 booted -> Selected Ubuntu and Ubuntu booted up no problems identified.
Applied update via Ubuntu Update Manager.
Rebooted
Press the F12 key to access BIOS boot device and selected -> + Hard Drive -> 80GB drive Ubuntu is installed on.
Grub2 booted -> Selected Windows 7 -> Windows 7 -> Win7 booted up up no problems Identified.
[/INDENT]**Note: Let the BIOS default to default HDD with  XP/Win7old/Win7D/Data everything boots as if Ubuntu is not installed.  Also Windows XP Media Center 2005 will not boot via Grub2 (ignored -  doesn't matter for testing - I'm sure it could be fix if needed for  testing all the the install scenarios).**
 

 Following Code sections are for information/documentation only:
```
After booting into Ubuntu 10.10 Live CD and before doing anything.
Information from Ubuntu Try boot without Ubuntu installed on any drive
All drives SATA except sda which is 80 GB unallocated PL ATA mounted in  an external SATA dock (BIOS set to LBA also this is the only drive BIOS  allowed to be set to LBA).
**********************************************************************************
!!!!!!!!!!!!NOTE:                                                                                     *
sda is the ONLY drive seen by GParted upon booting into Live CD  *
!!!!!!!!End NOTE:                                                                                  *
**********************************************************************************
Why was GParted only able to see sda which is sitting in an external  SATA dock connected via SATA cable to back of desktop to the MB IO SATA  port and the only unallocated drive in system.

Information about drives from boot_info_script055 Follows with some in-line note where indicated for additional information.

EVERYTHING ABOVE THIS LINE WAS ADDED FOR INFORMATION ALSO NOTES IN BOLD  TEXT REFER TO THAT SECTION ONLY ADD BY ME AND IS NOT PART OF THE  boot_info_script055 OUTPUT.
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________
**Note: Added OS to end of each line.**

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   209,718,431   209,718,369   7 HPFS/NTFS XP
/dev/sdb2         209,718,432   419,437,871   209,719,440   7 HPFS/NTFS **Win7Old**
/dev/sdb3         419,740,272   629,459,711   209,719,440   7 HPFS/NTFS **Win7D**
/dev/sdb4         629,459,712 2,930,277,167 2,300,817,456   7 HPFS/NTFS **Data**

Drive: sdc ___________________ _____________________________________________________
[B]Note: Formatted just to see what the boot_info_script055 will see.
      Also this drive need to be ran through Testdisk and changed to 16  heads, 63 sectors/track, ????? cylinders. The 255 heads, 63  sectors/track, 121601 cylinders is due to a previos clone of what is now  known as "sdd" and originally looked like what is now known as "sdb"
       Plan on testing install before Heads, Sectors, & Cylinders (HSC) are changed.
[/B]*****************************************************************************************************************************

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________
[B]Note: Formatted just to see what the boot_info_script055 will see.
      Also this drive need to be ran through Testdisk and changed to 16  heads, 63 sectors/track, ????? cylinders. The 255 heads, 63  sectors/track, 121601 cylinders is due to a previos clone of an older  250GB SATA HDD and originally looked like what is now known as "sdb"
       Plan on testing install before Heads, Sectors, & Cylinders (HSC) are changed.
*****************************************************************************************************************************
[/B] 
Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1              16,065 1,953,520,064 1,953,504,000   f W95 Ext d (LBA)
/dev/sdd5              16,128 1,953,520,064 1,953,503,937   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________
[B]Note: 2GB USB Flash Stick only used by Windows OS's not used in any Ubuntu install test.
[/B]
Disk /dev/sde: 2021 MB, 2021654016 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948543 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63     3,948,542     3,948,480   6 FAT16

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6664413B64410F6D                       ntfs       HP_PAVILION                   
/dev/sdb2        01CBCEB6C382A580                       ntfs       Win7Old                       
/dev/sdb3        01CBD7121ECFD030                       ntfs       Win7                          
/dev/sdb4        0478C00D78BFFF82                       ntfs       Data                          
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        01CBD6EE55392500                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1: PTTYPE="dos" 
/dev/sdd5        01CBD6EE2B2F6D00                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        0000-017F                              vfat                                     
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb4        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
``````

First boot After Installing Ubuntu 10.10

Questions????
Why was GParted only able to see sda which is setting in an external  SATA dock connected via SATA cable to back of desktop to the MB IO SATA  port which was the only unallocated drive in system.

Although the Ubuntu install see all the drives Why did the Ubuntu  install also identify the 80GB drive sitting in an external SATA dock  connected via SATA cable to back of desktop to the MB IO SATA port as  "sda"

EVERYTHING ABOVE THIS LINE WAS ADDED FOR INFOMATION ALSO NOTES IN BOLD  TEXT REFER TO THAT SECTION ONLY ADD BY ME AND IS NOT PART OF THE  boot_info_script055 OUTPUT.
***************************************************************************************************************
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,046    30,273,535    30,271,490   5 Extended
/dev/sda5               2,048    30,273,535    30,271,488  83 Linux
/dev/sda2          30,273,536   137,695,231   107,421,696  83 Linux
/dev/sda3         137,695,232   156,301,311    18,606,080  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   209,718,431   209,718,369   7 HPFS/NTFS
/dev/sdb2         209,718,432   419,437,871   209,719,440   7 HPFS/NTFS
/dev/sdb3         419,740,272   629,459,711   209,719,440   7 HPFS/NTFS
/dev/sdb4         629,459,712 2,930,277,167 2,300,817,456   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1              16,065 1,953,520,064 1,953,504,000   f W95 Ext d (LBA)
/dev/sdd5              16,128 1,953,520,064 1,953,503,937   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 2021 MB, 2021654016 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948543 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63     3,948,542     3,948,480   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        ab9a6908-5b40-4aa4-97f5-2f392d64a2a2   ext4                                     
/dev/sda3        60724ef5-ab38-424b-9988-b4deac0067a0   swap                                     
/dev/sda5        53319a2b-2497-491c-b2fe-d43f465ba4ac   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6664413B64410F6D                       ntfs       HP_PAVILION                   
/dev/sdb2        01CBCEB6C382A580                       ntfs       Win7Old                       
/dev/sdb3        01CBD7121ECFD030                       ntfs       Win7                          
/dev/sdb4        0478C00D78BFFF82                       ntfs       Data                          
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        01CBD6EE55392500                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1: PTTYPE="dos" 
/dev/sdd5        01CBD6EE2B2F6D00                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        0000-017F                              vfat                                     
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /home                    ext4       (rw,commit=0)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660     (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sde1        /media/0000-017F         vfat        (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb4        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 53319a2b-2497-491c-b2fe-d43f465ba4ac
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 53319a2b-2497-491c-b2fe-d43f465ba4ac
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 53319a2b-2497-491c-b2fe-d43f465ba4ac
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=53319a2b-2497-491c-b2fe-d43f465ba4ac ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 53319a2b-2497-491c-b2fe-d43f465ba4ac
    echo    'Loading Linux 2.6.35-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=53319a2b-2497-491c-b2fe-d43f465ba4ac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 53319a2b-2497-491c-b2fe-d43f465ba4ac
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 53319a2b-2497-491c-b2fe-d43f465ba4ac
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6664413b64410f6d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 01cbceb6c382a580
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 01cbd7121ecfd030
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
UUID=53319a2b-2497-491c-b2fe-d43f465ba4ac /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=ab9a6908-5b40-4aa4-97f5-2f392d64a2a2 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=60724ef5-ab38-424b-9988-b4deac0067a0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  11.0GB: boot/grub/core.img
  13.0GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-27-generic-pae
  11.0GB: boot/vmlinuz-2.6.35-27-generic-pae
   1.0GB: initrd.img
  11.0GB: vmlinuz

================================ sdb1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /FASTDETECT /USEPMTIMER /NOEXECUTE=OPTIN
c:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console"  /CMDCONS
``````
                Boot Info Script 0.55    dated  February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,046    30,273,535    30,271,490   5 Extended
/dev/sda5               2,048    30,273,535    30,271,488  83 Linux
/dev/sda2          30,273,536   137,695,231   107,421,696  83 Linux
/dev/sda3         137,695,232   156,301,311    18,606,080  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   209,718,431   209,718,369   7 HPFS/NTFS
/dev/sdb2         209,718,432   419,437,871   209,719,440   7 HPFS/NTFS
/dev/sdb3         419,740,272   629,459,711   209,719,440   7 HPFS/NTFS
/dev/sdb4         629,459,712 2,930,277,167 2,300,817,456   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1              16,065 1,953,520,064 1,953,504,000   f W95 Ext d (LBA)
/dev/sdd5              16,128 1,953,520,064 1,953,503,937   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 2021 MB, 2021654016 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948543 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63     3,948,542     3,948,480   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        ab9a6908-5b40-4aa4-97f5-2f392d64a2a2   ext4                                     
/dev/sda3        60724ef5-ab38-424b-9988-b4deac0067a0   swap                                     
/dev/sda5        53319a2b-2497-491c-b2fe-d43f465ba4ac   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6664413B64410F6D                       ntfs       HP_PAVILION                   
/dev/sdb2        01CBCEB6C382A580                       ntfs       Win7Old                       
/dev/sdb3        01CBD7121ECFD030                       ntfs       Win7                          
/dev/sdb4        0478C00D78BFFF82                       ntfs       Data                          
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        01CBD6EE55392500                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1: PTTYPE="dos" 
/dev/sdd5        01CBD6EE2B2F6D00                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        0000-017F                              vfat                                     
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /home                    ext4       (rw,commit=0)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660     (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sde1        /media/0000-017F         vfat        (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb4        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 53319a2b-2497-491c-b2fe-d43f465ba4ac
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 53319a2b-2497-491c-b2fe-d43f465ba4ac
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 53319a2b-2497-491c-b2fe-d43f465ba4ac
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=53319a2b-2497-491c-b2fe-d43f465ba4ac ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 53319a2b-2497-491c-b2fe-d43f465ba4ac
    echo    'Loading Linux 2.6.35-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=53319a2b-2497-491c-b2fe-d43f465ba4ac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 53319a2b-2497-491c-b2fe-d43f465ba4ac
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 53319a2b-2497-491c-b2fe-d43f465ba4ac
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 6664413b64410f6d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 01cbceb6c382a580
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 01cbd7121ecfd030
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
UUID=53319a2b-2497-491c-b2fe-d43f465ba4ac /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=ab9a6908-5b40-4aa4-97f5-2f392d64a2a2 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=60724ef5-ab38-424b-9988-b4deac0067a0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  11.0GB: boot/grub/core.img
  13.0GB: boot/grub/grub.cfg
   1.1GB: boot/initrd.img-2.6.35-27-generic-pae
  11.0GB: boot/vmlinuz-2.6.35-27-generic-pae
   1.1GB: initrd.img
  11.0GB: vmlinuz

================================ sdb1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /FASTDETECT /USEPMTIMER /NOEXECUTE=OPTIN
c:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS
```

---

### Post by John4582 on 2011-03-01
> **Zyzzy said:**
> Maybe, changing **Access mode** from **Auto** to **Large** on IDE disk in BIOS is the key... ???

Zyzzy, did you try it? If so what were the results? I will have to check to see if I have the setting "Large", I think (not sure) that after setting SATA to Native IDE the IDE access mode is either Auto or None in my BIOS. If I have the "Large" setting I might try the test next.

---

### Post by John4582 on 2011-03-02
[IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG] [SIZE=5]Solved Solved Solved Solved[/SIZE] [IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG] 

First of all I want to **Thank** you **_Oldfred_ & _you Quackers_ **again for all your help and sticking with me.

Turned out to be a BIOS Setting on the Gigabyte GA-MA785GM-US2H (rev  3.3) Motherboard after all. How I missed it IDK, :confused:I must have check/tried every  setting/combination of settings in the BIOS a dozen times, maybe the following will explain how.

Once in the system BIOS:
**Standard BIOS Settings -> [drive you want to change] -> IDE Access -> &#8220;Large&#8221;**, did the trick. (see below)

Special Note:
 **MUST be set to "Large"** !!!**!_[COLOR=Red]PRIOR TO INSTALL[/COLOR]_**!!!! - Can be set back to Auto after install, at least on the above motherboard anyway. (don't know why you would want to). 

Also when set back to Auto I noticed more frequent beeping from my  system but not sure if related because I do hear a beep once in awhile  even though it's set to "Large"
[B]
Zyzzy[/B] thank you for pointing me to the **Standard BIOS Settings -> [drive you want to change] -> IDE Access -> &#8220;Large&#8221;**, that did the trick. (**MUST be set to "Large"** [COLOR=Red]**PRIOR TO INSTALL.**[/COLOR]

I check booting the other OS's and they boot with no problems.

Thanks again Guys :razz:

John

[B]Conclusion of additional testing:
Grub can't deal with the following [COLOR=Red][COLOR=Black]HDD Geometry[/COLOR] unless AHCI is implemented [COLOR=Black](didn't test Raid)[/COLOR][/COLOR]
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
[COLOR=Red]16 heads, 63 sectors/track[COLOR=Black], 2907021 cylinders[/COLOR]
Units = cylinders of 1008 * 512 = 516096 bytes
[/COLOR][/B]
If _**[COLOR=Red]AHCI [/COLOR][COLOR=Red]IS NOT[/COLOR]**_ implemented and **[COLOR=Red]_using IDE_ [/COLOR]** then HDD Geometry must be as as follow [COLOR=Red]**Prior To/During Install**[/COLOR]:
[B]Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
[COLOR=Red]255 heads, 63 sectors/track[/COLOR][/B], 182401 cylinders, total 2930277168 sectors
[COLOR=Red]**Units = sectors of 1 * 512**[/COLOR] = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

[B]NOTE: Grub appears to only see Primary partition(s) unless AHCI is implemented if your HDD Geometry is 16 heads 63 sectors/track. (didn't test Raid)

Additional Information on my HDDs that had 16 heads, 63 sectors/track:

Used Seagate/Mactor DiscWizard to Ready the drives for uses.

[/B]All my internal HDDs are New Seagate LP Series (Green drives) SATA drives. Check Seagate product guide at the following Link:
[http://www.seagate.com/staticfiles/support/disc/manuals/desktop/Barracuda%20LP/100564361e.pdf]("http://www.seagate.com/staticfiles/support/disc/manuals/desktop/Barracuda%20LP/100564361e.pdf")

To be exact the drive I had all the Grub problems on was the ST31500541AS (7200.11) (Rev. E) 32MB Cashe SATA 3Gb/s. Also both my 1TB drives are ST31000520AS and the specs are also in same .pdf file.

The default Geometry of these drives is 16 heads 63 sectors/track. I thinks that this is because of the 4k sectors which most HDDs are going to and I think my Windows OS's are using.????

The newest Seagate Green drives version 7200.12 are 2TB & 1.5TB 7200 RPM SATA 32MB or 64MB 6Gb/s and I believe that they use the 4k block and have the 16 heads 63 sectors/track.

Also I heard back from **Gigabyte** today and basically they refused to help because they **DO NOT SUPPORT LINUX** because it's **GNU GPL**.

**Data used for Conclusion**

**No Test **- Before Ubuntu ever installed BIOS set to **Native IDE & IDE Access** set to **Auto **
Boot Ubuntu Live CD Click Install Ubuntu Icon on Desktop and install Ubuntu with Custom/Advance option.

**Drive  before Ubuntu ever installed** with **BIOS** set to **Native IDE & IDE  Access** set to **Auto** - Windows XP Pro installed 1st partition sda1 -  Windows 7 Pro installed 2nd partition sda2 - Data on 4th partition sda3 -  3rd partition Extended sda4 with 3 sub-partitions (/ sda5 - /home sda6 -  swap sda7) for Ubuntu 10.10 (not installed yet). 

**HDD before Ubuntu installed**
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
[COLOR=Red]**16 heads, 63 sectors/track**[/COLOR], 2907021 cylinders
[COLOR=Red]**Units = cylinders of 1008 * 512**[/COLOR] = 516096 bytes

**HDD after Ubuntu installed**
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
[COLOR=Red]**16 heads, 63 sectors/track**[/COLOR], 2907021 cylinders
[COLOR=Red]**Units = cylinders of 1008 * 512**[/COLOR] = 516096 bytes

**Grub2  is installed to sda** but only boots to[COLOR=Red]** Grub rescue -> "ls"**[/COLOR] only  drives Grub sees (hd0) (msdos3) (msdos2) (msdos1) (fd0) **Grub doesn't see  (msdos5)** where Grub is installed **even if you change the BIOS set to  Native IDE & IDE Access set to Large**. 


**Test 1** - Delete  Ubuntu partition and change **BIOS** set to **Native IDE & IDE Access** set  to **Large** Boot Ubuntu Live CD Click Install Ubuntu Icon on Desktop and  install Ubuntu with Custom/Advance option.

**Drive before Ubuntu  ever installed** with **BIOS** set to **Native IDE & IDE Access** set to **Large**  - Windows XP Pro installed 1st partition sda1 - Windows 7 Pro installed  2nd partition sda2 - Data on 4th partition sda3 - 100GB Unallocated  space.

**HDD before Ubuntu installed** (Note that the HDD heads changed form 16 to 240 because the IDE Access in the BIOS was changed to Large)
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
[COLOR=Red]**240 heads, 63 sectors/track**[/COLOR], 193801 cylinders, total 2930277168 sectors
[COLOR=Red]**Units = sectors of 1 * 512**[/COLOR] = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

[COLOR=Red]**HDD after Ubuntu installed**[/COLOR]
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
[COLOR=Red]**255 heads, 63 sectors/track**[/COLOR], 182401 cylinders, total 2930277168 sectors
[COLOR=Red]**Units = sectors of 1 * 512 **[/COLOR]= 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

[B]Grub2 is installed to sda boots all 3 OS's with no problems. (windows may perform a CHKDISK when you first boot into windows)
[/B]

**Test  2** - **BIOS** set to **Native IDE & IDE Access **set to **Auto** Boot into  Ubuntu on sda5 **Purge Grub **Then **reinstall Grub** with **BIOS** set to **Native  IDE & IDE Access** set to **Auto**

**Drive Ubuntu is installed on **change ** BIOS** set to Native **IDE & IDE Access** set to **Auto** - Windows XP Pro  installed 1st partition sda1 - Windows 7 Pro installed 2nd partition  sda2 - Data on 4th partition sda3 - 3rd partition Extended sda4 with 3  sub-partitions (/ sda5 - /home sda6 - swap sda7) where Ubuntu 10.10 is  installed.

**HDD before Grub purge** (Note that the HDD heads didn't change even though the IDE Access changed to Auto)
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
[COLOR=Red]**255 heads, 63 sectors/track**[/COLOR], 182401 cylinders, total 2930277168 sectors
**[COLOR=Red]Units = sectors of 1 * 512[/COLOR]** = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

**HDD after Grub purge and reinstalled**
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
[COLOR=Red]**255 heads, 63 sectors/track**[/COLOR], 182401 cylinders, total 2930277168 sectors
[COLOR=Red]**Units = sectors of 1 * 512 **[/COLOR]= 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

**Grub2 is installed to sda boots all 3 OS's with no problems.**

---

### Post by Zyzzy on 2011-03-02
Nice to see it works! :-) Thanks for test, I didn't try it yet, it was just an idea. I just browsed BIOS settings, but had no time to install Ubuntu/grub again.

---


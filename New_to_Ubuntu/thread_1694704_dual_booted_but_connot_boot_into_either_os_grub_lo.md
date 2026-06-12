---
title: "dual booted but connot boot into either os grub lost"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Ajay Ramaseshan on 2011-02-24
hello
I have a hp presario laptop with dual booted windows 7 32 bit and ubuntu 10.10 . I had installed some software on windows and restarted my machine to go to ubuntu but after restarting all i get is a black screen no boot loader ! So i put a live cd of ubuntu 9.04 to check if there was a hard disk failure but i am to see and mount the partitons from the live cd . I then read the restore grub 2 article but it says you should have a live cd of 9.10 or higher i want to confirm if 9.04 is ok to restore grub for 10.10 installation or not and if so what i should do next

Ajay

---

### Post by rosencrantz on 2011-02-24
Hi Ajay,
I don't think your grub is lost, Windows probably just wiped your MBR. See [this thread]("http://ubuntuforums.org/showthread.php?t=24113") for restoration. However, I don't think you'll get very far with the 9.04 CD, as Ubuntu has switched from grub1 to grub2 inbetween. So, either get a recent live Ubuntu (CD/USB) or try your luck with a [SuperGrub2 CD]("http://www.supergrubdisk.org/wiki/Howto_Fix_Grub") (smaller download size). Worked wonders for me on grub1.

Best of luck
rosencrantz

---

### Post by guilleme on 2011-02-24
If you are using grub 2, I'd suggest to get a newer ubu. version, because I think that 9.04 doesn't support it. 
From the live cd, I'd suggest to check File Systems, and use the aforementioned thread's information about MBR for repairing it if it's broken, and remember that grub needs some free space too :). ( If you boot from a live cd, and are going to mess up with partitions and MBR, Then this is a great time for updating your backups, or at least to make some for the important files;))
If everything fails, you can always reinstall Ubuntu, leaving some more space for grub:).

---

### Post by Ajay Ramaseshan on 2011-02-25
> **rosencrantz said:**
> Hi Ajay,
I don't think your grub is lost, Windows probably just wiped your MBR. See [this thread]("http://ubuntuforums.org/showthread.php?t=24113") for restoration. However, I don't think you'll get very far with the 9.04 CD, as Ubuntu has switched from grub1 to grub2 inbetween. So, either get a recent live Ubuntu (CD/USB) or try your luck with a [SuperGrub2 CD]("http://www.supergrubdisk.org/wiki/Howto_Fix_Grub") (smaller download size). Worked wonders for me on grub1.

Best of luck
rosencrantz

Hey

Got hold of an Ubuntu 10.10 live USB. and tried the link to restore the Grub . but when i typed Grub and went to the > prompt I typed root(hd0, and then pressed tab ) it shows this error :

```
grub> root (hd0,
Error 21: Selected disk does not exist
```

I thought maybe we have to mount all the partitions and then try so I did that too. but it still shows the same error.. 

I am also attaching the output of the "sudo fidk -l " command for your reference . can you please tell me what is the problem ??

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f22e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6528    52326400    7  HPFS/NTFS
/dev/sda3            6589       60802   435467265    5  Extended
/dev/sda4            6528        6589      488448   83  Linux
/dev/sda5           15045       60802   367538176    7  HPFS/NTFS
/dev/sda6            6589        6953     2928640   82  Linux swap / Solaris
/dev/sda7            6953       13178    49998848   83  Linux
/dev/sda8           13178       15044    14991360   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1006 MB, 1006632960 bytes
31 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 1922 * 512 = 984064 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cf44b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1022      982111    c  W95 FAT32 (LBA)

Disk /dev/sdc: 8103 MB, 8103395328 bytes
196 heads, 32 sectors/track, 2523 cylinders
Units = cylinders of 6272 * 512 = 3211264 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2524     7913456    c  W95 FAT32 (LBA)

```

Regards,
Ajay

---

### Post by oldfred on 2011-02-25
Are you booting with grub legacy or grub2. An error # is only from grub legacy, but if you had grub2 and now added grub that can confuse things.

To see where everything is at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Ajay Ramaseshan on 2011-02-26
> **oldfred said:**
> Are you booting with grub legacy or grub2. An error # is only from grub legacy, but if you had grub2 and now added grub that can confuse things.

To see where everything is at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

hey
I downloaded the bootinfo script and these are the contents of the file results.txt

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
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

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   104,859,647   104,652,800   7 HPFS/NTFS
/dev/sda3         105,838,590   976,773,119   870,934,530   5 Extended
/dev/sda5         241,696,768   976,773,119   735,076,352   7 HPFS/NTFS
/dev/sda6         105,838,592   111,695,871     5,857,280  82 Linux swap / Solaris
/dev/sda7         111,697,920   211,695,615    99,997,696  83 Linux
/dev/sda8         211,697,664   241,680,383    29,982,720  83 Linux
/dev/sda4         104,859,648   105,836,543       976,896  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1006 MB, 1006632960 bytes
31 heads, 62 sectors/track, 1022 cylinders, total 1966080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     1,964,283     1,964,222   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8103 MB, 8103395328 bytes
196 heads, 32 sectors/track, 2523 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32    15,826,943    15,826,912   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        341AF5931AF5527A                       ntfs       System Reserved               
/dev/sda2        8E8EFDBD8EFD9DC1                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        74d72390-c39a-4e51-a10c-59d3d37036ae   ext4                                     
/dev/sda5        1C4D314C0AD198E3                       ntfs       Ajay                          
/dev/sda6        8435cb99-4d46-4c57-8406-493e25bf8df9   swap                                     
/dev/sda7        e4e6246b-2e30-405f-bc4f-47e1923e4c92   ext4                                     
/dev/sda8        cdd0a365-3fc5-44fb-af8c-6b82a3738622   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A210-39A0                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        7136-62C9                              vfat       Transcend                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/Transcend         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=e4e6246b-2e30-405f-bc4f-47e1923e4c92 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda4 during installation
UUID=74d72390-c39a-4e51-a10c-59d3d37036ae /boot           ext4    defaults        0       2
# /home was on /dev/sda8 during installation
# Commented out by Dropbox
# UUID=cdd0a365-3fc5-44fb-af8c-6b82a3738622 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=8435cb99-4d46-4c57-8406-493e25bf8df9 none            swap    sw              0       0
UUID=cdd0a365-3fc5-44fb-af8c-6b82a3738622 /home ext4 defaults,user_xattr 0 2

============================= sda4/grub/grub.cfg: =============================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set e4e6246b-2e30-405f-bc4f-47e1923e4c92
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 74d72390-c39a-4e51-a10c-59d3d37036ae
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 74d72390-c39a-4e51-a10c-59d3d37036ae
    linux    /vmlinuz-2.6.35-25-generic-pae root=UUID=e4e6246b-2e30-405f-bc4f-47e1923e4c92 ro   quiet splash
    initrd    /initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 74d72390-c39a-4e51-a10c-59d3d37036ae
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /vmlinuz-2.6.35-25-generic-pae root=UUID=e4e6246b-2e30-405f-bc4f-47e1923e4c92 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 74d72390-c39a-4e51-a10c-59d3d37036ae
    linux    /vmlinuz-2.6.35-23-generic-pae root=UUID=e4e6246b-2e30-405f-bc4f-47e1923e4c92 ro   quiet splash
    initrd    /initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 74d72390-c39a-4e51-a10c-59d3d37036ae
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /vmlinuz-2.6.35-23-generic-pae root=UUID=e4e6246b-2e30-405f-bc4f-47e1923e4c92 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 74d72390-c39a-4e51-a10c-59d3d37036ae
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 74d72390-c39a-4e51-a10c-59d3d37036ae
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 341af5931af5527a
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

=================== sda4: Location of files loaded by Grub: ===================


  53.8GB: grub/core.img
  53.8GB: grub/grub.cfg
  53.7GB: initrd.img-2.6.35-23-generic-pae
  53.7GB: initrd.img-2.6.35-25-generic-pae
  53.7GB: vmlinuz-2.6.35-23-generic-pae
  53.7GB: vmlinuz-2.6.35-25-generic-pae
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  db 9a e3 8a 55 41 a2 a7  0e 8e 72 1c a2 a8 22 2a  |....UA....r..."*|
00000010  20 e3 82 02 31 f4 39 80  fd b8 3a 04 09 24 db b3  | ...1.9...:..$..|
00000020  18 20 71 02 55 42 89 14  69 c6 e6 79 fe 65 e4 ff  |. q.UB..i..y.e..|
00000030  ff 8a 4a 5f 7b fd 7f ff  fb 92 04 f6 80 02 f8 67  |..J_{..........g|
00000040  d2 d3 01 42 f2 5e ac fa  7a 3c 25 5e 4a e9 9f 4c  |...B.^..z<%^J..L|
00000050  e7 84 ab c9 6c 33 e9 e8  f0 95 79 ea 4b 4d 5d fd  |....l3....y.KM].|
00000060  34 df fe ae da db ff f3  a1 0e 8c 72 aa 28 88 c1  |4..........r.(..|
00000070  e1 64 51 55 87 46 b1 c4  ca ff a7 f4 db 11 43 97  |.dQU.F........C.|
00000080  39 9d c8 a5 54 1a 1d 38  74 73 90 68 74 15 0a 1d  |9...T..8ts.ht...|
00000090  10 71 50 80 8b 8b 58 7b  89 e6 06 82 81 49 34 ac  |.qP...X{.....I4.|
000000a0  c2 28 0a 80 c4 a3 14 94  10 50 c8 a2 57 3f f8 e6  |.(.......P..W?..|
000000b0  ff ff 9c 43 fa 83 7f da  bf ef 38 d4 54 71 ca 3f  |...C......8.Tq.?|
000000c0  af ff d5 7f ff fa 5d 8e  34 7a 4c 75 18 60 b8 f9  |......].4zLu.`..|
000000d0  67 28 40 7e 64 b9 23 09  33 f3 d2 9b ed 5b d1 18  |g(@~d.#.3....[..|
000000e0  f3 ca bb 8f 1a 7b a1 ce  31 11 58 f3 4f 14 8d 89  |.....{..1.X.O...|
000000f0  93 20 50 6e ce 2d 9c 3c  40 e1 d1 e0 69 87 93 18  |. Pn.-.<@...i...|
00000100  04 92 92 8e 9d 81 10 09  d1 ac 90 0e 45 88 2a e7  |............E.*.|
00000110  2f fd ef ff cf 32 bf eb  7f db ff 5b 2f 93 7e df  |/....2.....[/.~.|
00000120  ff 95 7f ff fe 7b 95 22  e2 a2 05 0c 39 48 a2 03  |.....{."....9H..|
00000130  95 08 38 5c 48 8f 7b 55  3d f6 d6 b2 54 ea 3d d2  |..8\H.{U=...T.=.|
00000140  ee 43 1c 72 07 59 d8 e3  44 85 c7 8a 10 0e c3 c1  |.C.r.Y..D.......|
00000150  68 8c 83 4c e8 71 e0 00  cb 8a 82 b6 e0 7a f0 6b  |h..L.q.......z.k|
00000160  03 84 2f b1 38 3a c2 d7  c9 32 64 8a 1b 2f 5d 99  |../.8:...2d../].|
00000170  7f fe b5 09 bd 33 ef b7  fe ef ff fe be 7d 7e ff  |.....3.......}~.|
00000180  ff ff ff ff fb ff ff 8f  8f ff f8 5d 5a 98 a4 12  |...........]Z...|
00000190  2b 17 64 a0 8c e2 8b 25  b0 e2 2a 6f ff f5 db ea  |+.d....%..*o....|
000001a0  39 d6 d7 29 b6 a6 1a fc  22 a1 22 4b 16 1a d4 38  |9..)...."."K...8|
000001b0  46 0f c6 1a 28 22 5b 96  62 a8 a9 32 18 0b 00 fe  |F...("[.b..2....|
000001c0  ff ff 07 fe ff ff 02 08  19 08 00 60 d0 2b 00 fe  |...........`.+..|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 60 59 00 00 00  |...........`Y...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

By the way, yesterday I just typed "grub" into the terminal of the live USB. As it wasnt there, i installed it using "sudo apt-get install grub" and started working with that. So it looks that I have used grub instead of grub2..

Ajay

---

### Post by oldfred on 2011-02-26
You have grub2, if you install grub it gets confused with both and you end up having to uninstall both and reinstall grub2. Since grub2 is also grub we sometimes mix them up in posts since those running old versions of Ubuntu and a few holdouts that liked old grub legacy.  

You also have a /boot partition. Since that is not common with Desktops, many instructions do not highlight that you have to also mount that when you reinstall grub2. 

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda7 and want grub2 in drive sda's MBR:
#Find linux partition, change sda7 if not correct:
sudo fdisk -l
#confirm that linux is sda7
sudo mount /dev/sda7 /mnt
sudo mount /dev/sda4 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

Does not include mount of /boot
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Only has footnote on mounting /boot
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Ajay Ramaseshan on 2011-02-26
> **oldfred said:**
> You have grub2, if you install grub it gets confused with both and you end up having to uninstall both and reinstall grub2. Since grub2 is also grub we sometimes mix them up in posts since those running old versions of Ubuntu and a few holdouts that liked old grub legacy.  

You also have a /boot partition. Since that is not common with Desktops, many instructions do not highlight that you have to also mount that when you reinstall grub2. 

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda7 and want grub2 in drive sda's MBR:
#Find linux partition, change sda7 if not correct:
sudo fdisk -l
#confirm that linux is sda7
sudo mount /dev/sda7 /mnt
sudo mount /dev/sda4 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

Does not include mount of /boot
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Only has footnote on mounting /boot
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

hey

Thank you very much . I have resolved the problem and now I have restored my Grub2 . 

I will this mark this problem now as "solved"...!
Thanks once again..!!

Ajay

---


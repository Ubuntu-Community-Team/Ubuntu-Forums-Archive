---
title: "Re install XPPRO on PC with U 9.10 already installed?..."
date: 2010-02-16
forum: New to Ubuntu
---

### Post by THXTom on 2010-02-16
Kids PC is hosed....
 
XP sys restore didnt work, when I get some time will try repair w/slipstream disk....
 
If that does not work am going to re install on same drive/partition as originally installed on.
 
Just wondering if there is any "gotcha's" or things to do differently when grub/ubuntu is installed.
 
Searching the board now for tips on this pending operation.
 
Thanks, T

---

### Post by presence1960 on 2010-02-16
If linux and windows will be on the same hard disk, when you install windows after linux it will overwrite GRUB on MBR and windows will write it's bootloader to MBR. Once windows is installed boot into it a couple times to make sure it is OK. Then you will have to restore GRUB to MBR of hard disk. If you don't know how post back.

If windows and linux will be on separate hard disks you must put the disk that windows will be installed onto as first disk to boot in the hard disk boot order in BIOS. This is absolutely necessary as windows writes it's bootloader to MBR of the first disk to boot irregardless of which disk you are installing windows onto. Example you are installing windows to sdb. If you don't set sdb as first hard disk to boot in BIOS the windows bootloader will be written to sda. ***_Again just make sure you set the hard disk you are putting windows onto as the first hard disk to boot in BIOS._***

---

### Post by pricetech on 2010-02-16
XP in a VM ???

---

### Post by underquark on 2010-02-16
I assume you have some games or something you want to run in XP.  Otherwise, I find ubuntu better than XP as it has Childsplay, gCompris etc. and still runs all their websites.  You could always do a complete clean install of XP using only half the disk and then a clean install of ubuntu in the remainder for the best of both worlds.  Sure, you have to reconfigure things and reinstall software by IMHO it doesn't hurt to do a Spring clean now and again.

---

### Post by THXTom on 2010-02-17
> **presence1960 said:**
> If linux and windows will be on the same hard disk, when you install windows after linux it will overwrite GRUB on MBR and windows will write it's bootloader to MBR. Once windows is installed boot into it a couple times to make sure it is OK. Then you will have to restore GRUB to MBR of hard disk. If you don't know how post back.
 
 
If windows and linux will be on separate hard disks you must put the disk that windows will be installed onto as first disk to boot in the hard disk boot order in BIOS. This is absolutely necessary as windows writes it's bootloader to MBR of the first disk to boot irregardless of which disk you are installing windows onto. Example you are installing windows to sdb. If you don't set sdb as first hard disk to boot in BIOS the windows bootloader will be written to sda. ***_Again just make sure you set the hard disk you are putting windows onto as the first hard disk to boot in BIOS._***
 
**So if i'm reading you right, I should have no problem doing a repair, and or a complete wipe of the XP patition on disk 1, and do a clean install...**
 
***XP is on disk 1 NTFS, Ubuntu is on Disk 2, Ext3....when I installed, XP was 1st, then Ubuntu was installed on disk 2...I never changed boot disk order.***
 
 
 
Many thanks, T

---

### Post by superprash2003 on 2010-02-17
check this link [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by presence1960 on 2010-02-17
> **THXTom said:**
> **So if i'm reading you right, I should have no problem doing a repair, and or a complete wipe of the XP patition on disk 1, and do a clean install...**
 
***XP is on disk 1 NTFS, Ubuntu is on Disk 2, Ext3....when I installed, XP was 1st, then Ubuntu was installed on disk 2...I never changed boot disk order.***
 
 
 
Many thanks, T

If XP is on the first disk to boot in BIOS you do not have to change the order of disks in BIOS. Whether you do a repair or a clean install to disk 1 (you probably mean disk 0) you won't have to change the order of the disks in BIOS. If GRUB is on the MBR of the disk which has XP you will have to reinstall GRUB though after the XP repair or clean install. Any problems post back!

---

### Post by THXTom on 2010-02-19
Thanks, for the help '1960 and others...
 
My boy now tells me XP _AND_ Ubuntu have problems "locking" up after the PC's been on for an hour or so. I have expierinced this also in XP
 
I want to check out the Ubuntu claim of locking up thou.
 
Well had some free time and ran Seagates tools on the 3 drives in this box, all checked OK.
 
Ran memtest86/v4.0 and checked OK....
 
It's an old P4 dell 8100 and I'm begining to think it's possibly a hardware issue...????
 
Whats a good diag app for motherboard, etc to check things out? (Linux maybe?)
 
Anyway, might try the re install of XP for the heck of it.
 
I'll be back for those grub re install steps if I go the re install route.
 
Thanks, T

---

### Post by THXTom on 2010-02-20
Ubuntu has been up running for 24 hrs, so I've ruled out PC problem.
 
Going to repair Windows, so if what I'm reading i'll have to re install grub2.
 
Is the follwing the way to go?
 
```

[COLOR=black][FONT=Verdana][SIZE=3][SIZE=2]To restore the grub, you must boot off the ubuntu live cd. Any ubuntu live cd will do.[/SIZE][/SIZE][/FONT][/COLOR]
 
[FONT=Verdana][SIZE=2][COLOR=black]Once there, open a terminal (Applications>Accessories>Terminal) and type this:[/COLOR][/SIZE][/FONT]
[COLOR=black][FONT=Verdana][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo grub[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=2]Next, you need to find which hard drive ubuntu and the grub is installed to. You do this by running this command:[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Courier New]find /boot/grub/stage1[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=2]Take note of what it returns (something like (hd0,1).)[/SIZE][/FONT][/COLOR]
 
[FONT=Verdana][SIZE=2][COLOR=black]Now you need to tell Grub where it is installed. Using the output of the last command, change this one and run it:[/COLOR][/SIZE][/FONT]
[COLOR=black][FONT=Verdana][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Courier New]root (hd<a>,<b>)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=2]Replacing <a> and <b> with what you got back before. For example, if "find /boot/grub/stage1" gave me "(hd0,1)", you would run "root (hd0,1)"[/SIZE][/FONT][/COLOR]
 
[FONT=Verdana][SIZE=2][COLOR=black]Ok, so thats the configuration over and done with. Now we just need to run one command to install the Grub to your hard drive:[/COLOR][/SIZE][/FONT]
[COLOR=black][FONT=Verdana][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
[SIZE=2][FONT=Verdana][COLOR=black][COLOR=black][FONT=Courier New]setup (hd0)[/FONT][/COLOR][/COLOR][/FONT][/SIZE]
 
[FONT=Verdana][COLOR=black][SIZE=2][COLOR=black][FONT=Verdana]Now to quit and check if it has worked:[/FONT][/COLOR][/SIZE]
[COLOR=black][FONT=Verdana][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Courier New][SIZE=2]quit[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Courier New][SIZE=2]sudo reboot[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=2]Make sure you have taken the live cd out of your disc tray. All going well, you should start back up and see the grub once again.[/SIZE][/FONT][/COLOR]
 
 
[/COLOR][/FONT]

```
 
 
Going to run the [FONT=Arial]**boot_info_script**[/FONT][FONT=Arial]  to see whats up first.[/FONT]
Thanks, T

---

### Post by presence1960 on 2010-02-20
That will only work if you have legacy GRUB 0.97 installed. If you have GRUB 2 which is a karmic default on a clean installation you need to do [this]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

To see which GRUB you have installed run in terminal ```
grub-install -v
```

---

### Post by naiku on 2010-02-20
> **presence1960 said:**
> If you have GRUB 2 which is a karmic default on a clean installation you need to do [this]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

To see which GRUB you have installed run in terminal ```
grub-install -v
```

This is the method I used a few days ago when facing the same situation. I had installed Ubuntu and removed XP, after getting annoyed trying to get 1 or 2 things working in Ubuntu, decided to reinstall XP. Got XP working and realized I could no longer get into Ubuntu, followed the steps provided at the link and now all is fine.

---

### Post by THXTom on 2010-02-20
> **presence1960 said:**
> That will only work if you have legacy GRUB 0.97 installed. If you have GRUB 2 which is a karmic default on a clean installation you need to do [this]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

To see which GRUB you have installed run in terminal ```
grub-install -v
```

OK:
GNU GRUB 1.97~BETA4

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=436fb0c5-ea72-45ea-a550-083f83e65024)/boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 67. But according to the info from fdisk, 
                       sdc5 starts at sector 96598912.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd36073fb

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    85,995,944    85,995,882   7 HPFS/NTFS
/dev/sda2          85,995,945   240,107,489   154,111,545   5 Extended
/dev/sda5          85,996,008   240,107,489   154,111,482   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders, total 60030432 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b605b60

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    56,645,189    56,645,127  83 Linux
/dev/sdb2          56,645,190    60,018,839     3,373,650   5 Extended
/dev/sdb5          56,645,253    60,018,839     3,373,587  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe23532f8

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    96,598,844    96,598,782   7 HPFS/NTFS
/dev/sdc2          96,598,845   442,253,384   345,654,540   5 Extended
/dev/sdc5          96,598,912   280,768,004   184,169,093   7 HPFS/NTFS
/dev/sdc6         280,768,068   442,253,384   161,485,317   7 HPFS/NTFS
/dev/sdc3         442,253,385   488,392,064    46,138,680   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        87572506FA9D1BA2                       ntfs       XP PRO 3                      
/dev/sda5        F446BEB481634ED2                       ntfs       FILES                         
/dev/sdb1        436fb0c5-ea72-45ea-a550-083f83e65024   ext3                                     
/dev/sdb5        8f079417-69a1-4eb1-8863-f4855bdd6c28   swap                                     
/dev/sdc1        35761F05518E5C5D                       ntfs       DATA                          
/dev/sdc3        F230643830640647                       ntfs       MT                            
/dev/sdc5        B4ECD3B2ECD36CDC                       ntfs       WD250G                        
/dev/sdc6        022B4AE57089BAE5                       ntfs       XP AND LINUX FILES            

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,errors=remount-ro)
/dev/sr1         /media/CNC3              udf        (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,umask=0077)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 436fb0c5-ea72-45ea-a550-083f83e65024
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 436fb0c5-ea72-45ea-a550-083f83e65024
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=436fb0c5-ea72-45ea-a550-083f83e65024 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 436fb0c5-ea72-45ea-a550-083f83e65024
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=436fb0c5-ea72-45ea-a550-083f83e65024 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 436fb0c5-ea72-45ea-a550-083f83e65024
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=436fb0c5-ea72-45ea-a550-083f83e65024 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 436fb0c5-ea72-45ea-a550-083f83e65024
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=436fb0c5-ea72-45ea-a550-083f83e65024 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 87572506fa9d1ba2
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=436fb0c5-ea72-45ea-a550-083f83e65024 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=8f079417-69a1-4eb1-8863-f4855bdd6c28 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   5.5GB: boot/grub/core.img
   5.5GB: boot/grub/grub.cfg
   5.6GB: boot/initrd.img-2.6.31-14-generic
   5.6GB: boot/initrd.img-2.6.31-19-generic
   5.6GB: boot/vmlinuz-2.6.31-14-generic
   5.6GB: boot/vmlinuz-2.6.31-19-generic
   5.6GB: initrd.img
   5.6GB: initrd.img.old
   5.6GB: vmlinuz
   5.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 f2 0e 00  60 5b 60 5b a3 7b 00 01  |........`[`[.{..|
000001c0  01 00 83 fe ff ff 3f 00  00 00 07 56 60 03 00 fe  |......?....V`...|
000001d0  ff ff 05 fe ff ff 46 56  60 03 52 7a 33 00 00 00  |......FV`.Rz3...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Now, on the Grub2 page, use the 1 of 2 options in section 11 to reinstall grub?

Thanks, T

---

### Post by presence1960 on 2010-02-20
This is what I would do. I would put GRUB on MBR of sdb and make sdb as first hard disk to boot in the hard disk boot order in BIOS. Then from Ubuntu I would repair the MBR of sda so that it has a windows MBR.

First put GRUB 2 on MBR of sdb. Boot the Live CD and choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
sudo mount /dev/sdb1 /mnt
``` This will mount your ubuntu / partition. next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```This will put GRUB on MBR of sdb. reboot without the Live CD and boot into ubuntu. Run in terminal ```
sudo dpkg-reconfigure grub-pc
```In the last window select sdb. This will insure all GRUB2 (grub-pc) updates go to sdb instead of sda. When finished run in terminal ```
sudo update-grub
```

Now from ubuntu you can fix the MBR of sda so it is a windows MBR. Run in terminal ```
sudo apt-get install lilo
```Ignore warnings if given. Then run in terminal ```
sudo lilo -M /dev/sda mbr
``` You should now be good to go.

Here is a link for your reference on reinstalling GRUB2 from Live CD: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

and one to a lot about GRUB2 and how to configure it: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by THXTom on 2010-02-21
> **presence1960 said:**
> This is what I would do. I would put GRUB on MBR of sdb and make sdb as first hard disk to boot in the hard disk boot order in BIOS. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
 
 
OK, will do in a few days.....thank you so much.
 
Being new to Ubuntu my learning curve is steep and this helps alot.
 
Brings me back to the Tandy 1000 days and DOS...:D

---

### Post by presence1960 on 2010-02-21
> **THXTom said:**
> OK, will do in a few days.....thank you so much.
 
Being new to Ubuntu my learning curve is steep and this helps alot.
 
Brings me back to the Tandy 1000 days and DOS...:D

If you need any further assistance post back. We all had to start at the beginning, but with help from this community learning is attainable more quickly than if we were left to our own devices.

---


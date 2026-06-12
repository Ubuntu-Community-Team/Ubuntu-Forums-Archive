---
title: "HELP GRUB not working cant access anything!"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by Angelbrand on 2010-12-19
i cannot get onto my computer whatso ever, on vista or ubuntu. i have just switched ubuntu to its own partition from wubi but when i rebooted it brought up a txt screen wich says:

Intel UNDI, PXE-2. 1 1997-2000   Intel Corporation


For Realtek RTL8111B/8111C Gigabit Ethernet Controller  vT. 17
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.


Error: no such device: 4f685464-88e3-407d-8c73k6c4d652fff5f.
Grub rescuse>

---

### Post by Eiji Takanaka on 2010-12-19
Loose hard-drive/power supply cable? 

Laptop/desktop?

The more relevant info divulged the better ;)

---

### Post by alzie on 2010-12-19
I just went through a similar situation.  Instructions to get things going again can be found here:
 [http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi+megathread](http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi+megathread)

---

### Post by Angelbrand on 2010-12-19
have to find my ubuntu install cd... Damn but thanks so much at least i its something i can do my self and not pay some overpriced tech to do!! :)

---

### Post by oldfred on 2010-12-19
If you have grub in the MBR and have the full install, you are not using wubi, anymore.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
Can you manual boot?
Manual boot:
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command or whatever number it is. The hd0 should be your hard drive, hd0,1 or 0,2 is probably windows, so we want the partition with Ubuntu.
configfile (hd0,1)/boot/grub/grub.cfg


If you are in the middle of converting, run this from liveCD.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by bcbc on 2010-12-19
Reinstall the Windows bootloader as described in the Wubi Megathread *alzie* referred to (you can use lilo too from the live CD).
Then boot the Wubi install, and - if you still want to - rerun the migration, but this time use the script ;)

---

### Post by Angelbrand on 2010-12-20
what do mean by use script...? i used your code the first time to migrate.

i have the ubuntu install cd in now so i can acess ubuntu through that but im not sure what to do from here... the partitions are allocated properly but i need to set up grub properly so i can access both OS's

---

### Post by Angelbrand on 2010-12-20
[SIZE=3]**[Solution #2:**[/SIZE]

If you do not have a Windows CD, or are unable to get hold of one, you  can use an Ubuntu CD to install a Windows-like bootloader.

From a terminal on the LiveCD (Applications > Accessories > Terminal), run the following commands:

     Code:
     sudo apt-get install lilo sudo lilo -M /dev/sd**[COLOR=Red]a[/COLOR]** mbr 
This assumes that sda is the Windows drive. If not, change this to reflect the actual drive e.g. sdb, sdc, etc. 

Ignore any warnings and continue with the installation to the MBR. The  main point is to get lilo installed and allow the user to boot Windows,  and hopefully Ubuntu, again.]


i entered that code and it asked do i want to continue Y/n so i say y but it comes up abort. what else can i do?

---

### Post by Angelbrand on 2010-12-20
its decided to install now...

---

### Post by Angelbrand on 2010-12-20
so have installed lilo but um what do i do now...?

---

### Post by QLee on 2010-12-20
Angelbrand,
Now would be a good time to slow down and stop. Take a deep breath and slowly let it out. When you feel calm, reread oldfred's post, #5. Follow the advice to run and post the info obtained from the boot info script while you are booted with the Live CD. That will let all of us (even the overpriced techs who are users here) see what state your system is currently in and then you will get useful and clear suggestions on how to proceed. Just follow one piece of advice through all the way, many people looking at your posts will ensure that you get good advice.

---

### Post by Rubi1200 on 2010-12-20
Totally agree with QLee on this one.

Stay calm. 

Run the boot info script we need and then we can help you further.

By the way, if lilo was installed then the next step would normally be to reboot and hopefully find yourself in Windows again (after which we would have helped you sort out the other issues).

---

### Post by bcbc on 2010-12-20
> **Angelbrand said:**
> what do mean by use script...? i used your code the first time to migrate.

i have the ubuntu install cd in now so i can acess ubuntu through that but im not sure what to do from here... the partitions are allocated properly but i need to set up grub properly so i can access both OS's

If you look again at the migration "Howto" it gives manual instructions, but that is immediately followed by an description of the automated migration and it has an attached script. There's also a reference to it right at the start of the manual instructions.

I agree with QLee that you need to slow down. The truth of the matter is that if you rushed through the migration, there are many commands there that could damage your system if run incorrectly. That's why I recommended using the script.

So, run the bootinfoscript, and hopefully, it's just a simple bootloader replacement...

PS to the others helping here - the OP was had posted on my Wubi migration thread before (to give you a little background, in case that wasn't obvious).

---

### Post by Angelbrand on 2010-12-20
ran boot info 

results:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
6 heads, 8 sectors/track, 6512121 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    12,290,047    12,288,000  27 Hidden HPFS/NTFS
/dev/sda2    *     12,290,048    84,054,015    71,763,968   7 HPFS/NTFS
/dev/sda3          84,054,016   219,508,735   135,454,720   7 HPFS/NTFS
/dev/sda4         219,508,736   312,580,095    93,071,360   5 Extended
/dev/sda5         219,510,784   265,021,439    45,510,656  83 Linux
/dev/sda6         265,023,488   312,580,095    47,556,608  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       4f685464-88e3-407d-8c73-6c4d652fff5f   ext4                                     
/dev/sda1        20B82189B8215F12                       ntfs       WinRE                         
/dev/sda2        56A42F8EA42F6FA3                       ntfs       OS_Install                    
/dev/sda3        F2CC2E0BCC2DCB25                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        9e6024fe-2ca1-42dd-8a81-9ea1a5d6397b   ext4                                     
/dev/sda6        df00e527-5e91-4a96-892a-bd94296f340a   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-23-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set f2cc2e0bcc2dcb25
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set f2cc2e0bcc2dcb25
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set f2cc2e0bcc2dcb25
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set f2cc2e0bcc2dcb25
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 56a42f8ea42f6fa3
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

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


    .1GB: boot/grub/core.img
   4.4GB: boot/grub/grub.cfg
   1.3GB: boot/initrd.img-2.6.35-22-generic
    .1GB: boot/initrd.img-2.6.35-23-generic
   1.2GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: boot/vmlinuz-2.6.35-23-generic
    .1GB: initrd.img
   1.3GB: initrd.img.old
    .8GB: vmlinuz
   1.2GB: vmlinuz.old

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
}

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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9e6024fe-2ca1-42dd-8a81-9ea1a5d6397b
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=9e6024fe-2ca1-42dd-8a81-9ea1a5d6397b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9e6024fe-2ca1-42dd-8a81-9ea1a5d6397b
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=9e6024fe-2ca1-42dd-8a81-9ea1a5d6397b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9e6024fe-2ca1-42dd-8a81-9ea1a5d6397b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9e6024fe-2ca1-42dd-8a81-9ea1a5d6397b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9e6024fe-2ca1-42dd-8a81-9ea1a5d6397b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9e6024fe-2ca1-42dd-8a81-9ea1a5d6397b ro single 
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
    search --no-floppy --fs-uuid --set 9e6024fe-2ca1-42dd-8a81-9ea1a5d6397b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9e6024fe-2ca1-42dd-8a81-9ea1a5d6397b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 56a42f8ea42f6fa3
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


UUID=9e6024fe-2ca1-42dd-8a81-9ea1a5d6397b    /    ext4    errors=remount-ro    0    1
UUID=df00e527-5e91-4a96-892a-bd94296f340a    none    swap    sw    0    0

=================== sda5: Location of files loaded by Grub: ===================


 129.8GB: boot/grub/grub.cfg
 112.5GB: boot/initrd.img-2.6.35-22-generic
 116.3GB: boot/initrd.img-2.6.35-23-generic
 129.7GB: boot/vmlinuz-2.6.35-22-generic
 129.7GB: boot/vmlinuz-2.6.35-23-generic
 116.3GB: initrd.img
 112.5GB: initrd.img.old
 129.7GB: vmlinuz
 129.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  f9 1b ff e1 89 20 a0 f8  b4 21 23 1a 42 54 c2 8a  |..... ...!#.BT..|
00000010  02 44 09 c6 5b 10 a4 90  2a 4a 24 b0 c5 4b 3e 8b  |.D..[...*J$..K>.|
00000020  2c 12 35 62 41 09 ca c6  8c ba 92 3c bb 28 5a c2  |,.5bA......<.(Z.|
00000030  c4 b3 fd 8e 2e 2f 53 5a  38 05 03 0e 52 65 ac 43  |...../SZ8...Re.C|
00000040  4c 5e 91 98 a5 3e 19 0f  d2 88 4a dd 90 65 6c 65  |L^...>....J..ele|
00000050  3b 0b 8a 58 11 e1 0f a4  83 0f df 34 9e 36 54 9f  |;..X.......4.6T.|
00000060  16 3d 99 50 7a b2 af fe  47 6f 7d bb 65 8c 2c d8  |.=.Pz...Go}.e.,.|
00000070  62 9a da 65 96 e7 eb 0e  fe 26 ac f9 81 28 77 38  |b..e.....&...(w8|
00000080  2e bc 98 68 3a b4 63 62  4e 72 98 26 35 e4 3b af  |...h:.cbNr.&5.;.|
00000090  28 82 5b 98 6b 57 94 65  da 71 b9 e7 36 90 3c c8  |(.[.kW.e.q..6.<.|
000000a0  e6 6f fe e6 e9 ce 2b 71  7b c6 72 08 5f e5 15 8e  |.o....+q{.r._...|
000000b0  f0 0a 89 55 e8 c1 69 1a  09 63 5a 2c 4c 91 49 54  |...U..i..cZ,L.IT|
000000c0  3d a8 69 67 de 13 33 0e  1a 42 61 b2 26 c6 7e 00  |=.ig..3..Ba.&.~.|
000000d0  5c ab da 8e b4 f6 26 c5  73 26 8f 44 fb 7c 0f 6b  |\.....&.s&.D.|.k|
000000e0  c0 84 97 25 7c f2 3c 1e  1c 2b 9f 60 2e 6a 73 0f  |...%|.<..+.`.js.|
000000f0  71 9a 7c 11 9a 56 c8 31  38 96 42 54 f2 da 3a 4f  |q.|..V.18.BT..:O|
00000100  ce 76 36 08 4c 21 2d df  74 31 1d 4d 53 d5 35 13  |.v6.L!-.t1.MS.5.|
00000110  b6 3c 00 9e 4b 71 01 43  db ff 36 c6 94 5c 3b 8c  |.<..Kq.C..6..\;.|
00000120  4b 07 79 08 59 2a 7f dc  83 cb 90 e5 74 14 43 40  |K.y.Y*......t.C@|
00000130  aa 99 d4 09 3b 2e ec 40  2b d4 c9 10 b1 12 74 05  |....;..@+.....t.|
00000140  26 b3 8a d6 55 de 33 d3  8c 20 d3 cb 24 bc 71 26  |&...U.3.. ..$.q&|
00000150  1a 4e 62 93 a7 55 14 fc  78 fb e4 be a7 74 69 83  |.Nb..U..x....ti.|
00000160  a1 67 55 1a 47 b5 ee 51  b7 bc 7d 6c ed 4d 0a e7  |.gU.G..Q..}l.M..|
00000170  12 41 c2 eb ce ac a2 dc  54 c8 61 44 e8 45 38 9a  |.A......T.aD.E8.|
00000180  25 92 44 e1 d0 75 1b d1  14 29 8f ca fc 7c 08 42  |%.D..u...)...|.B|
00000190  e1 7b c9 9e f9 0c 3f 1e  53 05 e7 92 a1 fc 39 73  |.{....?.S.....9s|
000001a0  67 e1 9d d0 f4 70 84 79  8f 94 9e 9a 23 82 5a 2d  |g....p.y....#.Z-|
000001b0  45 a9 5b 21 c1 9c cb bc  87 fb 6c a7 1e c4 00 05  |E.[!......l.....|
000001c0  c8 ff 83 05 c8 ff 00 08  00 00 00 70 b6 02 00 05  |...........p....|
000001d0  c8 ff 05 05 c8 ff e0 7f  b6 02 20 a8 d5 02 00 00  |.......... .....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Angelbrand on 2010-12-20
didnt mean to offend any one by saying 'over priced techs' just theones here were going to charge me round $80 just to burn an ubuntu disk plus $120 to install it...

---

### Post by bcbc on 2010-12-20
So it looks like you migrated the wubi install, but installed grub incorrectly (you installed it from the wubi install, not within the chroot). 

If that's the only mistake you made, it's easy to fix:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

The grub.cfg on /dev/sda5 looks correct, the /etc/fstab looks correct, and so - I think it's likely that this will work properly.

Please note, that your grub menu describes your Windows as "Recovery" but it is your actual Windows (the boot flag is on that partition). That will the entry you need to boot windows.

If you have any issues, reinstalling lilo or the windows bootloader, will get Windows booting, and then you can still boot wubi. You can also try out the migrated install from there - or rerun the migration if required. 
But I'd try the proper grub install first.

---

### Post by oldfred on 2010-12-20
I think bcbc may have better ways to recover. You have installed grub to the MBR but whenever you do that from wubi the grub points to partition #256 which does not exist. You can install the windows or lilo boot loaders to get back into windows or wubi.

It does look like you have copied most of your system to sda5, but the grub.cfg still refers to sda3, the wubi install, so your grub.cfg will not work without update or manual configuration. I think you will have to chroot and do a update-grub and reinstall of grub2 to the MBR so it knows to boot sda5 not sda256 nor sda3.

Lets see what bcbc says. You can reinstall lilo if you want to get windows to work for now.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by Angelbrand on 2010-12-20
thanks heaps all up and running smoothly now. Im not going to try anything for at least a month now!! so confusing!! thanks heaps ya'll!!

---

### Post by bcbc on 2010-12-20
> **Angelbrand said:**
> thanks heaps all up and running smoothly now. Im not going to try anything for at least a month now!! so confusing!! thanks heaps ya'll!!

That's great! So did you end up reinstalling the grub bootloader as I suggested - or fall back to the windows bootloader (inquiring minds need to know).

I wanted to say that there were 2 grub.cfg files in the bootinfoscript results and the second was for sda5 that looked good. But I was too slow before your response.  But I'm hoping that the migration was a success!

---

### Post by QLee on 2010-12-21
[QUOTE=Angelbrand]didnt mean to offend any one by saying 'over priced techs' just theones here were going to charge me round $80 just to burn an ubuntu disk plus $120 to install it...[/QUOTE]

Just so you know, you didn't offend me, I'm retired anyway. However, when one posts in a public forum it's wise not to include anything in one's posts that might cause anyone reading to ignore your question. I agree the fees you cited seem inflated, it's possible they just didn't want to do the job but it does cost a lot to run a business in 2010 and years of training and experience to become a good tech.  You never know who might have the most useful answer, just like when you walk down the street you never know who might be an angel. Plumbers usually charge  a lot too, but when you need a plumber...

I'm glad you are back up and running, I was confident you would get good help here, as usual. Notice how even though we were all watching we don't try and confuse you with lots of different things to do from different people at the same time and how when you follow things slowly and carefully you can have success. That's a good thing about community.

---

### Post by Angelbrand on 2010-12-24
> **bcbc said:**
> That's great! So did you end up reinstalling the grub bootloader as I suggested - or fall back to the windows bootloader (inquiring minds need to know).

I wanted to say that there were 2 grub.cfg files in the bootinfoscript results and the second was for sda5 that looked good. But I was too slow before your response.  But I'm hoping that the migration was a success!

i reinstalled the grub boot loader. i tried the windows lilo first but it  didnt work. i also cant stand windows any way i would delete it but i have to wait until i get a removable hard drive so i can transfer files...

thanks heaps! =)

---

### Post by Angelbrand on 2010-12-24
> **QLee said:**
> Just so you know, you didn't offend me, I'm retired anyway. However, when one posts in a public forum it's wise not to include anything in one's posts that might cause anyone reading to ignore your question. I agree the fees you cited seem inflated, it's possible they just didn't want to do the job but it does cost a lot to run a business in 2010 and years of training and experience to become a good tech.  You never know who might have the most useful answer, just like when you walk down the street you never know who might be an angel. Plumbers usually charge  a lot too, but when you need a plumber...

I'm glad you are back up and running, I was confident you would get good help here, as usual. Notice how even though we were all watching we don't try and confuse you with lots of different things to do from different people at the same time and how when you follow things slowly and carefully you can have success. That's a good thing about community.

its great! and this one is far better than the windows forums... i went there once to ask a very simple question. how do i reset the apperance prefernces and the next 20 posts told me i had to completely reinstall windows...  of course i didnt and eventually figured it out on my own but vista is awful! i think so at least lol

---


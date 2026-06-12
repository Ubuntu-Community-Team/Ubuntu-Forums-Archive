---
title: "Ubuntu 11.04 dual boot with windows 7 doesn`t appear"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by Attefable on 2011-06-03
Hello forum.. i`m a linux newbie so please be bear with me :) 

first i downloaded ubuntu 11.04 from the website and burned the iso on a CD then booted from it and started the installation .. and it was so smooth i choosed install along side with windows ( i have windows 7 ) and i had two partitions one for windows 7 and another one for all my files and data.. so i choose everything by default and the installation and updating packages were fine , then it asked me for restart my machine, when it started it boot into windows 7 automatically, THERE IS NO  multiboot window appears to choose from which OS i want to boot to !!.. 

now i supposed i have Ubuntu 11.04 on my hard drive but i cannt access it, i dont know how to boot into Ubuntu and how i can choose from which os to boot, how i can make this multi boot window appear before windows 7 starts by it self??!.. i hope u got what i mean. 
thanks alot

---

### Post by Attefable on 2011-06-03
Hello forum.. i`m a linux newbie so please be bear with me  

first i downloaded ubuntu 11.04 from the website and burned the iso on a CD then booted from it and started the installation .. and it was so smooth i choosed install along side with windows ( i have windows 7 ) and i had two partitions one for windows 7 and another one for all my files and data.. so i choose everything by default and the installation and updating packages were fine , then it asked me for restart my machine, when it started it boot into windows 7 automatically, THERE IS NO multiboot window appears to choose from which OS i want to boot to !!.. 

now i supposed i have Ubuntu 11.04 on my hard drive but i cannt access it, i dont know how to boot into Ubuntu and how i can choose from which os to boot, how i can make this multi boot window appear before windows 7 starts by it self??!.. i hope u got what i mean. 
thanks alot

---

### Post by Rubi1200 on 2011-06-03
Hi and welcome to the forums :-)

You need to do the following please so we can see what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Attefable on 2011-06-03
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda2 has 
                       102193151 sectors, but according to the info from 
                       fdisk, it has 102207526 sectors.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 65. But according to the info from fdisk, 
                       sda5 starts at sector 102414440.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 867011344 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub on this drive. According to 
                       the info in the boot sector, sda6 starts at sector 
                       959. But according to the info from fdisk, sda6 starts 
                       at sector 915329024.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   102,414,374   102,207,527   7 NTFS / exFAT / HPFS
/dev/sda3         102,414,438   976,766,975   874,352,538   5 Extended
/dev/sda5         102,414,440   862,362,021   759,947,582   7 NTFS / exFAT / HPFS
/dev/sda6         915,329,024   976,766,975    61,437,952   7 NTFS / exFAT / HPFS
/dev/sda7         862,363,648   907,220,991    44,857,344  83 Linux
/dev/sda8         907,223,040   915,318,783     8,095,744  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        C678CE8378CE71AB                       ntfs       System Reserved
/dev/sda2        06DEDB7CDEDB630B                       ntfs       Win7
/dev/sda5        F896D7F596D7B1FC                       ntfs       Media
/dev/sda6        7CE45C29E45BE444                       ntfs       
/dev/sda7        30705932-ec83-48c0-a40e-586c74b10c29   ext4       
/dev/sda8        87c7e209-13f0-4ec7-9aa6-d293c3f7cd62   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root 30705932-ec83-48c0-a40e-586c74b10c29
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root 30705932-ec83-48c0-a40e-586c74b10c29
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 30705932-ec83-48c0-a40e-586c74b10c29
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=30705932-ec83-48c0-a40e-586c74b10c29 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 30705932-ec83-48c0-a40e-586c74b10c29
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=30705932-ec83-48c0-a40e-586c74b10c29 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 30705932-ec83-48c0-a40e-586c74b10c29
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 30705932-ec83-48c0-a40e-586c74b10c29
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root C678CE8378CE71AB
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
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=30705932-ec83-48c0-a40e-586c74b10c29 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=87c7e209-13f0-4ec7-9aa6-d293c3f7cd62 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 413.423252106 = 443.909836800  boot/grub/core.img                             1
 423.435855865 = 454.660788224  boot/grub/grub.cfg                             1
 412.613281250 = 443.040137216  boot/initrd.img-2.6.38-8-generic-pae           2
 412.090270996 = 442.478559232  boot/vmlinuz-2.6.38-8-generic-pae              2
 412.613281250 = 443.040137216  initrd.img                                     2
 412.090270996 = 442.478559232  vmlinuz                                        2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  3f 68 3e 1d 3c 20 1f 69  22 de 4e ed 2f 73 59 c5  |?h>.< .i".N./sY.|
00000010  df 94 b9 6c 5e ed cd cb  e2 87 8c 24 fd e1 73 af  |...l^......$..s.|
00000020  f6 cd 85 f1 23 59 79 21  cc 6d 4b b7 33 fd c7 23  |....#Yy!.mK.3..#|
00000030  84 5d f0 13 b6 d1 4f 9b  49 e5 cf 8e a7 01 d4 2f  |.]....O.I....../|
00000040  28 27 ac 1b ae a6 a3 05  8c d7 50 ec 20 83 bc 6a  |('........P. ..j|
00000050  62 8e e4 12 d4 d9 8d 12  14 82 4b a3 e8 e0 d1 47  |b.........K....G|
00000060  f1 9d 01 45 ee de 00 f0  48 f2 a6 0a a3 4b fb 77  |...E....H....K.w|
00000070  04 8c 0f e4 c3 6f bc f8  86 1e f4 26 5b bf 25 b3  |.....o.....&[.%.|
00000080  78 36 aa 2e ee e1 e0 b8  74 59 f7 02 b1 a7 4f f9  |x6......tY....O.|
00000090  84 1f ef b0 b2 34 bb 20  79 c5 6d 7d 61 c7 f7 94  |.....4. y.m}a...|
000000a0  01 3e 38 1e 5e ea dd 23  bf 87 0b 96 18 73 a6 b5  |.>8.^..#.....s..|
000000b0  18 be 9d ed ee e0 51 29  55 dc 76 83 e7 13 39 8f  |......Q)U.v...9.|
000000c0  24 ea 01 dc 5b 06 53 da  6c d5 00 42 0c de 9f b0  |$...[.S.l..B....|
000000d0  00 d9 71 75 da 1e bf f6  91 c0 64 07 b5 47 ec 49  |..qu......d..G.I|
000000e0  21 93 55 d7 0f b1 da 80  34 d3 d0 67 6c f3 cd c7  |!.U.....4..gl...|
000000f0  bb 9e c6 34 f9 b3 81 72  5a 0a 16 b7 a5 28 93 8b  |...4...rZ....(..|
00000100  64 0a 94 9d aa 4c e6 cb  3e 76 8a a2 be b5 70 2d  |d....L..>v....p-|
00000110  1e f8 98 e8 78 ac 96 1b  5b b2 5a 38 f3 f1 16 93  |....x...[.Z8....|
00000120  5f fb 2b 86 4b 7a 75 a1  32 69 92 ac fa 31 07 77  |_.+.Kzu.2i...1.w|
00000130  51 a8 64 72 95 d8 11 39  24 e4 ef 08 0b dd 4a bf  |Q.dr...9$.....J.|
00000140  45 fc cd 80 5a 9e 13 9d  a7 4c 7e 45 72 28 93 df  |E...Z....L~Er(..|
00000150  95 44 0a e6 fa 64 84 42  07 46 ee ea 33 1f 17 7b  |.D...d.B.F..3..{|
00000160  66 77 fd 33 c2 23 d9 59  4c ec 11 10 be 1f ea f0  |fw.3.#.YL.......|
00000170  b9 7b 8b 52 20 a3 f8 64  6f 3c ce ac f2 b1 73 ff  |.{.R ..do<....s.|
00000180  27 d0 3a 3d 10 5f 1c 3c  3c 34 0d c0 73 e2 8d 5f  |'.:=._.<<4..s.._|
00000190  ab 9a 02 ce 76 50 f7 67  6a 44 85 10 c0 e9 b8 f9  |....vP.gjD......|
000001a0  46 3d 78 30 9e e6 63 34  4f e9 e7 f1 ad 19 f4 16  |F=x0..c4O.......|
000001b0  45 86 d9 a9 f4 9b 3a 6e  be 4a fe 96 d8 53 00 fe  |E.....:n.J...S..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 3e e1 4b 2d 00 fe  |..........>.K-..|
000001d0  ff ff 05 fe ff ff 2a f2  73 30 70 9d a9 03 00 00  |......*.s0p.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Attefable on 2011-06-03
First thanks a lot for your reply.. i followed your steps and the pasted the content of the results.txt in the above reply.. and now i`m waiting what to do next? :D

---

### Post by Rubi1200 on 2011-06-03
Thanks for the results. I am trying to get some things clear here so please bear with me.

Did you move the install at some point from another disk or was another disk plugged in during the initial install?

The reason I ask is because the script says the install is on sda7 but fstab refers to it as sdb7.

Second, was sda6 supposed to be a boot partition? GRUB was accidentally installed there, but it appears to be a data partition?

Currently, you have Windows installed in the MBR of the drive which is why you are unable to boot Ubuntu.

Since all the Ubuntu files are where I would expect them to be this is how I would deal with this.

Use the LiveCD and run the following commands in a terminal:
[FONT=monospace]
[/FONT]```
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```Once the command completes you can reboot the computer taking out the CD.

Back in Ubuntu, run this command to add Windows to the boot menu:

```
sudo update-grub
```Let me know how it goes or if you need any other help.

---

### Post by Attefable on 2011-06-03
Okay thanks a bundle  now i`m using Ubuntu without the Live CD.. 
and in the boot menu the windows 7 was there.. but i didnt try it. i will continue with the terminal with the command of windows and see what will happen back in windows 7 

thanks alot!!

---

### Post by Rubi1200 on 2011-06-03
No problem, let me know if Windows also boots normally.

If yes, then you are back in business :-)

Once resolved, please mark this thread Solved using the Thread Tools near the top of the page.

Thanks.

---

### Post by cariboo on 2011-06-03
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Attefable on 2011-06-04
okay guys thanks alot .. everything is working now normal .. and sorry for posting it two times. i didnt got any reply back there so i though i should have posted here from the beginning :)

---

### Post by Rubi1200 on 2011-06-04
Good to know :-)

Enjoy!

---

### Post by jirico on 2012-01-25
Hello guys, I have the same problem with Windows XP.

I followed the steps and here what I got




  ```
                Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb6 
                       and looks at sector 832649216 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    30,716,279    30,716,217   7 NTFS / exFAT / HPFS
/dev/sda2          30,716,280    78,220,484    47,504,205   f W95 Extended (LBA)
/dev/sda5          30,716,343    78,220,484    47,504,142   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   409,593,239   409,593,177   7 NTFS / exFAT / HPFS
/dev/sdb2         819,187,710   976,771,071   157,583,362   f W95 Extended (LBA)
/dev/sdb5         819,187,712   827,925,992     8,738,281  82 Linux swap / Solaris
/dev/sdb6         827,926,528   839,643,135    11,716,608  83 Linux
/dev/sdb7         839,645,184   956,829,695   117,184,512  83 Linux
/dev/sdb8         956,831,744   976,771,071    19,939,328  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        74B84BA3B84B632A                       ntfs       
/dev/sda5        A89492939492641A                       ntfs       Documentos
/dev/sdb1        9010A30310A2F000                       ntfs       
/dev/sdb5        f936b8fc-30e8-4670-8342-0405f6d17a97   swap       
/dev/sdb6        8a439d03-b3c2-448a-98bb-b7d4fc0c4fb1   ext4       
/dev/sdb7        d6edb37a-21d2-4ea5-aff2-314ee11f0c6a   ext4       
/dev/sdb8        633ba438-e98e-4ef7-ad6b-ce35a65b59c7   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

============================= sdb6/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos8)'
search --no-floppy --fs-uuid --set=root 633ba438-e98e-4ef7-ad6b-ce35a65b59c7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos6)'
  search --no-floppy --fs-uuid --set=root 8a439d03-b3c2-448a-98bb-b7d4fc0c4fb1
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 8a439d03-b3c2-448a-98bb-b7d4fc0c4fb1
    linux    /vmlinuz-3.0.0-12-generic root=UUID=633ba438-e98e-4ef7-ad6b-ce35a65b59c7 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 8a439d03-b3c2-448a-98bb-b7d4fc0c4fb1
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=633ba438-e98e-4ef7-ad6b-ce35a65b59c7 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 8a439d03-b3c2-448a-98bb-b7d4fc0c4fb1
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 8a439d03-b3c2-448a-98bb-b7d4fc0c4fb1
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 74B84BA3B84B632A
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
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                grub/core.img                                  1
               =                grub/grub.cfg                                  1
               =                initrd.img-3.0.0-12-generic                    1
               =                vmlinuz-3.0.0-12-generic                       1

=============================== sdb8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb8 during installation
UUID=633ba438-e98e-4ef7-ad6b-ce35a65b59c7 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb6 during installation
UUID=8a439d03-b3c2-448a-98bb-b7d4fc0c4fb1 /boot           ext4    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=d6edb37a-21d2-4ea5-aff2-314ee11f0c6a /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=f936b8fc-30e8-4670-8342-0405f6d17a97 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  bd cb 1a b4 34 8c c6 36  6b 31 65 f4 69 b4 0b 32  |....4..6k1e.i..2|
00000010  b6 cd 86 b3 55 8c 7e 5b  77 0f 18 5d af 06 6f 21  |....U.~[w..]..o!|
00000020  d4 8c 95 55 b8 4d ad 87  92 87 57 a6 f2 3b 94 cb  |...U.M....W..;..|
00000030  67 b2 6d 5f 5d e8 7b d1  08 99 41 a8 48 ea 59 24  |g.m_].{...A.H.Y$|
00000040  98 29 39 42 b7 ac ab 35  20 00 05 c3 18 2c 41 40  |.)9B...5 ....,A@|
00000050  e7 00 49 a7 37 ce d6 58  4f d6 6c 9f 8c 07 4b 79  |..I.7..XO.l...Ky|
00000060  f0 a6 b6 8a 1c 70 f9 6b  d0 c9 c3 87 2d 38 5e 7e  |.....p.k....-8^~|
00000070  03 ac 2f f7 bb 9c b1 b3  f2 f1 70 fb 9b f7 13 14  |../.......p.....|
00000080  cd ac 75 54 85 a1 7e 1d  a8 53 57 89 48 25 24 e7  |..uT..~..SW.H%$.|
00000090  0d dd 7a d8 17 4c 47 89  ed 90 26 7d 76 23 5f cd  |..z..LG...&}v#_.|
000000a0  d7 b6 dc b9 75 57 62 35  b6 9e 86 9f 67 1f 8b b9  |....uWb5....g...|
000000b0  73 76 ec 98 a2 bd 19 8e  29 9d bc 1f 0f 3d 59 db  |sv......)....=Y.|
000000c0  5d 8a bf 8a d8 67 5e 6b  5c 71 dd 4c a6 24 44 06  |]....g^k\q.L.$D.|
000000d0  df 8a 26 77 f7 16 57 a6  6b 68 2e ae 83 11 16 40  |..&w..W.kh.....@|
000000e0  60 e5 48 0a 83 3a dc 64  4c ba b4 53 49 d2 2c 72  |`.H..:.dL..SI.,r|
000000f0  eb d7 07 31 2c 3c 89 31  82 e7 4a ce e3 0e 17 5a  |...1,<.1..J....Z|
00000100  a1 78 ef 13 62 7e f7 60  e7 2e 7e 5e 2a 41 d5 79  |.x..b~.`..~^*A.y|
00000110  c4 c8 6a 90 93 32 84 3c  6e 88 cc 32 ab 41 61 70  |..j..2.<n..2.Aap|
00000120  f1 78 27 34 68 52 5b b2  80 bb 54 92 22 74 50 3e  |.x'4hR[...T."tP>|
00000130  bd c5 9c b9 45 12 28 a2  9c d3 5b e2 f0 d9 31 3c  |....E.(...[...1<|
00000140  84 64 bc a0 96 b8 f4 e1  8f cf f5 3a 6d 7c 6a 3e  |.d.........:m|j>|
00000150  e5 35 31 ba 3e 94 6d a5  ad 86 1d 65 8c b2 78 1c  |.51.>.m....e..x.|
00000160  5d 1b 9c ad ed f4 11 cf  e3 24 9f d2 fb 06 ad 0e  |]........$......|
00000170  2a 06 c2 19 63 fb 0e 3c  cc 77 09 ab 5c a1 11 38  |*...c..<.w..\..8|
00000180  9e b8 7e 98 5b 3e aa 78  49 03 ce 09 f2 84 6a f6  |..~.[>.xI.....j.|
00000190  03 33 78 cf 46 11 10 0b  46 27 08 67 e8 ed e5 03  |.3x.F...F'.g....|
000001a0  ea 2a 21 9f ae 26 f9 68  8a 22 dd 21 8c 03 ae 58  |.*!..&.h.".!...X|
000001b0  d9 e2 c4 44 c1 f6 a2 b1  32 4a c9 4c 49 1b 00 fe  |...D....2J.LI...|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 0e db d4 02 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

Ubuntu doesnt appear on boot, I have already reinstalled but it`s not working... pls help me...

---

### Post by Mark Phelps on 2012-01-26
You need to be booting from the Ubuntu drive -- which is, hopefully, where you installed GRUB.  That should boot directly into Ubuntu.

If it does, then open a terminal and enter "sudo update-grub"

That will regenerate the GRUB menu and add an entry for Windows.

When you reboot, you will see entries for both OSs.

---

### Post by Malphas666 on 2012-03-25
Hi,I'm new to the linux family and I just installed Ubuntu 10.04 along with Windows 7 and I have the same booting problem.I'm running it from the CD because it's not showing on a multiboolt screen.The partition on which i installed ubuntu dissapeared.I must mention that Windows 7 is installed on a C:\ partition and Ubuntu is installed on an G:\ pertition. I'm going to leave the results from the boot info script here. Please help me :D


[B]              Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 41.0 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders, total 80043264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    76,668,927    76,666,880  83 Linux
/dev/sda2          76,670,974    80,041,983     3,371,010   5 Extended
/dev/sda5          76,670,976    80,041,983     3,371,008  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   204,796,619   204,796,557   7 NTFS / exFAT / HPFS
/dev/sdb2         204,796,620   312,560,639   107,764,020   f W95 Extended (LBA)
/dev/sdb5         204,796,683   312,560,639   107,763,957   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   976,770,143   976,770,081   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        f8229d24-dacf-4f88-b8ee-936aa1905eca   ext4       
/dev/sda5        f6f6f18e-0507-4b47-a6b4-22de50bcf65a   swap       
/dev/sdb1        0EB0FB72B0FB5F21                       ntfs       
/dev/sdb5        12E863E6E863C717                       ntfs       
/dev/sdc1        DA4817B448178DFF                       ntfs       Malphas

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     ext4       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set f8229d24-dacf-4f88-b8ee-936aa1905eca
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
search --no-floppy --fs-uuid --set f8229d24-dacf-4f88-b8ee-936aa1905eca
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
menuentry 'Ubuntu, with Linux 2.6.32-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f8229d24-dacf-4f88-b8ee-936aa1905eca
    linux    /boot/vmlinuz-2.6.32-38-generic root=UUID=f8229d24-dacf-4f88-b8ee-936aa1905eca ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f8229d24-dacf-4f88-b8ee-936aa1905eca
    echo    'Loading Linux 2.6.32-38-generic ...'
    linux    /boot/vmlinuz-2.6.32-38-generic root=UUID=f8229d24-dacf-4f88-b8ee-936aa1905eca ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-38-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f8229d24-dacf-4f88-b8ee-936aa1905eca
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f8229d24-dacf-4f88-b8ee-936aa1905eca
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 0EB0FB72B0FB5F21
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f8229d24-dacf-4f88-b8ee-936aa1905eca /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.138370514 = 8.738508800    boot/grub/core.img                             1
  28.139396667 = 30.214447104   boot/grub/grub.cfg                             1
   8.258426666 = 8.867418112    boot/initrd.img-2.6.32-38-generic              1
   8.160999298 = 8.762806272    boot/vmlinuz-2.6.32-38-generic                 1
   8.258426666 = 8.867418112    initrd.img                                     1
   8.160999298 = 8.762806272    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  64 43 00 00 00 00 00 00  06 a0 00 00 20 41 01 d9  |dC.......... A..|
00000010  a6 9c 44 3b 1d 01 00 00  00 00 00 40 d8 02 45 c0  |..D;.......@..E.|
00000020  fd 12 45 00 f0 0a c3 7c  94 d6 3e b3 fe 01 c3 00  |..E....|..>.....|
00000030  00 00 00 26 88 24 bf e1  1d 44 bf a1 af ef bb 39  |...&.$...D.....9|
00000040  1f 44 bf 47 89 24 3f 00  00 00 80 0b 0d 9a bb b3  |.D.G.$?.........|
00000050  9f b7 bb 3f fe 7f 3f d2  01 8b 3c 34 31 e0 42 00  |...?..?...<41.B.|
00000060  00 00 00 00 00 00 00 00  00 00 00 01 00 00 00 00  |................|
00000070  00 00 00 31 78 8b ad f1  7c f1 2d 4d 47 14 19 c0  |...1x...|.-MG...|
00000080  d7 02 45 40 fd 12 45 00  f8 1b c3 00 00 00 00 00  |..E@..E.........|
00000090  00 00 00 00 00 88 41 00  00 00 00 00 80 1d 3d 28  |......A.......=(|
000000a0  d4 64 43 00 00 00 00 64  00 00 00 00 00 00 00 00  |.dC....d........|
000000b0  00 00 00 00 00 00 00 00  00 f0 42 00 00 00 00 00  |..........B.....|
000000c0  00 00 00 00 00 00 00 20  00 00 00 01 00 00 00 00  |....... ........|
000000d0  00 00 00 55 05 00 00 00  00 00 00 01 00 00 00 00  |...U............|
000000e0  00 00 00 ec 0a f7 02 20  0b f7 02 00 00 00 00 00  |....... ........|
000000f0  00 00 00 00 04 00 00 00  03 00 00 00 00 00 00 00  |................|
00000100  00 00 00 64 00 10 00 00  80 1d 3d 28 d4 64 43 00  |...d......=(.dC.|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 7a  |...............z|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 48 44 00 00 96 42 00  |.........HD...B.|
00000140  00 a0 43 00 00 fa 43 00  00 a0 40 00 00 20 41 00  |..C...C...@.. A.|
00000150  00 20 41 00 00 80 40 00  00 00 40 00 00 80 3f 00  |. A...@...@...?.|
00000160  00 80 3f 00 00 80 3f 00  00 90 41 00 00 fa 44 00  |..?...?...A...D.|
00000170  40 1c 46 00 00 00 00 01  00 00 00 63 6c 5f 62 61  |@.F........cl_ba|
00000180  64 6c 61 6e 64 73 00 00  00 00 00 00 00 00 00 00  |dlands..........|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 20 44 00  00 20 44 00 00 d3 43 00  |..... D.. D...C.|
000001b0  00 80 3f 00 00 00 00 00  00 00 00 c0 d7 02 00 fe  |..?.............|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 70 33 00 00 00  |...........p3...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb2

00000000  05 c6 87 f3 55 fe 54 5c  b6 c1 82 fb 6c 5f 74 27  |....U.T\....l_t'|
00000010  3f 69 69 c1 b3 ce 71 72  6c d6 50 ef 09 5b ea a4  |?ii...qrl.P..[..|
00000020  63 67 12 1f 1f f7 c8 53  58 c0 03 ff f2 6b 13 0f  |cg.....SX....k..|
00000030  c2 72 e0 ec e5 d5 77 20  67 aa 41 13 d6 a3 4e b0  |.r....w g.A...N.|
00000040  7e 88 94 12 88 89 29 7c  34 35 80 52 b0 cd 1e ac  |~.....)|45.R....|
00000050  d2 04 cf dc 4e 40 40 9b  85 15 82 91 09 99 76 a0  |....N@@.......v.|
00000060  5d 48 38 3b 23 db 1e b4  3e ad 45 52 6c 33 d7 06  |]H8;#...>.ERl3..|
00000070  71 9c 77 07 71 93 5d 83  27 00 b7 72 7d 10 77 59  |q.w.q.].'..r}.wY|
00000080  3a ef 8e 78 0e bb 23 7f  25 aa c1 0e 44 72 d0 e5  |:..x..#.%...Dr..|
00000090  f8 da c1 5e 9f 01 89 5d  36 98 51 46 87 c7 9c 82  |...^...]6.QF....|
000000a0  8a f5 14 5e 01 76 23 47  03 6c a8 87 32 ca a2 61  |...^.v#G.l..2..a|
000000b0  6c 1e 9b 3a f7 14 00 5a  e2 a5 09 ff a0 98 b3 26  |l..:...Z.......&|
000000c0  38 91 4f 10 e8 c4 8b 70  ed 9d 48 10 d8 05 2c 99  |8.O....p..H...,.|
000000d0  24 b2 32 95 10 27 d5 e0  74 c7 24 6e f6 e3 6c 05  |$.2..'..t.$n..l.|
000000e0  66 2b 30 5b 81 ff 7b 05  44 e9 5f 2a e0 b9 46 5a  |f+0[..{.D._*..FZ|
000000f0  f1 2f 7c d0 e3 95 bc de  d2 89 07 7a 8a 52 d0 75  |./|........z.R.u|
00000100  4d d9 12 6f a0 e6 9f f8  86 90 50 56 5c 59 13 92  |M..o......PV\Y..|
00000110  83 33 5a b8 0b a2 ae bd  65 7b 43 21 b9 b2 72 8a  |.3Z.....e{C!..r.|
00000120  72 76 59 97 5f ab b4 ac  dc d7 dc 50 10 0d cd c0  |rvY._......P....|
00000130  07 57 34 3c 50 98 dc f8  ee fe 46 21 ea 15 a6 1b  |.W4<P.....F!....|
00000140  68 b5 b7 c5 16 25 ef 4c  26 97 df 16 75 c9 d3 f9  |h....%.L&...u...|
00000150  f9 75 0f c4 92 26 bf 28  5a 52 3b 43 80 60 dd b2  |.u...&.(ZR;C.`..|
00000160  b7 93 e6 b8 a2 71 69 d4  3b cd df 53 da 70 1f fb  |.....qi.;..S.p..|
00000170  9b 23 5a 1c 9e 7e 00 e7  da 86 db 5f 1c e5 cb cb  |.#Z..~....._....|
00000180  a3 25 d3 fc dd 42 d1 ae  d8 7b 59 83 8d f5 33 f1  |.%...B...{Y...3.|
00000190  c5 f7 c7 62 47 b3 06 d1  86 75 6b a7 f9 a3 48 28  |...bG....uk...H(|
000001a0  8c 1d ce f2 a1 70 60 86  02 2f 2e 59 1f 8b 1d 4e  |.....p`../.Y...N|
000001b0  1e 7b ee 96 9a d2 e9 e1  01 e7 e2 40 2c 56 00 fe  |.{.........@,V..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 f5 58 6c 06 00 00  |......?....Xl...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

[/B]

---


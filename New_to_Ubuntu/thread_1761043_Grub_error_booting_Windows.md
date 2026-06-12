---
title: "Grub error booting Windows"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by jarheead on 2011-05-17
Evening all, just after a helping hand to fix a problem with Grub2.

I had Ubuntu 10.10 and Windows XP dual booting successfully until an upgrade to Ubuntu 11.04.

Booting my computer I have now lost the Windows XP menu entry.

After reading numerous posts I have taken the plunge and manually edited grub.cfg and managed to add the Windows XP menu entry back to my Grub boot menu.

However, when I select the Windows menu entry I receive the following message:

[INDENT]Error: no argument specified
Press key to continue
[/INDENT]
After a few seconds my Windows system boots.

Can anybody help me help me clearing this error message at boot up?  I am so close to solving a problem that has taken some time to solve.
Any comment / assistance appreciated.

---

### Post by oldfred on 2011-05-17
Post this to see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply, Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

New version seems to be a .zip file that you have to extract the .sh file to run per instructions on site.

Did you run this to find XP?
sudo update-grub

---

### Post by jarheead on 2011-05-18
I ran sudo update-grub and it did not find the hard drive with XP.  It had no problem with the updated version of Ubuntu just no mention of XP.
I used a graphical tool to edit the timeout at boot up and that must have run update-grub again and over wrote my hashed grub.clg.  I have managed to paste the texty back in from a previous version and XP boots again, even the graphical does not recognise my XP hard drive.  Not sure if that has over complicated things?


CODE]                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid bc10cbb6-cc8c-4556-874f-c10dc25b784c root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   976,751,999   976,751,937   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     3,905,535     3,903,488  82 Linux swap / Solaris
/dev/sdb2           3,907,582   398,295,039   394,387,458   5 Extended
/dev/sdb5           3,907,584   150,390,783   146,483,200  83 Linux
/dev/sdb6         150,392,832   398,295,039   247,902,208  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4CB4E6DBB4E6C694                       ntfs       
/dev/sdb1        c31258d2-855f-4d05-ac06-0507f6ea7e84   swap       
/dev/sdb5        bc10cbb6-cc8c-4556-874f-c10dc25b784c   ext4       
/dev/sdb6        0facc6fc-1556-4eaf-9810-0c0b7bfc8370   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb6        /home                    ext4       (rw,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root bc10cbb6-cc8c-4556-874f-c10dc25b784c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root bc10cbb6-cc8c-4556-874f-c10dc25b784c
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=20
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root bc10cbb6-cc8c-4556-874f-c10dc25b784c
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bc10cbb6-cc8c-4556-874f-c10dc25b784c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root bc10cbb6-cc8c-4556-874f-c10dc25b784c
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bc10cbb6-cc8c-4556-874f-c10dc25b784c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root bc10cbb6-cc8c-4556-874f-c10dc25b784c
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bc10cbb6-cc8c-4556-874f-c10dc25b784c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root bc10cbb6-cc8c-4556-874f-c10dc25b784c
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bc10cbb6-cc8c-4556-874f-c10dc25b784c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root bc10cbb6-cc8c-4556-874f-c10dc25b784c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root bc10cbb6-cc8c-4556-874f-c10dc25b784c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4cb4e6dbb4e6c694
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=bc10cbb6-cc8c-4556-874f-c10dc25b784c /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=0facc6fc-1556-4eaf-9810-0c0b7bfc8370 /home           ext4    defaults        0       2
# swap was on /dev/sdb1 during installation
UUID=c31258d2-855f-4d05-ac06-0507f6ea7e84 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  28.064765930 = 30.134312960   boot/grub/core.img                             1
  54.365604401 = 58.374623232   boot/grub/grub.cfg                             1
   3.495590210 = 3.753361408    boot/initrd.img-2.6.35-28-generic              2
   3.033084869 = 3.256750080    boot/initrd.img-2.6.38-8-generic               2
  27.995159149 = 30.059573248   boot/vmlinuz-2.6.35-28-generic                 1
   5.023742676 = 5.394202624    boot/vmlinuz-2.6.38-8-generic                  1
   3.033084869 = 3.256750080    initrd.img                                     2
   3.495590210 = 3.753361408    initrd.img.old                                 2
   5.023742676 = 5.394202624    vmlinuz                                        1
  27.995159149 = 30.059573248   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  19 70 cd e7 5e 9e f2 47  9a 05 3f a2 2e c3 53 c6  |.p..^..G..?...S.|
00000010  7d 5d 03 23 e1 4f d8 2c  00 ef 40 6e f8 09 95 3d  |}].#.O.,..@n...=|
00000020  4b 58 4a 01 c5 ca 41 42  d3 5b 5b 0a 6a e4 42 b4  |KXJ...AB.[[.j.B.|
00000030  f2 ea 52 f8 c9 00 05 39  3a 06 41 97 99 20 0c 82  |..R....9:.A.. ..|
00000040  9e a8 5c 01 4a 8e 4b 84  8f 94 e0 53 6a a1 67 9f  |..\.J.K....Sj.g.|
00000050  35 3b a4 a4 55 ca 83 30  29 95 55 37 c8 6b b6 f3  |5;..U..0).U7.k..|
00000060  bb 8c 0b dd 34 94 96 4e  63 82 9b 20 91 ab c1 70  |....4..Nc.. ...p|
00000070  91 da ce 1f f7 19 be 24  1f 6d db 20 d5 f9 d2 41  |.......$.m. ...A|
00000080  9e 5d be 69 40 b5 d2 7a  3a 1d 55 6e 9f 0a 4b b9  |.].i@..z:.Un..K.|
00000090  de 3c f0 67 02 b4 c9 91  3e 3d 3d c3 e4 7d ec ff  |.<.g....>==..}..|
000000a0  40 1f ae 86 3c d1 b0 29  df e9 2b a1 bb 15 01 9d  |@...<..)..+.....|
000000b0  f6 19 d6 f1 85 d3 88 47  9e 4a 08 69 da d8 ef 77  |.......G.J.i...w|
000000c0  7a 80 9e 07 46 d5 29 59  0b de 08 66 7d 13 55 a8  |z...F.)Y...f}.U.|
000000d0  4d 97 fe 9f 1e 73 7b 79  2e 3b f1 32 f8 85 3b 4e  |M....s{y.;.2..;N|
000000e0  68 f8 14 fd 2b 2f 91 22  cd d3 22 5e 67 7f 07 4b  |h...+/.".."^g..K|
000000f0  32 70 49 d8 25 6d 03 6a  ec 45 0d cb 6e 9f 38 60  |2pI.%m.j.E..n.8`|
00000100  29 f5 58 fe ab e3 5e 8d  38 18 32 2e 4a 64 ba c1  |).X...^.8.2.Jd..|
00000110  a5 34 f0 36 0b 0f ac d4  05 78 4c 1e 41 82 0e f4  |.4.6.....xL.A...|
00000120  7a 5d e3 46 32 7e 87 9e  5a f2 d2 24 c1 95 b1 59  |z].F2~..Z..$...Y|
00000130  08 6c 53 58 13 12 c0 24  b8 0d 01 b1 da a2 e5 3f  |.lSX...$.......?|
00000140  fb 3c 5e 71 02 08 72 15  b5 77 8a 2a e1 c0 4c 28  |.<^q..r..w.*..L(|
00000150  83 c1 00 ba e7 f0 0c b3  54 81 22 03 01 f5 53 05  |........T."...S.|
00000160  02 fd 3e 60 11 a6 25 7b  f7 bd 97 38 82 86 78 4e  |..>`..%{...8..xN|
00000170  2f 0f 8b 6b 45 39 3a 27  2b 8d 73 82 e3 84 fc 05  |/..kE9:'+.s.....|
00000180  09 28 51 63 d3 b0 42 51  c3 c2 40 1e f2 72 c1 60  |.(Qc..BQ..@..r.`|
00000190  42 1e 83 12 09 4a ae dc  c1 98 14 f4 a4 26 a3 ec  |B....J.......&..|
000001a0  f2 74 2f f8 94 5d bc 11  31 01 16 09 c4 85 51 54  |.t/..]..1.....QT|
000001b0  b1 4a a9 a6 a1 ff c8 60  08 c5 69 c7 ec 8f 00 3c  |.J.....`..i....<|
000001c0  0a f3 83 fe ff ff 02 00  00 00 00 28 bb 08 00 fe  |...........(....|
000001d0  ff ff 05 fe ff ff 02 28  bb 08 00 b8 c6 0e 00 00  |.......(........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
[/CODE]

---

### Post by oldfred on 2011-05-18
I do not see anything wrong with results.txt.

Is the boot stanza from os-prober or is it one you added. It is identical to mine as far as I can tell, but mine is from 1.98.

If windows boots you could try editing the windows boot stanza. try deleting some lines, sometimes that makes a difference. Only the set root & chainload lines should be required, depending on which drive you are booting. You may need drivemap. Use the e on grub menu to edit boot stanza as a way to test alternatives.

Which drive are you booting and does it make any difference if you boot one or the other. You have grub2 in both drives.

---

### Post by jarheead on 2011-05-19
Thanks for the help oldfred.  Greatly appreciated.

It appears the problem is to do with a more pedantic coding of Grub2.

See link below.  Entered =root as described and hey presto.


[http://ubuntuforums.org/showthread.php?t=1662142](http://ubuntuforums.org/showthread.php?t=1662142)

---


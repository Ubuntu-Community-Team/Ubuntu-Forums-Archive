---
title: "Dual Boot Problem"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by neptune422 on 2010-11-30
Hi Ubuntu Community,

BACKGROUND: I hate windows. My dad's computer was slower than, well you know. I thought I would do him a favor and install Ubuntu so he could enjoy his computer again and I could stop having to drop by and fix his computer. I installed Ubuntu 10.10 on his windows XP machine making it a dual boot so he would not sweat the change and not not kill me if he needed to go back.
     The install went fine. I made Ubuntu the default OS if no other choice was selected after 10 seconds. The problem is that when I choose Windows, nothing happens except a blinking cursor at the top of the screen. Now all he's saying is he wished I had not done the install. This sucks! I wanted to get him converted and now I'm pulling my hair out trying to figure out how to fix this dual boot problem. And of course the problem is windows!!! nothing new there.

All I want is to figure out how to fix the computer so it will boot windows XP & Ubuntu.
I have a feeling that it will be some stupid little change that will get the dual boot to work correctly. But I need help on what change to make,  where to make the change, and how to do it so it's permanent. 

Here is the report I generated about the hard drive(s):

                     pre { font-family: "Times New Roman"; }p { margin-bottom: 0.08in; }                  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders, total 234493056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   139,151,848   139,151,786   7 HPFS/NTFS
/dev/sda2         139,153,406   234,491,903    95,338,498   5 Extended
/dev/sda5         139,153,408   230,498,303    91,344,896  83 Linux
/dev/sda6         230,500,352   234,491,903     3,991,552  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   234,436,544   234,436,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5428CD8D28CD6F14                       ntfs       PRESARIO                      
/dev/sda2: PTTYPE="dos" 
/dev/sda5        4e0ab77b-7465-46d8-8f76-f8302c86c57b   ext4                                     
/dev/sda6        bc630880-27aa-4401-a847-e0625acacc5a   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        72DC23E8DC23A4F7                       ntfs       Backup Slave Drive H          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] timeout=30 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS [operating systems] multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
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
search --no-floppy --fs-uuid --set 4e0ab77b-7465-46d8-8f76-f8302c86c57b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 4e0ab77b-7465-46d8-8f76-f8302c86c57b
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 4e0ab77b-7465-46d8-8f76-f8302c86c57b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4e0ab77b-7465-46d8-8f76-f8302c86c57b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 4e0ab77b-7465-46d8-8f76-f8302c86c57b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4e0ab77b-7465-46d8-8f76-f8302c86c57b ro single 
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
    search --no-floppy --fs-uuid --set 4e0ab77b-7465-46d8-8f76-f8302c86c57b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 4e0ab77b-7465-46d8-8f76-f8302c86c57b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5428cd8d28cd6f14
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
# / was on /dev/sda5 during installation
UUID=4e0ab77b-7465-46d8-8f76-f8302c86c57b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bc630880-27aa-4401-a847-e0625acacc5a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  88.5GB: boot/grub/core.img
 110.4GB: boot/grub/grub.cfg
  71.9GB: boot/initrd.img-2.6.35-22-generic
  88.5GB: boot/vmlinuz-2.6.35-22-generic
  71.9GB: initrd.img
  88.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  5a cc 49 2e 00 00 00 01  |........Z.I.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 82 37 f9 0d 00 00  |......?....7....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda2

00000000  f4 01 36 35 31 38 37 34  86 f4 01 64 6d 79 75 07  |..651874...dmyu.|
00000010  f8 01 b9 91 00 32 30 88  8a 01 58 5a 2e 34 30 33  |.....20...XZ.403|
00000020  06 ed 01 ec d4 01 41 89  ed 01 31 36 32 35 33 31  |......A...162531|
00000030  38 88 20 07 35 30 33 38  30 38 88 41 05 41 2e 32  |8. .503808.A.A.2|
00000040  32 34 37 09 6e 00 c9 03  00 32 33 2e 31 89 f8 01  |247.n....23.1...|
00000050  32 31 38 36 38 32 30 89  5a 09 42 2e 44 52 2e 34  |2186820.Z.B.DR.4|
00000060  37 89 5a 09 42 2e 44 52  2e 35 36 89 5a 09 42 2e  |7.Z.B.DR.56.Z.B.|
00000070  44 52 2e 37 32 86 33 02  45 4c 2e 31 88 f4 01 36  |DR.72.3.EL.1...6|
00000080  34 35 32 37 32 88 f4 01  34 34 31 36 38 39 88 f4  |45272...441689..|
00000090  01 34 31 30 39 33 38 88  f4 01 35 34 30 36 31 34  |.410938...540614|
000000a0  88 f4 01 36 35 33 39 36  37 89 f4 01 35 36 38 35  |...653967...5685|
000000b0  31 35 36 88 f4 01 38 31  39 36 32 33 86 33 02 45  |156...819623.3.E|
000000c0  46 2e 31 88 f4 01 35 34  39 31 30 38 88 f4 01 35  |F.1...549108...5|
000000d0  37 38 32 30 39 88 f4 01  34 34 34 38 35 39 86 33  |78209...444859.3|
000000e0  02 45 48 2e 31 88 f4 01  36 33 36 34 38 37 88 f4  |.EH.1...636487..|
000000f0  01 34 30 36 34 37 39 88  f4 01 36 38 33 31 32 33  |.406479...683123|
00000100  89 f4 01 32 34 39 35 30  30 33 86 33 02 45 4d 2e  |...2495003.3.EM.|
00000110  31 88 f4 01 33 37 35 34  30 34 88 f4 01 36 39 31  |1...375404...691|
00000120  33 39 38 89 f4 01 31 30  36 37 31 36 31 88 f4 01  |398...1067161...|
00000130  35 31 31 33 35 35 86 2f  02 62 71 63 6b 07 ec 01  |511355./.bqck...|
00000140  8b dd 00 34 31 84 89 06  33 39 07 f8 01 01 7b 00  |...41...39....{.|
00000150  33 39 86 f4 01 64 6c 61  72 06 f8 01 76 7a 00 39  |39...dlar...vz.9|
00000160  87 b3 00 44 2e 39 32 35  86 f4 01 64 66 64 79 86  |...D.925...dfdy.|
00000170  f4 01 64 66 65 61 86 f4  01 64 66 64 7a 86 f4 01  |..dfea...dfdz...|
00000180  64 6d 74 66 88 56 05 41  2e 31 33 34 38 85 86 04  |dmtf.V.A.1348...|
00000190  66 76 6f 85 86 04 66 76  70 08 9c 07 8f 55 01 33  |fvo...fvp....U.3|
000001a0  30 30 08 9c 07 8f 55 01  33 33 32 08 d1 00 6b 05  |00....U.332...k.|
000001b0  00 41 2e 32 85 b1 06 63  73 64 87 3e 08 41 00 fe  |.A.2...csd.>.A..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d0 71 05 00 fe  |............q...|
000001d0  ff ff 05 fe ff ff 02 d0   71 05 00 f0 3c 00 00 00  |........q...<...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200





Here is a screen shot of what I look at when grub2 starts:

[http://pavmedia.com/](http://pavmedia.com/)

1) Main menu
2) Ubuntu details
3) Windows details


I have tried pressing 'e' to edit the code and put in different values to no avail. I don't even know if what I change is ignored or used for that boot. I'm under the impression that my edits are used for that boot only and revert back the next start up. But in truth I don't even think my changes are being recognized.

Please help me figure out what to change and how to change it!!

Thank you!!!!!!!

Ubuntu noobie, neptune422

---

### Post by Chrisy91 on 2010-11-30
Hopefully you have your parents data backed up, do you have a copy of windows available? best thing to do is perform a clean install and start again. :)

---

### Post by neptune422 on 2010-11-30
Clean install of what, windows? Ubuntu? Both?

---

### Post by sikander3786 on 2010-11-30
Your bootinfoscript looks pretty normal. All the boot files for Windows seem in tact. Shouldn't be causing a problem anyway...

Is a Windows disc available? If yes, I would recommend to fixmbr and fixboot from the Windows disc, once you are able to boot Windows successfully, hopefully reinstalling Grub won't break it again.

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

For re-installing Grub,

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by neptune422 on 2010-11-30
Hmm, I followed the first link you gave me and I followed the directions. Problem is that I didn't read the last paragraph in the instructions:

*Also, make sure you only use these commands on a system with one  operating system installed. If you have more than one operating system  installed, fixmbr and fixboot could mess up everything.*

The computer won't boot now unless I have the live CD in. When I go to fix grub2 using the live CD it tells me it can't find the place I want to mount grub2.

Please Help!!!

---

### Post by sikander3786 on 2010-11-30
> Also, make sure you only use these commands on a system with one operating system installed. If you have more than one operating system installed, fixmbr and fixboot could mess up everything.

No problem with that statement. We know that messes up Grub so I posted a link to reinstall Grub as well.

What happens if you try to boot from the HDD? Does it boot XP successfully? If not, any errors or just blinking cursor?

---

### Post by neptune422 on 2010-11-30
This is the message I get when I start the computer:

A disk read error occurred
Press crtl + alt +delete to start

---

### Post by madjr on 2010-11-30
lol, this happen to me once.

to buy some time i came up with a weird excuse, like it was windows-partition/malware/slowness/reg-errors fault and that ubuntu actually **saved** his computer, because windows was going to collapse at anytime anyway :P

after a day or 2 i got xp working again, but he was already comfortable browsing in ubuntu.

if you place some nice **big icons** for the browser, etc, and make things a bit more familiar (like one panel), he wont even complain after the first day (specially since he knows he wont deal with slowness and viruses anymore).

Sometimes you can take the positive out of what may seem a bad situation.

surely my example is not the most desirable thing to do, but its already messed up, so you cant go back in time. The best thing you can do right now is get him off your back for a while so you can fix his computer in peace.

---

### Post by sikander3786 on 2010-11-30
> **neptune422 said:**
> This is the message I get when I start the computer:

A disk read error occurred
Press crtl + alt +delete to start
Try fixmbr once more and also run chkdsk c: from the recovery console this time. Then reboot and see....

[COLOR="Red"]**Edit:**[/COLOR] Also make sure the HDD is not configured to be a slave drive. It should be master as that errors seems to appear with an HDD setup as slave.

---

### Post by oldfred on 2010-11-30
Did you by any chance edit boot.ini from Ubuntu? Your has the entires all on one line. Mine looks like this:

```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

```

If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.

The windows repairs mentioned above also should update boot.ini from windows and fix it, if that is the problem.

---

### Post by neptune422 on 2010-11-30
I redid the fixmbr & fixboot

Still getting the same error message.

I've done nothing with boot.ini


If I can't get grub2 installed again using the live CD am I totally sunk?

---

### Post by sikander3786 on 2010-11-30
I am not sure about the error you are receiving regarding XP.

But these commands should install Grub and boot you back to Ubuntu at least.

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Note, for the second command it is just sda and not sda5.

---

### Post by neptune422 on 2010-11-30
When I type sudo mount /dev/sda5/mnt

I get the error:
Can't find /dev/sda5/mnt in /etc/fstab or /etc/mtab

---

### Post by sikander3786 on 2010-11-30
Put a space between /dev/sda5 and /mnt :-)

Or if possible, just copy/paste the commands from this page straight in to your terminal.

---

### Post by neptune422 on 2010-11-30
OK. That worked. THX

Who knew that a space makes that much of a difference.

So now I'm back to where I started, XP still won't start up. Is there something I can do in grub to get XP to start? It's like it goes to look for the starting point of windows and just can't find it so it stops there with the cursor blinking. That's just my own theory of course.

I was wondering if it would make a difference to change:

File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /[COLOR=Red]**NTDETECT.COM**[/COLOR]

Maybe if I could take that red part out...could it be something simple like that? Based on the report generated it seems as though XP is there with no problem; what on earth could be stopping it from booting...

---

### Post by nm_geo on 2010-11-30
Does this strike anyone as strange.

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for[COLOR=Red] (,msdos5)[/COLOR]/boot/grub.


Mine and others Dual booting;

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

Not sure if it is an issue but why would it look for (,msdos5)

---

### Post by nm_geo on 2010-11-30
> **neptune422 said:**
> OK. That worked. THX

Who knew that a space makes that much of a difference.

So now I'm back to where I started, XP still won't start up. Is there something I can do in grub to get XP to start? It's like it goes to look for the starting point of windows and just can't find it so it stops there with the cursor blinking. That's just my own theory of course.

I was wondering if it would make a difference to change:

File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /[COLOR=Red]**NTDETECT.COM**[/COLOR]

Maybe if I could take that red part out...could it be something simple like that? Based on the report generated it seems as though XP is there with no problem; what on earth could be stopping it from booting...

Here is mine Neptune just like yours I think they will try to install Grub2 again;

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

---

### Post by oldfred on 2010-11-30
Did you in windows run the update that rewrites boot.ini? Or copy & paste (not using gedit) a new boot.ini?

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

BOOTCFG  /rebuild
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

---

### Post by neptune422 on 2010-11-30
I'll assume that you have a dual boot system and that both boot fine...

In that case taking out the red highlighted code NTDETECT.COM will not fix the problem.

Thank you for the comparison.

---

### Post by nm_geo on 2010-11-30
> **neptune422 said:**
> I'll assume that you have a dual boot system and that both boot fine...

In that case taking out the red highlighted code NTDETECT.COM will not fix the problem.

Thank you for the comparison.

  Well yes I am now doing a triple boot, but our XP partition do look the same. I am trying to learn here also..

---

### Post by oldfred on 2010-11-30
The ,msdos5 is to know it is MBR (msdos) style partitioning. This is the new standard in grub2.

I boot Maverick from sdb and have sdb set as gpt style partitions.
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,gpt2)/boot/grub.

---

### Post by nm_geo on 2010-11-30
I figured you would know and respond thanks oldfred.

---

### Post by nm_geo on 2010-11-30
Question: 

Neptune can you see the Windows partition under Places?
And then can you open it? the Windoz boot.ini is located there if you can.

---

### Post by neptune422 on 2010-11-30
I booted into the XP repair console on the XP disk.

I ran the **map** command. The results are as follows:

C: NTFS               67945MB        \Device\Harddisk0\Partition1
G:                         44603MB       \Device\Harddisk0\Partition2
H:                          1950MB         \Device\Harddisk0\Partition3
D: NTFS             114470MB         \Device\Harddisk1\Partition1
A:                                                 \Device\Floppy0
E:                                                 \Device\CdRom0
F:                                                 \Device\CdRom1


Does this give any clues as to what will fix the boot problem?

There are two hard drives in the tower. One is the master and the second is the slave which is used as a backup drive. When I boot into 10.10 I can see all the files on the drive including all the windows files. I looked for the boot.ini file and found it and a backup boot.ini file. It listed the original XP OS and second one whice I mistakenly added earlier today when I was fiddling around. 

I'm not sure why there are so many partitions...There should only be two, 1 for XP and the other for 10.10

---

### Post by nm_geo on 2010-11-30
What listed the second Win OS your boot.ini.
OPen boot.ini with gedit and compare to this one.

```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

### Post by neptune422 on 2010-11-30
**This is what my boot.ini file, opened with gedit, says:**

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
[COLOR=Red]default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP" /fastdetect /NoExecute=OptIn
[/COLOR][COLOR=Black][COLOR=Red]default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="exit" 3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="/fastdetect" /fastdetect[/COLOR]
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn[/COLOR]

The red indicates the entries I made in error while screwing around with the XP recovery disk. I would love to just delete those lines but I haven't because I keep reading that it's not a good idea to directly change the boot.ini file. I'm now trying to find a way to rid the file of the stuff in red that I added.

That being said, the last listing:
[COLOR=Black]default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn[/COLOR]


looks almost just like yours **nm_geo**. Except the order is different:
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"[I] /noexecute=optin /fastdetect

[/I]Do you think that is something that could be the problem? A simple reversal of code...

---

### Post by nm_geo on 2010-11-30
> **neptune422 said:**
> I booted into the XP repair console on the XP disk.


C: NTFS               67945MB        \Device\Harddisk0\Partition1
G:                         44603MB       \Device\Harddisk0\Partition2
H:                          1950MB         \Device\Harddisk0\Partition3
D: NTFS             114470MB         \Device\Harddisk1\Partition1
A:                                                 \Device\Floppy0
E:                                                 \Device\CdRom0
F:                                                 \Device\CdRom1


I'm not sure why there are so many partitions...There should only be two, 1 for XP and the other for 10.10
  
The partitions look okay to me..  Notice harddrive 0 has three partitions c: Windows, G: Ubuntu and H: Linux Swap file.

---

### Post by nm_geo on 2010-11-30
> **neptune422 said:**
> **This is what my boot.ini file, opened with gedit, says:**

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
[COLOR=Red]default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP" /fastdetect /NoExecute=OptIn
[/COLOR][COLOR=Black][COLOR=Red]default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="exit" 3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="/fastdetect" /fastdetect[/COLOR]
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn[/COLOR]

The red indicates the entries I made in error while screwing around with the XP recovery disk. I would love to just delete those lines but I haven't because I keep reading that it's not a good idea to directly change the boot.ini file. I'm now trying to find a way to rid the file of the stuff in red that I added.

That being said, the last listing:
[COLOR=Black]default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn[/COLOR]


looks almost just like yours **nm_geo**. Except the order is different:
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"[I] /noexecute=optin /fastdetect

[/I]Do you think that is something that could be the problem? A simple reversal of code...

I wish I could tell you for sure, but that was what oldfred was asking you.. How did you add those lines in red? You have home edition and I have XP pro are the only differences..and you probably do have Home Edition don't change that for sure..

---

### Post by nm_geo on 2010-11-30
ANOTHER thought check the boot.ini backup see if it does not have the red lines..

It may have been created when you added things and might be really an original.

---

### Post by neptune422 on 2010-11-30
The red highlighted lines I added by mistake when fooling around with the XP recovery disk. I added them by mistake using the bootcfg /add comand.

I just edited the boot.ini file with gedit and saved it. Now the 'bootcfg /list', only shows the one correct and original entry. I think I'll change the remaining entry to get rid of the 'NoExecute=OptIn' line to see if that makes any difference.

All this is using the XP recovery disk.

---

### Post by nm_geo on 2010-11-30
> **neptune422 said:**
> The red highlighted lines I added by mistake when fooling around with the XP recovery disk. I added them by mistake using the bootcfg /add comand.

I just edited the boot.ini file with gedit and saved it. Now the 'bootcfg /list', only shows the one correct and original entry. I think I'll change the remaining entry to get rid of the 'NoExecute=OptIn' line to see if that makes any difference.

All this is using the XP recovery disk.

What does the backup file look like?  Open it with gedit too and it might be just what you need.

---

### Post by neptune422 on 2010-11-30
The boot.ini backup file was the same.

At this point I have tried modifying the boot.ini file to have NoExecute=OptIn there and not there. Either way it makes no difference, XP won't start.

Now I'm going back to try and see if I can get windows to get rid of grub and see if I can boot into XP.

---

### Post by nm_geo on 2010-11-30
> **neptune422 said:**
> The boot.ini backup file was the same.

At this point I have tried modifying the boot.ini file to have NoExecute=OptIn there and not there. Either way it makes no difference, XP won't start.

Now I'm going back to try and see if I can get windows to get rid of grub and see if I can boot into XP.
  
You should be able to do that if you do the fixboot and fixmbr from the recovery disk.  You really should not edit the boot.ini with gedit but the fixboot should repair that.  I just wanted you to look at it with gedit should have said that.

---

### Post by oldfred on 2010-11-30
Did you not read post #10 - use nano if you want to edit boot.ini from Ubuntu. Gedit just corrupted your boot.ini with the wrong line endings.

Use 
BOOTCFG  /rebuild
Details on why:
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)

Or you can just use nano and copy any of the boot.ini that we have posted.

Do you have the backup also mounted? Grub may be confused if you have the original and the backup both available to boot?

---

### Post by neptune422 on 2010-12-01
I can't seem to find nano in order to use it, can you believe that! It is even listed as installed on my computer in the package manager. However, my modifying the boot.ini file has not created any new problems. So for now I guess I'll leave the boot.ini file alone.

I have edited my boot.ini file and then, using the XP cd, deleted grub by replacing the mbr with the windows mbr. This unfortunately did not fix the problem in that I could still not boot XP. I have edited the boot.ini file back to what it was before using gedit. I wanted to use nano but I can't find it for the life of me. I even used ALT +F2 to find it and it won't come up. I also tried right clicking on the file and choose another program and it's not there.

So now, assuming that my boot.ini file is not corrupt, I am right where I started from in the beginning. I get the GRUB menu which lists all my OS's (Ubuntu & Windows) and only Ubuntu will start.

What's next? I really would love to get GRUB2 to do it's job and start windows. At this point I can't start XP even as a single OS. How or what can I change in GRUB2 as another possible fix?

---

### Post by oldfred on 2010-12-01
nano is a command line editor.

sudo nano /boot/grub/grub.cfg

for your boot.ini

sudo nano /media/{whatever path is to windows}/boot.ini

To make it easier to copy path I use Nautilus to drill down to the folder with the file I want to edit and copy & paste into the command in the command line.

Another way I use is to use nautilus to drill down, right click on file, open with other applications, use custom command, then type in sudo nano on command line it opens. Next time you do not have to open custom command as the sudo will be listed as a open with command

You can just copy & paste the entries we have shown into your boot.ini if it is the same drive 0 and partition 1.

---

### Post by runeh76 on 2010-12-01
> **nm_geo said:**
> The partitions look okay to me..  Notice harddrive 0 has three partitions c: Windows, G: Ubuntu and H: Linux Swap file.


Partitions looks strange to me..dunno
But why u dont make just re-install, backup everything and Format good those hd. Install Windows first and use Ext3 to ubuntu. U have 2hd.s so why u try to install ubuntu to same hd where is C: ?

---


---
title: "Dedicated partitions instead of common space"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by parthgadhia on 2011-05-10
Hello,

I'm using a Dell Inspiron 1545, Core 2 Duo 2.00 GHz. 3 GB Ram, and 320 GB hard drive partitioned into C and D.

I had been using Vista for the last 2 years, and just recently installed Ubuntu dual-boot.
 
My question is, C and D were both Vista drives, and I installed Ubuntu on D. Now, D is being shared by both Vista and Ubuntu. However, I don't want that. It's a little too clumsy. Is there anyway I can make D: a dedicated Ubuntu drive, and C a dedicated Vista drive without any common sharing between the 2?

Vista can be ONLY C and Ubuntu ONLY D?

Any help will be highly appreciated.

Thanks. :)

---

### Post by Not unique on 2011-05-10
Yes I'm sure there is I have seen it before I will look it up and post some thing.
However let me get it straight you have a PC with 1 hard drive separated into 2 partitions and you want what? Windows on one and Ubuntu on the other ?

---

### Post by Locke_99GS on 2011-05-10
Use the entirety of /dev/sdb during install. Where and how to install would have been options when installing Ubuntu.

edit: nvm - one drive with multiple partitions. You'd have to give us more detailed information if you want detailed answers. Give the output of "sudo fdisk -l" so we can see your current partitioning scheme.

---

### Post by Not unique on 2011-05-10
How can D be shared by Vista and Ubuntu? I'm confused or am I being dumb?

---

### Post by Locke_99GS on 2011-05-10
Maybe it's a wubi thing? (I don't know anything about wubi)

---

### Post by parthgadhia on 2011-05-10
Thank you for your replies. 

> **Not unique said:**
> Yes I'm sure there is I have seen it before I will look it up and post some thing.
However let me get it straight you have a PC with 1 hard drive separated into 2 partitions and you want what? Windows on one and Ubuntu on the other ?

Yes, exactly. I have a PC with one 320 GB hard drive, and I want Vista on one and Ubuntu on the other. It is like that right now. But whatever I save on my Ubuntu drive can be accessed through Vista, since D: shows up in Vista as well, which is actually my Ubuntu drive. 

I installed Ubuntu through WUBI. 

> **Locke_99GS said:**
> Use the entirety of /dev/sdb during install. Where and how to install would have been options when installing Ubuntu.

edit: nvm - one drive with multiple partitions. You'd have to give us more detailed information if you want detailed answers. Give the output of "sudo fdisk -l" so we can see your current partitioning scheme.

Hey, here are my sudo fdisk -1 results:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1df919ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51200000    7  HPFS/NTFS
/dev/sda2            6375       20498   113446864+   7  HPFS/NTFS
/dev/sda3           20498       30402    79550465    5  Extended
/dev/sda5           30015       30402     3103744   82  Linux swap / Solaris
/dev/sda6           29629       30015     3096576   82  Linux swap / Solaris
/dev/sda7           20498       29242    70238208   83  Linux
/dev/sda8           29243       29628     3099648   82  Linux swap / Solaris

Partition table entries are not in disk order



I can't access the Vista drive from Ubuntu but I can access the Ubuntu drive from Vista, and I don't want it like that. I want them seperate. :)


> **Locke_99GS said:**
> Maybe it's a wubi thing? (I don't know anything about wubi)

I guess, I used WUBI to install. :)

---

### Post by parthgadhia on 2011-05-10
Bump.

---

### Post by Not unique on 2011-05-10
Sounds like Wubi I would of clean installed Win then Lin (Ubuntu) I don' know if you can do much about it but I found these hope they (or some one else) can help.

[U][I][http://osdir.com/ml/kubuntu-users/2010-02/msg00222.html](http://osdir.com/ml/kubuntu-users/2010-02/msg00222.html)
[http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer](http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer))
[/I][/U]

If you have to fresh install remember to **back up** but maybe some one knows.

---

### Post by oldfred on 2011-05-10
If you have wubi, you also have a full partitioned install in sda7 and somehow have 3 swap partitions (only one suggested).

Do you want to keep wubi? Do you have data in wubi that you want in your full install. Vista & Ubuntu will be then totally separate but we normally suggest a shared NTFS partition (your d: drive) for any data you may want in both.

Post this for details on your installs.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

more info on wubi.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by parthgadhia on 2011-05-10
Thank You.

Here are my Boot Info Script results:


```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   102,402,047   102,400,000   7 HPFS/NTFS
/dev/sda2         102,402,048   329,295,776   226,893,729   7 HPFS/NTFS
/dev/sda3         329,295,870   488,396,799   159,100,930   5 Extended
/dev/sda5         482,189,312   488,396,799     6,207,488  82 Linux swap / Solaris
/dev/sda6         475,981,824   482,174,975     6,193,152  82 Linux swap / Solaris
/dev/sda7         329,295,872   469,772,287   140,476,416  83 Linux
/dev/sda8         469,774,336   475,973,631     6,199,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        14BABEFBBABED886                       ntfs                                     
/dev/sda2        7E308CFB308CBBA1                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        71b0c30b-fa50-40cf-85a4-97e63cd3eb71   swap                                     
/dev/sda6        d4349931-ae2c-47a4-b55f-54d21b030011   swap                                     
/dev/sda7        be25be80-6af0-423c-8c49-094c6f545f4b   ext4                                     
/dev/sda8        cb716de8-32a1-4acc-a710-2a4d28404c54   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)
/dev/sda2        /media/7E308CFB308CBBA1  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root be25be80-6af0-423c-8c49-094c6f545f4b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root be25be80-6af0-423c-8c49-094c6f545f4b
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root be25be80-6af0-423c-8c49-094c6f545f4b
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=be25be80-6af0-423c-8c49-094c6f545f4b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root be25be80-6af0-423c-8c49-094c6f545f4b
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=be25be80-6af0-423c-8c49-094c6f545f4b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root be25be80-6af0-423c-8c49-094c6f545f4b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root be25be80-6af0-423c-8c49-094c6f545f4b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 14BABEFBBABED886
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda8 during installation
UUID=cb716de8-32a1-4acc-a710-2a4d28404c54 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 190.2GB: boot/grub/core.img
 205.2GB: boot/grub/grub.cfg
 169.8GB: boot/initrd.img-2.6.38-8-generic
 190.2GB: boot/vmlinuz-2.6.38-8-generic
 169.8GB: initrd.img
 190.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  f6 fc 79 5d bb 9a f5 72  d9 ae 78 53 1e 1a 08 7a  |..y]...r..xS...z|
00000010  0a 24 fe 18 17 ab aa 64  79 7d bd 4d f7 2b 86 8e  |.$.....dy}.M.+..|
00000020  bc 8c bb 48 2e 7d c1 96  0a 39 b0 88 29 b5 d2 2b  |...H.}...9..)..+|
00000030  3e af e6 8b b2 cf f0 c9  0b dc 9d 8a a5 d3 e3 ed  |>...............|
00000040  b1 b1 32 aa bb 95 66 9d  23 de e4 ff 3b d5 c3 e9  |..2...f.#...;...|
00000050  50 3d c3 2b 50 5c 5d 73  95 22 57 4b 2c d4 d7 61  |P=.+P\]s."WK,..a|
00000060  14 8b bd e4 33 d2 db ff  ac d7 70 ef b3 1e 08 63  |....3.....p....c|
00000070  49 30 5e 8e e1 b5 45 ee  f7 76 7c f2 93 6f 4c b0  |I0^...E..v|..oL.|
00000080  d4 55 fd c7 cf e7 ae d7  0f b5 45 02 cf 1f 5d f9  |.U........E...].|
00000090  82 33 79 a1 4b c2 98 af  97 4c 2a ee d7 4f 65 8f  |.3y.K....L*..Oe.|
000000a0  97 ce 23 6a 5b 1a 11 65  ca 36 ed 21 12 99 51 f1  |..#j[..e.6.!..Q.|
000000b0  1e 35 57 75 cd f5 75 a2  47 cb da 54 af 7d d5 54  |.5Wu..u.G..T.}.T|
000000c0  79 46 84 6c 0f 07 02 e7  84 c8 7d c2 6b 87 aa 81  |yF.l......}.k...|
000000d0  fd 9a 3c 56 04 28 b0 49  a7 93 05 e0 72 36 d1 85  |..<V.(.I....r6..|
000000e0  4b c2 7c 8a 1f 3f ec a4  89 85 80 b8 24 28 96 47  |K.|..?......$(.G|
000000f0  aa f1 bc 00 a1 d6 74 c0  cc 70 4d fd ec 57 08 7e  |......t..pM..W.~|
00000100  ac 7d 00 df 8c ff 3b 84  e2 4f ae 01 ce e5 34 f1  |.}....;..O....4.|
00000110  98 5a 32 2a f6 3c 7f 61  ab 56 58 d7 f6 e6 3d e9  |.Z2*.<.a.VX...=.|
00000120  01 f8 05 d5 24 fe 3a 0a  61 e8 75 ca b6 70 e4 97  |....$.:.a.u..p..|
00000130  87 ce b9 30 f9 9f 69 ff  50 66 b6 69 5c 79 3d c2  |...0..i.Pf.i\y=.|
00000140  d0 1a e6 2d 3c 98 f4 17  f3 95 c0 1b 15 cf f1 f8  |...-<...........|
00000150  4e 3f a6 88 ce 93 64 98  20 d9 61 df 5d f5 3c 25  |N?....d. .a.].<%|
00000160  aa 1f df 73 e6 84 9d b3  8f 0a 61 b8 93 4e 89 7e  |...s......a..N.~|
00000170  a3 ca 7a cf ec c7 90 bd  c1 4c 14 bf 8a eb bf 6e  |..z......L.....n|
00000180  ba e4 7e 9f 7b d3 0f 9c  af 6e 1e f5 32 25 97 cd  |..~.{....n..2%..|
00000190  87 fc f2 3c 57 7c 7d 3f  97 1e 77 d6 4f cc 32 3e  |...<W|}?..w.O.2>|
000001a0  ef 63 d3 04 3d df dd e9  9d 18 4b 16 36 98 22 58  |.c..=.....K.6."X|
000001b0  a7 d2 75 d3 7d 48 e7 ab  0f 9f f7 74 ea 61 00 fe  |..u.}H.....t.a..|
000001c0  ff ff 82 fe ff ff 02 f8  1c 09 00 b8 5e 00 00 fe  |............^...|
000001d0  ff ff 05 fe ff ff be 20  be 08 44 9f 5e 00 00 00  |....... ..D.^...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

I'm fine either way actually, just need to know what's happening with the computer. If a common drive's recommended, then that's how I'll keep it.
I thought that I'd done something wrong, is why both the OS's were sharing space, and was afraid my hard drive would crash. 
Anyway, what do you reckon I should do? Keep it the way it is? Or alter it?

---

### Post by oldfred on 2011-05-10
Other than the two extra swaps, I do not see anything wrong. You do not have wubi but a full install in sda7 and swap in sda8.

I would use your D: in windows as data partition in Ubuntu so you can share data. I only suggest reading (not writing) from the Vista system partition, if you decide to mount it at all from Ubuntu. There are some advantages to auto mounting your NTFS data partition.
Shared NTFS partition:
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Link XP my docs
[http://www.techsupportalert.com/how_to_move_my_documents.htm](http://www.techsupportalert.com/how_to_move_my_documents.htm)

---

### Post by parthgadhia on 2011-05-10
> **oldfred said:**
> Other than the two extra swaps, I do not see anything wrong. You do not have wubi but a full install in sda7 and swap in sda8.

I would use your D: in windows as data partition in Ubuntu so you can share data. I only suggest reading (not writing) from the Vista system partition, if you decide to mount it at all from Ubuntu. There are some advantages to auto mounting your NTFS data partition.
Shared NTFS partition:
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Link XP my docs
[http://www.techsupportalert.com/how_to_move_my_documents.htm](http://www.techsupportalert.com/how_to_move_my_documents.htm)


Ok. Just to make sure I understood it correctly.

So Essentially, I have 50 odd GB as my Windows partition, 52 GB as my Ubuntu OS partition, and another 116 GB as my common file data sharing partition, right?

And what you're saying is that I may read files in that common space from Windows, but preferably not write anything from there?

And another thing, what do you mean when you say "if you decide to mount it at all from Ubuntu?" I'm a little new to this, sorry.. heh :)

And also, how can I get rid of the 2 extra swaps?

Thanks a lot. :)

---

### Post by oldfred on 2011-05-10
Your can read & write from the d: or sda2 partition with both windows & Ubuntu, but should only read from the sda1 Vista partition from Ubuntu. Windows will not see the Linux partitions.

You have to use gparted from a liveCD to delete the swap partitions sda5 & sda6. Gparted usually mounts one or more of the swaps to speed things up & that locks the entire extended partition. You have to click on the swap partition and right click swap off. Once you have deleted them can can create one new data partition or move the / (root) partition left. i normally do not like to move partitions left as all data has to be copied and verified, takes a longer time and is slightly more risky. You may have to reinstall grub2's boot loader also, if partition is moved too much.

If your d:/sda2 is not very full you can move it & the left of the extended partition left and add a new /home. But just know whatever you do it will not be what you want in a year or two. My own optimal partitioning plan of two years ago is obsolete.

---

### Post by parthgadhia on 2011-05-10
Thanks a lot. :)

---


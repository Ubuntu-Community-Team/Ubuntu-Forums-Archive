---
title: "I cant run"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by farhadsharif on 2010-06-26
I installed ubuntu 10.04 on my laptop. But when I restart my laptop I cant run it again. 
I mean it cannot run from the hard drive. 
what should I do?

---

### Post by Rubi1200 on 2010-06-26
Hi, 
please provide us with more information. The more you tell us, the better we can help you.

Did you install from a CD or with Wubi?

Is Windows or another OS present on the system?

What are your specifications e.g. RAM, graphics card, HDD etc.?

:-)

---

### Post by farhadsharif on 2010-06-26
Hi. I downloaded an image, then i burn that and install from that CD. when I was installing I set new partitions, so my HDD is formated. and there is no OS on my system,
My laptop is lenovo T500 ATI graphic card, 2 GB RAM and 250 GB HDD. cpu is t9400 (2.53Ghz)

Ill be very happy if my problem solve...
thanks a lot rubi.

---

### Post by Rubi1200 on 2010-06-26
Ok,

if you still have the CD, then boot your computer with it choosing the Try Ubuntu option, follow the instructions here then post back to the forum:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I am sure someone can then help you resolve this.

---

### Post by farhadsharif on 2010-06-26
dear rubi can you email that for me? I cannot download it,

---

### Post by warfacegod on 2010-06-26
You'll need to take the .zip off of the end of the file name.

---

### Post by farhadsharif on 2010-06-26
Thanks a lot, but I steel really dont know what should I do?
you know this is my first day using ubuntu!
and I totally canfused. 
:(

---

### Post by Rubi1200 on 2010-06-26
I will try and make this as easy as possible:

> Boot the LiveCD (the one you installed Ubuntu with). 
When asked, choose to try Ubuntu without installing. That will take you to a LiveCD Desktop. From there you can access the terminal and run the script.

Your computer should boot the CD. If it doesn't, you may have to enter the BIOS and change it so the CD boots before your hard drive. Different computers use different methods to access the BIOS. Usually the user must press one of the Function keys (F1-F12), the DEL key, etc during the boot process to enter the BIOS. courtesy of drs305

You can find the terminal by going to Applications > Accessories > Terminal

The instructions for the script are like this:

> **How to use the boot info script**

  
[LIST]
[*] Boot into any Linux based operating system, LiveCD or LiveUSB with an Internet connection.
[*]  [                                                 Download the Boot Info Script ]("http://sourceforge.net/projects/bootinfoscript")
[*] Open a terminal (Applications>Accessories>Terminal in Gnome) and type sudo bash [path/to/the/download_folder]/boot_info_script*.sh For example if you downloaded the file to the desktop, use sudo bash ~/Desktop/boot_info_script*.sh
[*] If your operation system does not use sudo, use              su 
     bash ~/Desktop/boot_info_script*.sh
[*] You will now have the file RESULTS.txt in the same directory as     the script.[SIZE=-1] But if the script is inside a system directory (like     /usr or /etc) RESULTS.txt will be in the home directory.[/SIZE]
[*] If you already have an existing RESULTS.txt, subsequent  files will be called RESULTS1.txt, RESULTS2.txt,...
[*] Open RESULTS.txt in your favorite text editor.
[*] If you came here from a Linux forum, paste the content of RESULTS.txt into your next post. Make sure to use the appropriate formating. For example in the Ubuntu forums click on the code tags (the symbol #) before pasting RESULTS.txt.
[/LIST]
When you have the RESULTS.txt, post it here on the forum and we will try and help you resolve the problem.

---

### Post by farhadsharif on 2010-06-26
I do the exactly what you said. but the terminal say: No such file or directory.
I copy that file to my desktop, & did the structur but it didnt work. 
I dont know why?

---

### Post by Rubi1200 on 2010-06-27
> **farhadsharif said:**
> I do the exactly what you said. but the terminal say: No such file or directory.
I copy that file to my desktop, & did the structur but it didnt work. 
I dont know why?

Not sure what to tell you, but maybe try again.

If the first command does not work

```
sudo bash ~/Desktop/boot_info_script*.sh
```

then try this

```
su bash ~/Desktop/boot_info_script*.sh
```

---

### Post by cuberts on 2010-06-27
> **warfacegod said:**
> You'll need to take the .zip off of the end of the file name.Actually you can just simply use the ZIP archive to extract the files inside.

---

### Post by farhadsharif on 2010-06-27
now I have the result.txt at home/ubuntu/desktop
what should i do now?

---

### Post by alphacrucis2 on 2010-06-27
> **farhadsharif said:**
> now I have the result.txt at home/ubuntu/desktop
what should i do now?

Double click on the result.txt file on the desktop. That should open the file in gedit. From the Edit menu, click Select All, then Edit Copy. Then paste in your reply here. Highlight all the pasted text by holding down the left mouse button and dragging over all the text. Then click the # button to wrap code tags around the text. Then click Submit Reply.

---

### Post by warfacegod on 2010-06-27
> **cuberts said:**
> Actually you can just simply use the ZIP archive to extract the files inside.

It's not a .zip at all. I added that onto the end because the size limitation was too small for the .sh file. It's cheating, I know and my apologies to any Admins. but this guy needed the file.

---

### Post by farhadsharif on 2010-06-27
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     7,999,487     7,997,440  82 Linux swap / Solaris
/dev/sda2           8,001,534   488,394,751   480,393,218   5 Extended
/dev/sda5           8,001,536   107,999,231    99,997,696  83 Linux
/dev/sda6         108,001,280   488,394,751   380,393,472  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a84df3a6-9d78-4cea-972d-e1cea33de460   swap                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        36b34696-709d-4135-9927-ccd6cea18805   ext4                                     
/dev/sda6        d2484770-fe72-4435-900e-239f2c634aea   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 36b34696-709d-4135-9927-ccd6cea18805
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
search --no-floppy --fs-uuid --set 36b34696-709d-4135-9927-ccd6cea18805
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36b34696-709d-4135-9927-ccd6cea18805
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=36b34696-709d-4135-9927-ccd6cea18805 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36b34696-709d-4135-9927-ccd6cea18805
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=36b34696-709d-4135-9927-ccd6cea18805 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36b34696-709d-4135-9927-ccd6cea18805
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36b34696-709d-4135-9927-ccd6cea18805
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
UUID=36b34696-709d-4135-9927-ccd6cea18805 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=d2484770-fe72-4435-900e-239f2c634aea /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=a84df3a6-9d78-4cea-972d-e1cea33de460 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
  13.0GB: boot/grub/grub.cfg
  12.9GB: boot/initrd.img-2.6.32-21-generic
  13.0GB: boot/vmlinuz-2.6.32-21-generic
  12.9GB: initrd.img
  13.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  f5 a2 ff ff c2 08 00 90  e4 ff ff ff 00 00 00 00  |................|
00000010  cc ff ff ff 00 00 00 00  fe ff ff ff ae a7 e9 6c  |...............l|
00000020  c2 a7 e9 6c 90 90 90 90  90 8b ff 55 8b ec 83 ec  |...l.......U....|
00000030  10 56 57 8d 71 2c 8d 7d  f0 a5 8d 45 1c 50 a5 8d  |.VW.q,.}...E.P..|
00000040  45 f0 50 ff 75 14 a5 ff  75 10 a5 e8 0d 9c fe ff  |E.P.u...u.......|
00000050  8b 4d 24 5f 66 89 01 33  c0 5e c9 c2 20 00 90 90  |.M$_f..3.^.. ...|
00000060  90 90 90 8b ff 55 8b ec  8b 55 0c 53 33 c0 57 bb  |.....U...U.S3.W.|
00000070  ff ff ff 7f 85 d2 74 04  3b d3 76 05 b8 57 00 07  |......t.;.v..W..|
00000080  80 8b 7d 08 85 c0 7c 30  83 65 0c 00 33 c9 56 8b  |..}...|0.e..3.V.|
00000090  f2 8b c7 3b d1 74 0e 66  39 08 74 05 40 40 4e 75  |...;.t.f9.t.@@Nu|
000000a0  f6 3b f1 75 09 c7 45 0c  57 00 07 80 eb 04 8b ca  |.;.u..E.W.......|
000000b0  2b ce 8b 45 0c 5e eb 02  33 c9 85 c0 7c 10 8b 45  |+..E.^..3...|..E|
000000c0  10 53 2b d1 6a 00 8d 0c  4f e8 b3 c4 fd ff 5f 5b  |.S+.j...O....._[|
000000d0  5d c2 0c 00 90 90 90 90  90 8b ff 55 8b ec 33 c0  |]..........U..3.|
000000e0  39 45 0c 74 09 81 7d 0c  ff ff ff 7f 76 05 b8 57  |9E.t..}.....v..W|
000000f0  00 07 80 85 c0 7c 15 8b  45 0c 57 ff 75 14 8b 7d  |.....|..E.W.u..}|
00000100  08 ff 75 10 6a 00 e8 3e  9f fe ff 5f 5d c2 10 00  |..u.j..>..._]...|
00000110  90 90 90 90 90 8b ff 55  8b ec b8 04 10 00 00 e8  |.......U........|
00000120  f7 a1 ff ff a1 1c a1 ea  6c 33 c5 89 45 fc 56 57  |........l3..E.VW|
00000130  8b 7d 08 8d 45 10 50 ff  75 0c be 00 08 00 00 56  |.}..E.P.u......V|
00000140  8d 85 fc ef ff ff 50 e8  8d ff ff ff 68 8c a9 e9  |......P.....h...|
00000150  6c 56 8d 85 fc ef ff ff  50 e8 05 ff ff ff 8d 85  |lV......P.......|
00000160  fc ef ff ff 50 ff 15 18  12 e7 6c 03 c0 50 8d 85  |....P.....l..P..|
00000170  fc ef ff ff 50 8b cf e8  c9 fd ff ff 8b 4d fc 5f  |....P........M._|
00000180  33 cd 5e e8 e4 81 fd ff  c9 c3 90 90 0d 00 0a 00  |3.^.............|
00000190  00 00 90 90 90 90 90 8b  ff 55 8b ec 53 8b 5d 08  |.........U..S.].|
000001a0  56 57 33 ff 8b f1 39 7d  10 74 16 8b c6 2b 45 0c  |VW3...9}.t...+E.|
000001b0  50 68 08 ad e9 6c 53 e8  59 ff ff ff 83 c4 00 12  |Ph...lS.Y.......|
000001c0  61 f2 83 fe ff ff 02 00  00 00 00 d8 f5 05 00 fe  |a...............|
000001d0  ff ff 05 fe ff ff 02 d8  f5 05 00 60 ac 16 00 00  |...........`....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by farhadsharif on 2010-06-27
is it like this?
did I do it right?

---

### Post by warfacegod on 2010-06-27
> **farhadsharif said:**
> is it like this?
did I do it right?

Yes. But do us a favor. Click Edit on that post> click Advanced> highlight that> and click the # icon. That will put code brackets on the content and make it much easier to read.

---

### Post by Rubi1200 on 2010-06-27
Great that you managed to get this to us!

You need to highlight the text and then use the code tags like this```
 your text
```I hope that one of the experts will come along soon and give you advice regarding how to resolve this issue.

Good luck!

forget this post; just saw the previous one

---

### Post by farhadsharif on 2010-06-27
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     7,999,487     7,997,440  82 Linux swap / Solaris
/dev/sda2           8,001,534   488,394,751   480,393,218   5 Extended
/dev/sda5           8,001,536   107,999,231    99,997,696  83 Linux
/dev/sda6         108,001,280   488,394,751   380,393,472  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a84df3a6-9d78-4cea-972d-e1cea33de460   swap                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        36b34696-709d-4135-9927-ccd6cea18805   ext4                                     
/dev/sda6        d2484770-fe72-4435-900e-239f2c634aea   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 36b34696-709d-4135-9927-ccd6cea18805
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
search --no-floppy --fs-uuid --set 36b34696-709d-4135-9927-ccd6cea18805
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36b34696-709d-4135-9927-ccd6cea18805
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=36b34696-709d-4135-9927-ccd6cea18805 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36b34696-709d-4135-9927-ccd6cea18805
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=36b34696-709d-4135-9927-ccd6cea18805 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36b34696-709d-4135-9927-ccd6cea18805
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36b34696-709d-4135-9927-ccd6cea18805
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
UUID=36b34696-709d-4135-9927-ccd6cea18805 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=d2484770-fe72-4435-900e-239f2c634aea /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=a84df3a6-9d78-4cea-972d-e1cea33de460 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
  13.0GB: boot/grub/grub.cfg
  12.9GB: boot/initrd.img-2.6.32-21-generic
  13.0GB: boot/vmlinuz-2.6.32-21-generic
  12.9GB: initrd.img
  13.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  f5 a2 ff ff c2 08 00 90  e4 ff ff ff 00 00 00 00  |................|
00000010  cc ff ff ff 00 00 00 00  fe ff ff ff ae a7 e9 6c  |...............l|
00000020  c2 a7 e9 6c 90 90 90 90  90 8b ff 55 8b ec 83 ec  |...l.......U....|
00000030  10 56 57 8d 71 2c 8d 7d  f0 a5 8d 45 1c 50 a5 8d  |.VW.q,.}...E.P..|
00000040  45 f0 50 ff 75 14 a5 ff  75 10 a5 e8 0d 9c fe ff  |E.P.u...u.......|
00000050  8b 4d 24 5f 66 89 01 33  c0 5e c9 c2 20 00 90 90  |.M$_f..3.^.. ...|
00000060  90 90 90 8b ff 55 8b ec  8b 55 0c 53 33 c0 57 bb  |.....U...U.S3.W.|
00000070  ff ff ff 7f 85 d2 74 04  3b d3 76 05 b8 57 00 07  |......t.;.v..W..|
00000080  80 8b 7d 08 85 c0 7c 30  83 65 0c 00 33 c9 56 8b  |..}...|0.e..3.V.|
00000090  f2 8b c7 3b d1 74 0e 66  39 08 74 05 40 40 4e 75  |...;.t.f9.t.@@Nu|
000000a0  f6 3b f1 75 09 c7 45 0c  57 00 07 80 eb 04 8b ca  |.;.u..E.W.......|
000000b0  2b ce 8b 45 0c 5e eb 02  33 c9 85 c0 7c 10 8b 45  |+..E.^..3...|..E|
000000c0  10 53 2b d1 6a 00 8d 0c  4f e8 b3 c4 fd ff 5f 5b  |.S+.j...O....._[|
000000d0  5d c2 0c 00 90 90 90 90  90 8b ff 55 8b ec 33 c0  |]..........U..3.|
000000e0  39 45 0c 74 09 81 7d 0c  ff ff ff 7f 76 05 b8 57  |9E.t..}.....v..W|
000000f0  00 07 80 85 c0 7c 15 8b  45 0c 57 ff 75 14 8b 7d  |.....|..E.W.u..}|
00000100  08 ff 75 10 6a 00 e8 3e  9f fe ff 5f 5d c2 10 00  |..u.j..>..._]...|
00000110  90 90 90 90 90 8b ff 55  8b ec b8 04 10 00 00 e8  |.......U........|
00000120  f7 a1 ff ff a1 1c a1 ea  6c 33 c5 89 45 fc 56 57  |........l3..E.VW|
00000130  8b 7d 08 8d 45 10 50 ff  75 0c be 00 08 00 00 56  |.}..E.P.u......V|
00000140  8d 85 fc ef ff ff 50 e8  8d ff ff ff 68 8c a9 e9  |......P.....h...|
00000150  6c 56 8d 85 fc ef ff ff  50 e8 05 ff ff ff 8d 85  |lV......P.......|
00000160  fc ef ff ff 50 ff 15 18  12 e7 6c 03 c0 50 8d 85  |....P.....l..P..|
00000170  fc ef ff ff 50 8b cf e8  c9 fd ff ff 8b 4d fc 5f  |....P........M._|
00000180  33 cd 5e e8 e4 81 fd ff  c9 c3 90 90 0d 00 0a 00  |3.^.............|
00000190  00 00 90 90 90 90 90 8b  ff 55 8b ec 53 8b 5d 08  |.........U..S.].|
000001a0  56 57 33 ff 8b f1 39 7d  10 74 16 8b c6 2b 45 0c  |VW3...9}.t...+E.|
000001b0  50 68 08 ad e9 6c 53 e8  59 ff ff ff 83 c4 00 12  |Ph...lS.Y.......|
000001c0  61 f2 83 fe ff ff 02 00  00 00 00 d8 f5 05 00 fe  |a...............|
000001d0  ff ff 05 fe ff ff 02 d8  f5 05 00 60 ac 16 00 00  |...........`....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by farhadsharif on 2010-06-27
Thanks a lot dear Rubi, I hope my problem will solve soon.

---


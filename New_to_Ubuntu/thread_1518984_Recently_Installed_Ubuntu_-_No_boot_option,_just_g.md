---
title: "Recently Installed Ubuntu - No boot option, just goes straight to ubuntu."
date: 2010-06-27
forum: New to Ubuntu
---

### Post by Jaydamis on 2010-06-27
Howdy - 

I recently installed Lucid and I have no option to choose what I want to boot. I had windows 7 installed, but like I said, no option to go to it.  Last time I tried a linux distro (ubuntu 8.04) I did not have this issue...

Any advice appreciated... thanks in advance!

---

### Post by takisan on 2010-06-27
GRUB, well, you might have wiped it (7) off of the HD, so it's probibly lost. If you're sure it's there, run update-grub to update grub and see if it finds 7 on the HD. Personally, I'd welcome an all-ubuntu installation, because Ubuntu can run Windows Programs (see [http://www.winehq.org/](http://www.winehq.org/))

---

### Post by oldfred on 2010-06-27
Welcome to the forums.

If ubuntu only sees one operating system it does not show a menu. You have to hold down the shift key from BIOS until menu appears.

If per takisan's this does not find the win install:
sudo update-grub

then run this to show everything related to booting about your system:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by Jaydamis on 2010-06-27
> **takisan said:**
> GRUB, well, you might have wiped it (7) off of the HD, so it's probibly lost. If you're sure it's there, run update-grub to update grub and see if it finds 7 on the HD. Personally, I'd welcome an all-ubuntu installation, because Ubuntu can run Windows Programs (see [http://www.winehq.org/](http://www.winehq.org/))

It's definitely still there - I can look into the windows filesystem at least... Maybe once I am very comfortable w/ ubuntu I will go the all-ubuntu route. I've used wine to run a few things, but right now its so damn easy to stay with windows since, when I run into problems I'm not well versed enough in linux systems to fix problems on my own (I got a few books I'm reading tho! This is kinda my new hobby... )

> **oldfred said:**
> If per takisan's this does not find the win install:
sudo update-grub

This is my output from sudo update-grub:

Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

So it looks like it doesn't see 7 - right?

Here is the bootinfo output :

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,046   402,343,935   402,341,890   5 Extended
/dev/sda5               2,048   390,625,279   390,623,232  83 Linux
/dev/sda6         390,627,328   402,343,935    11,716,608  82 Linux swap / Solaris
/dev/sda2         819,204,096 1,953,521,663 1,134,317,568   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        365E19B05E196A3F                       ntfs                                     
/dev/sda5        24a66a1e-1f5f-4936-9c89-5b9455b4b8ce   ext4                                     
/dev/sda6        5dd20f45-fed8-4a06-8822-76da19d272dd   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 24a66a1e-1f5f-4936-9c89-5b9455b4b8ce
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
search --no-floppy --fs-uuid --set 24a66a1e-1f5f-4936-9c89-5b9455b4b8ce
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 24a66a1e-1f5f-4936-9c89-5b9455b4b8ce
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=24a66a1e-1f5f-4936-9c89-5b9455b4b8ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 24a66a1e-1f5f-4936-9c89-5b9455b4b8ce
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=24a66a1e-1f5f-4936-9c89-5b9455b4b8ce ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 24a66a1e-1f5f-4936-9c89-5b9455b4b8ce
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=24a66a1e-1f5f-4936-9c89-5b9455b4b8ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 24a66a1e-1f5f-4936-9c89-5b9455b4b8ce
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=24a66a1e-1f5f-4936-9c89-5b9455b4b8ce ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 24a66a1e-1f5f-4936-9c89-5b9455b4b8ce
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 24a66a1e-1f5f-4936-9c89-5b9455b4b8ce
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
UUID=24a66a1e-1f5f-4936-9c89-5b9455b4b8ce /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5dd20f45-fed8-4a06-8822-76da19d272dd none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 176.2GB: boot/grub/core.img
 176.2GB: boot/grub/grub.cfg
 176.2GB: boot/initrd.img-2.6.32-21-generic
 176.2GB: boot/initrd.img-2.6.32-22-generic
 176.2GB: boot/vmlinuz-2.6.32-21-generic
    .5GB: boot/vmlinuz-2.6.32-22-generic
 176.2GB: initrd.img
 176.2GB: initrd.img.old
    .5GB: vmlinuz
 176.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  02 f1 a0 40 80 00 07 30  00 f9 4d ae 37 ff 4d fa  |...@...0..M.7.M.|
00000010  4d 73 0d 0c f2 4d f8 30  0f 03 f1 03 b1 0d 55 70  |Ms...M.0......Up|
00000020  70 65 72 46 5c 69 6c b0  59 12 34 f3 32 05 f2 99  |perF\il.Y.4.2...|
00000030  f0 5e 0a f7 36 e2 41 30  07 f1 20 44 70 0e 73 d4  |.^..6.A0.. Dp.s.|
00000040  00 6b 50 90 72 90 00 76  b0 0e f3 28 82 2d 72 8c  |.kP.r..v...(.-r.|
00000050  00 00 c8 9b 0e 72 35 f3  71 51 71 ac 30 0b 73 04  |.....r5.qQq.0.s.|
00000060  e0 03 72 56 f5 03 9e 20  72 a2 b3 93 e4 3b 74 36  |..rV... r....;t6|
00000070  0b 00 31 0e be 78 74 03  71 0a f9 51 71 04 71 ad  |..1..xt.q..Qq.q.|
00000080  53 b0 27 5b 11 16 f5 ab  2e 10 09 75 ad 69 d0 17  |S.'[.......u.i..|
00000090  6b 7d 70 38 6c b0 3d 91  18 7f 51 51 04 73 2c 64  |k}p8l.=...QQ.s,d|
000000a0  a5 f4 0c 2e 70 00 6e 00  11 40 0e 74 08 03 73 7c  |....p.n..@.t..s||
000000b0  f7 52 00 00 53 69 6c 65  3c 6e 74 d4 08 20 04 73  |.R..Sile<nt.. .s|
000000c0  15 7d 55 00 00 ab 7b 55  f5 65 07 f2 17 c0 76 0d  |.}U...{U.e....v.|
000000d0  0c 76 48 d1 73 04 10 00  3c 30 05 70 70 1f 31 0f  |.vH.s...<0.pp.1.|
000000e0  01 31 00 54 72 6f 75 62  6c 65 10 53 68 6f 6f 20  |.1.Trouble.Shoo |
000000f0  1a 2d 30 c0 05 70 27 68  b0 2d 70 00 3a 00 2f 45  |.-0..p'h.-p.:./E|
00000100  10 00 68 d0 17 6c 00 70  90 00 74 55 10 0f 68 10  |..h..l.p..tU..h.|
00000110  6a 6f 50 11 2f 30 00 73  d1 d8 15 2e 00 68 10 01  |joP./0.s.....h..|
00000120  6d b0 05 f3 1d 5d 73 5c  08 f9 15 74 5c 71 08 a8  |m....]s\...t\q..|
00000130  70 1f d0 55 30 00 18 f0  01 50 30 00 d8 30 00 00  |p..U0....P0..0..|
00000140  b5 30 09 48 30 00 b0 30  00 60 04 00 f5 5e 90 ce  |.0.H0..0.`...^..|
00000150  b0 e8 64 75 2c f8 30 55  cb a7 33 79 a0 0a 72 cd  |..du,.0U..3y..r.|
00000160  38 36 ff 5e 36 40 04 1e  70 81 04 30 00 f9 5e 71  |86.^6@..p..0..^q|
00000170  2f d1 97 2b a2 a7 f5 05  f4 11 b0 76 32 30 30 09  |/..+.......v200.|
00000180  e7 24 03 32 d2 f5 05 58  0f ff 05 71 32 b1 ae bf  |.$.2...X...q2...|
00000190  f1 02 f9 05 f1 0f f5 1e  df c9 f5 46 0d 72 4c 8c  |...........F.rL.|
000001a0  f8 0d f7 2f 77 5e 45 78  74 40 05 c1 71 66 2e 00  |.../w^Ext@..qf..|
000001b0  4e 00 54 01 06 30 00 f3  f3 1b f3 5c 30 0e 00 20  |N.T..0.....\0.. |
000001c0  21 00 83 fe ff ff 02 00  00 00 00 70 48 17 00 fe  |!..........pH...|
000001d0  ff ff 05 fe ff ff 02 70  48 17 00 d0 b2 00 00 00  |.......pH.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

Once again I really appreciate the help! Hope to learn a bit from this :D

-Jay

---

### Post by Jaydamis on 2010-06-27
Just an update, this is now in my /etc/grub.d folder as 11_Windows7...

#! /bin/sh -e
echo &#8220;Adding Windows&#8221; >&2
cat << EOF
menuentry &#8220;Windows 7&#8243; {
set root=(hd0,2)
chainloader +1
}
EOF

hd0,2 b/c i see it is sda2, right. Am I getting warmer? I ran update-grub as well as what is found here:


Edited 40_custom to include:
# (2) Windows XP
menuentry "Windows XP" {
set root=(hd0,2)
chainloader +1"
} And followed directions below.
"
**  Using grub-mkconfig **

 The best way to add other entries is editing the [COLOR=#005500][FONT=monospace]/etc/grub.d/40_custom[/FONT][/COLOR]. The entries in this file will be  automatically added when running **grub-mkconfig**. After adding the new lines, run  
 # grub-mkconfig -o /boot/grub/grub.cfg 
to generate an updated [COLOR=#005500][FONT=monospace]grub.cfg[/FONT][/COLOR]. 
 **  With GNU/Linux **

 Assuming that the other distro is on partition [COLOR=#005500][FONT=monospace]sda2[/FONT][/COLOR]: 
 menuentry "Other Linux" {
set root=(hd0,2)
linux /boot/vmlinuz (add other options here as required)
initrd /boot/initrd.img (if the other kernel uses/needs one)
}
**  With Windows **

 This assumes that your Windows partition is [COLOR=#005500][FONT=monospace]sda3[/FONT][/COLOR]. 
 # (2) Windows XP
menuentry "Windows XP" {
set root=(hd0,3)
chainloader +1"
}

"

No luck so far...

---

### Post by Dustin2128 on 2010-06-27
An option you may consider (If you've got the install disks and absolutely must have windows) is installing windows to a virtual machine and copying what files you have left from your windows partition onto the virtual hard drive. Works quite well as long as there's no gaming involved, and when there is gaming involved you can usually tweak wine to work with most mainstream games.

---

### Post by sandyd on 2010-06-27
tri this.
```

gksudo gedit /etc/grub.d/40_custom

```
add this
```

menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid
    chainloader +1
}

```
save and run
```

sudo update-grub
```

---

### Post by Jaydamis on 2010-06-27
Carlee - Just followed your advice, got this as output:

Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

So I'm assuming it did not work... I'll try a restart (boo hoo 15 seconds from my life on ubuntu :D ) to make sure.

Thanks for the help

---

### Post by oldfred on 2010-06-27
Your windows is missing these files.

/bootmgr /Boot/BCD 

These files are often in a hidden system/recovery partition that was sda1 which was the boot partition as it still has the boot flag. You converted sda1 to the extended partition and overwrote the system partition.  You should be able to repair it.

You need to move the boot flag to sda2 or windows will not find the partition to repair it. You can use gparted or disk utility or :

set boot flag on for sda2 (off for others)
sudo sfdisk -A2 /dev/sda

Then you need to uses your windows CD to repair the windows install and it should reinstall bootmgr and create a new BCD.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

If you install the windows boot loader to the MBR you will have to reinstall grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by Jaydamis on 2010-06-27
Oldfred - Thank you, I need to go pick up the seven installer from my friend's place (I left my CD in my apt, and I'm home for the summer) and I'lll let you know how it goes. Would you suggest going the reinstalling grub route, or just skipping the update of the MBR?

---

### Post by sandyd on 2010-06-27
> **Jaydamis said:**
> Carlee - Just followed your advice, got this as output:

Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

So I'm assuming it did not work... I'll try a restart (boo hoo 15 seconds from my life on ubuntu :D ) to make sure.

Thanks for the help
It shouldn;t show up on that list, it should only show up on your boot menu

---

### Post by Jaydamis on 2010-06-27
> **carlee said:**
> It shouldn;t show up on that list, it should only show up on your boot menu

Ah well, still don't have the boot menu, but I'll be trying what oldfred suggested soon, so hopefully that works!

---

### Post by oldfred on 2010-06-27
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by sandyd on 2010-06-28
> **Jaydamis said:**
> Ah well, still don't have the boot menu, but I'll be trying what oldfred suggested soon, so hopefully that works!
oops. try running
```

sudo chmod +x /etc/grub.d/40_custom
```

---

### Post by Jaydamis on 2010-06-29
> **Dustin2128 said:**
> An option you may consider (If you've got the install disks and absolutely must have windows) is installing windows to a virtual machine and copying what files you have left from your windows partition onto the virtual hard drive. Works quite well as long as there's no gaming involved, and when there is gaming involved you can usually tweak wine to work with most mainstream games.

Wow I completely missed your post the other day... unfortunately, gaming is the only reason I want to keep windows. Wine is working ok for a few of my steam games w/o any tweaking so I'm a little happy at least.

---

### Post by Jaydamis on 2010-06-29
@ Carlee - still a no go :(

@ oldfred
> **oldfred said:**
> If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

I know I'm full of problems and quirks, but I'm waiting on my friend to get back in town so i can swipe his usb w/ 7 on it (Sadly, I'm out of CDs lol :/ ), but is there a way to make a bootable drive with the windows 7 repair isos? If not I'll just have to wait.

Thank you guys again for all your help! I've been playing around the last few days and now I got a really pretty desktop env and I'm rather happy :D

---

### Post by wilee-nilee on 2010-06-29
> **Jaydamis said:**
> Wow I completely missed your post the other day... unfortunately, gaming is the only reason I want to keep windows. Wine is working ok for a few of my steam games w/o any tweaking so I'm a little happy at least.

Follow oldfreds advice if you want the dual boot still, the missing boot files need to be installed.

/bootmgr /Boot/BCD

---

### Post by Jaydamis on 2010-06-29
> **Jaydamis said:**
> @ Carlee - still a no go :(

@ oldfred


I know I'm full of problems and quirks, but I'm waiting on my friend to get back in town so i can swipe his usb w/ 7 on it (Sadly, I'm out of CDs lol :/ ), but is there a way to make a bootable drive with the windows 7 repair isos? If not I'll just have to wait.

Thank you guys again for all your help! I've been playing around the last few days and now I got a really pretty desktop env and I'm rather happy :D

Eh that sounded retarded. What I meant to ask was can I make a bootable windows repair USB from ubuntu, or do I need windows to do that extra step of making it bootable?

---

### Post by Jaydamis on 2010-07-08
I finally got around to trying the fix. I used the advice found Oldfred's post (post #9), at first without using the /fixmbr (no luck) and then using the /fixmbr. I'll get grub back on as soon as I find a spare minute.

Thank you all for the help, I greatly appreciate the speed and quality of service :D

-Jay

---


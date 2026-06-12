---
title: "&quot;GRUB- error: no such partition&quot; after installing Ubuntu"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by Odexios on 2011-07-30
Hello everyone!

I have Windows 7 installed on my laptop, and I've installed this afternoon Ubuntu 11.04 on an empty partition I saved for it. I'm not an expert, but I installed Ubuntu on, well, almost all my friends' PCs without ever having any issue. This time, after the installation, I rebooted the system and I found a black screen with the error "GRUB-error: no such partition", and a grub rescue prompt.

I thought something went wrong with the installation, and considering I had just installed the OS, I took the (seemingly) easy way and formatted the partition and then reinstalled the system.

Well, as you can imagine, nothing had changed. I searched the forums and found a guide to restore GRUB ( [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) ); I followed it, no command gave me an error, but everything is still the same.

Can anyone help figure out what went wrong, and how can I solve it? Apparently my last resort solution, formatting, isn't working this time XD

---

### Post by amjjawad on 2011-07-30
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GRUB-+error%3A+no+such+partition%22+after+installing+Ubuntu&as_qdr=all&sa=Google+Search&lang=en#1267](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GRUB-+error%3A+no+such+partition%22+after+installing+Ubuntu&as_qdr=all&sa=Google+Search&lang=en#1267)

---

### Post by Odexios on 2011-07-30
> **amjjawad said:**
> [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GRUB-+error%3A+no+such+partition%22+after+installing+Ubuntu&as_qdr=all&sa=Google+Search&lang=en#1267](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GRUB-+error%3A+no+such+partition%22+after+installing+Ubuntu&as_qdr=all&sa=Google+Search&lang=en#1267)
So?

>  Well, as you can imagine, nothing had changed. I searched the forums and found a guide to restore GRUB ( [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) ); I followed it, no command gave me an error, but everything is still the same.

As I said, I already searched, but what I found didn't help me.

---

### Post by amjjawad on 2011-07-30
How did you install Ubuntu?

What is the specifications of your machine?

Are you sure you have searched for everything? there is no harm to have a look at the link I provided to you. You need to do something by yourself too, right? ;)

Have a look at this and see if that applies to your case:
[https://help.ubuntu.com/community/Grub2#error:%20no%20such%20partition](https://help.ubuntu.com/community/Grub2#error:%20no%20such%20partition)

---

### Post by drs305 on 2011-07-30
Odexios,

Boot the Ubuntu LiveCD.

Please post the contents of RESULTS.txt, which you can download/extract/run from the following site:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

The RESULTS.txt file will show us the status of your boot files and OS.

---

### Post by Odexios on 2011-07-30
> **amjjawad said:**
> How did you install Ubuntu?

Are you sure you have searched for everything? there is no harm to have a look at the link I provided to you. You need to do something by yourself too, right? ;)Sorry if the "So?" sounded too harsh, I just meant to say that I already had searched, but I didn't find anything.

Anyway, you're right. I didn't provide almost any information.

I installed ubuntu the first time via a Live CD, the second time using a USB stick. I had the same results.

> Have a look at this and see if that applies to your case:
[https://help.ubuntu.com/community/Grub2#error:%20no%20such%20partition](https://help.ubuntu.com/community/Grub2#error:%20no%20such%20partition)Already seen; the BIOS recognizes the full hard-disk size, so I assumed the solution provided wouldn't do anything. Was that a wrong assumption?

> **drs305 said:**
> Odexios,

Boot the Ubuntu LiveCD.

Please post the contents of RESULTS.txt, which you can download/extract/run from the following site:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net/")

The RESULTS.txt file will show us the status of your boot files and OS.Yep, sorry, I saw everyone else did it, but I completely forgot to do it by the time I was writing the opening post. I'm posting the output in a minute.

---

### Post by Odexios on 2011-07-30
Here it is:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   307,701,759   307,494,912   7 NTFS / exFAT / HPFS
/dev/sda3         307,703,806   625,141,759   317,437,954   5 Extended
/dev/sda5         307,703,808   315,514,879     7,811,072  82 Linux swap / Solaris
/dev/sda6         315,516,928   625,141,759   309,624,832  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        88DC98D2DC98BC3E                       ntfs       Riservato per il sistema
/dev/sda2        52D8AA96D8AA77BD                       ntfs       
/dev/sda5        c615589c-16c2-4e92-a2eb-a9fcd55a1be4   swap       
/dev/sda6        bfe2a463-e2fd-4e2f-bcb8-7ffd3951d9d2   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root bfe2a463-e2fd-4e2f-bcb8-7ffd3951d9d2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root bfe2a463-e2fd-4e2f-bcb8-7ffd3951d9d2
set locale_dir=($root)/boot/grub/locale
set lang=it_IT
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
menuentry 'Ubuntu, con Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bfe2a463-e2fd-4e2f-bcb8-7ffd3951d9d2
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bfe2a463-e2fd-4e2f-bcb8-7ffd3951d9d2 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, con Linux 2.6.38-8-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bfe2a463-e2fd-4e2f-bcb8-7ffd3951d9d2
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bfe2a463-e2fd-4e2f-bcb8-7ffd3951d9d2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bfe2a463-e2fd-4e2f-bcb8-7ffd3951d9d2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root bfe2a463-e2fd-4e2f-bcb8-7ffd3951d9d2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 88DC98D2DC98BC3E
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 234.583511353 = 251.882127360  boot/grub/core.img                             1
 184.612106323 = 198.225739776  boot/grub/grub.cfg                             1
 151.528320312 = 162.702295040  boot/initrd.img-2.6.38-8-generic               2
 234.582500458 = 251.881041920  boot/vmlinuz-2.6.38-8-generic                  1
 151.528320312 = 162.702295040  initrd.img                                     2
 234.582500458 = 251.881041920  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  24 11 16 53 c6 7a ce 15  65 c2 34 a6 5f 57 cd ac  |$..S.z..e.4._W..|
00000010  7e 91 f9 5b 48 5e 00 07  ff fb 64 04 e6 8c c1 94  |~..[H^....d.....|
00000020  1c d3 93 03 2a 50 31 e2  fa 61 61 26 38 86 78 8f  |....*P1..aa&8.x.|
00000030  52 67 8c 49 48 cc 8c 29  89 83 0c e1 31 50 4f 53  |Rg.IH..)....1POS|
00000040  eb 23 86 11 d5 ce b1 90  b8 af 41 85 1d 81 51 45  |.#........A...QE|
00000050  fc 0a ae 42 1a 53 dd ef  22 08 bb 33 66 1a 44 02  |...B.S.."..3f.D.|
00000060  0a 8c 11 01 9c 71 df 70  0d b6 8a 0f 07 21 87 20  |.....q.p.....!. |
00000070  e9 22 db 36 aa 50 9a 2a  d6 c3 e3 44 44 b6 29 01  |.".6.P.*...DD.).|
00000080  ca 0b 75 7d 2d a8 83 26  4a 5c 37 49 96 61 84 99  |..u}-..&J\7I.a..|
00000090  07 a5 e1 34 ad 4e 04 95  c7 f4 0a f5 74 0f 07 00  |...4.N......t...|
000000a0  60 eb 5a eb a5 00 38 89  da d0 ad 5f 00 20 03 10  |`.Z...8...._. ..|
000000b0  81 88 a5 ae 9b 3b be 46  47 62 f3 3d ec 8e 61 2f  |.....;.FGb.=..a/|
000000c0  f7 ca b1 e2 c1 c0 21 e6  50 92 7c 34 59 f7 ea 10  |......!.P.|4Y...|
000000d0  04 79 c9 7f c0 02 6e 48  4f c6 b8 6e 09 f7 64 71  |.y....nHO..n..dq|
000000e0  b3 67 76 76 eb 4b d3 83  03 72 f0 55 13 18 29 83  |.gvv.K...r.U..).|
000000f0  ad f8 ba 5d 7a ce bd 36  4e 94 f5 b5 c1 54 5d be  |...]z..6N....T].|
00000100  3e 3d 8c e5 67 ac 82 1e  30 30 64 63 45 03 00 00  |>=..g...00dcE...|
00000110  00 00 01 b6 98 4f c1 09  fb a0 6c 6f 11 44 7a 79  |.....O....lo.Dzy|
00000120  a6 2c 44 64 1e 1e e6 e2  c3 1d d6 26 eb 53 70 08  |.,Dd.......&.Sp.|
00000130  ac 19 70 66 0e 0f c3 b5  d5 0c fc d1 a0 60 6a 88  |..pf.........`j.|
00000140  c1 41 9c 47 12 19 5c 26  2a d7 8d a1 b2 03 10 a4  |.A.G..\&*.......|
00000150  ea 4c b9 30 0b 94 69 a1  70 9d 77 8d dc dd 5e 27  |.L.0..i.p.w...^'|
00000160  d4 c7 33 ad 49 d4 1a fb  3e b2 01 50 68 79 74 b5  |..3.I...>..Phyt.|
00000170  a2 67 7f fd 9f fc 44 64  6d a4 4f 42 d4 74 70 44  |.g....Ddm.OB.tpD|
00000180  60 e9 ba 44 0d 0d ec a3  ec 22 47 47 5e 42 2b e0  |`..D....."GG^B+.|
00000190  44 f7 5f e6 0c fe db ff  73 28 5b 84 86 47 8c e8  |D._.....s([..G..|
000001a0  3c fc 00 a3 14 74 74 70  60 77 fd b6 e4 89 bd 14  |<....ttp`w......|
000001b0  7a 01 48 61 1c 14 1c d4  c0 88 6d 79 0a 0f 00 ef  |z.Ha......my....|
000001c0  ff ff 82 ef ff ff 02 00  00 00 00 30 77 00 00 ef  |...........0w...|
000001d0  ff ff 05 ef ff ff 02 30  77 00 00 88 74 12 00 00  |.......0w...t...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

Let me know if I didn't post it correctly.

---

### Post by drs305 on 2011-07-30
Would you try rebooting and enter the BIOS setup during boot and check the reported disk size? See if it reports the drive size as approximately 137GB.

Your Grub2 files look fairly normal. The rescue prompt indicates that Grub can't find the files it needs to boot.

The only thing I note is that all the files are well into the drive. If the BIOS is limited to seeing the first 137GB you won't be able to boot the Ubuntu files without taking some further steps. I won't expound unless you find the BIOS is restricted.

---

### Post by Odexios on 2011-07-30
> **drs305 said:**
> Would you try rebooting and enter the BIOS setup during boot and check the reported disk size? See if it reports the drive size as approximately 137GB.

Your Grub2 files look fairly normal. The only thing I note is that all the files are well into the drive. If the BIOS is limited to seeing the first 137GB you won't be able to boot the Ubuntu files without taking some further steps. I won't expound unless you find the BIOS is restricted.Yep, already checked; it sees all the 300 GB of the hard disk.

---

### Post by drs305 on 2011-07-30
> **Odexios said:**
> Yep, already checked; it sees all the 300 GB of the hard disk.

I often forget this since it is fairly new, but I'd recommend you try the Boot Repair tool. Here is the link for that app:
[http://ubuntuforums.org/showthread.php?t=1769482#post10976174]("http://ubuntuforums.org/showthread.php?t=1769482#post10976174")


If that doesn't work and you installed this from a CD (not a removable USB device), I would next recommend purging and reinstalling Grub from the LiveCD. You would mount /dev/sda6, then 'chroot' into it. Confirm you have a working Internet connection, then completely remove Grub 2 and reinstall it. It does the same thing as the Boot Repair Tool, just from the command line. The instructions are located in the "Chroot" link in my signature line.

---


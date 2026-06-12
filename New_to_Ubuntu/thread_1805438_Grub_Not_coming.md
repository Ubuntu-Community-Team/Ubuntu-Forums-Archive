---
title: "Grub Not coming"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by vivek.purushoth on 2011-07-16
hello . Thanks in Advance . 

I had Triple-Boot Windows XP , Windows 7 and Ubuntu in my System.
In the Beginning i had chosen while installing Ubuntu i had chosen install 
inside Windows option . But now i wanted to dedicate a whole new drive for Linux .
 So i thought of getting rid of XP and installing Kubuntu in that drive .
 Now the problem is as soon as the computer switches on i won't get the Grub .
 Directly Kubuntu boots . I would be very glad if someone is able to help me out .
 I want to retain Windows 7 as well as be able to use Kubuntu.

---

### Post by Elfy on 2011-07-16
First let's see if windows is on the grub menu - open a terminal and run 

```
cat /boot/grub/grub.cfg |grep menuentry
```

If windows is on the list we need to unhide the menu.

If windows is not on the list run 

```
sudo update-grub
```

---

### Post by vivek.purushoth on 2011-07-16
@forestpiskie - thanks a lot for trying to help me

->When i tried the first code 
cat /boot/grub/grub.cfg |grep menuentry

i got this

menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {


I didn't understand what exactly it was . And i tried the 2nd code 
sudo update-grub
and still after restart i don't get the Grub Menu. Directly Kubuntu Boots
I am sorry i am still a beginner with Kubuntu . So i would be very glad if you could help me step - by- step.

---

### Post by amjjawad on 2011-07-16
> **vivek.purushoth said:**
> and still after restart i don't get the Grub Menu. Directly Kubuntu Boots

Did you install Kubuntu or you are trying to install it?

From what I can understand from your post is you are trying to boot from Kubuntu LiveCD/USB and you did not install it yet.

Could you please explain that?

---

### Post by vivek.purushoth on 2011-07-16
@amjjawad - Ok i'll explain what has happened.

First i had only Xp in my system (C drive).
Later i installed Windows 7 (D drive).
Later i installed Ubuntu inside Windows 7 . 
But i no longer needed XP so i thought of getting rid of it so i did install KUBUNTU
on the same drive where XP was there before . I didn't just boot from live cd . I did install Kubuntu properly on the same drive .

---

### Post by Elfy on 2011-07-16
Hi - ok so we can see from the first that windows is not on the list.

If you run ```
cat /boot/grub/grub.cfg |grep menuentry
``` now is windows mentioned? 

If it's _not_ please go to this link and follow the instructions please. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

@amjjawad - it's installed ;)

---

### Post by vivek.purushoth on 2011-07-16
And i think all the boot setting was present in C drive which i have formatted before installing Kubuntu . Now only Kubuntu is booting Directly (I have removed CD from CD-ROM) . I am not able to select Windows 7 or Ubuntu which was installed inside windows7 . Is there anyway i can get the grub menu something like this now 

Windows 7
Kubuntu

or something like that?

---

### Post by Elfy on 2011-07-16
> **vivek.purushoth said:**
> I didn't understand what exactly it was . And i tried the 2nd code 
sudo update-grub
and still after restart i don't get the Grub Menu. Directly Kubuntu Boots
I am sorry i am still a beginner with Kubuntu . So i would be very glad if you could help me step - by- step.

Basically the first command looked at the grub menu and told us what it saw - no Windows as you know.

The second command does as it says and updates grub.

The script in the link I just gave will give us a lot of information to look at about the system.

---

### Post by amjjawad on 2011-07-16
> **forestpiskie said:**
> @amjjawad - it's installed ;)

Then it's different story :)

Thank you!

---

### Post by vivek.purushoth on 2011-07-16
forestpiskie . 
I tried to run that boot_info_script.sh .
But it says cannot execute binary file

---

### Post by amjjawad on 2011-07-16
> **vivek.purushoth said:**
> forestpiskie . 
I tried to run that boot_info_script.sh .
But it says cannot execute binary file

Please read the instructions in [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) carefully and you'll make it :)

---

### Post by vivek.purushoth on 2011-07-16
@amjjawad - thanks
[ATTACH]197615[/ATTACH]
This is My results.txt file .

---

### Post by amjjawad on 2011-07-16
> **vivek.purushoth said:**
> @amjjawad - thanks
[ATTACH]197615[/ATTACH]
This is My results.txt file .

This is very hard to read :(

Please, copy and paste it here and put CODE tags at the beginning and at the end.

---

### Post by vivek.purushoth on 2011-07-16
@amjjawad
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 17058311 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for ?? on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    97,656,312    97,656,250  83 Linux
/dev/sda2          97,656,830   976,751,999   879,095,170   f W95 Extended (LBA)
/dev/sda5         162,786,708   325,573,289   162,786,582   7 NTFS / exFAT / HPFS
/dev/sda6         325,573,353   488,359,934   162,786,582   7 NTFS / exFAT / HPFS
/dev/sda7         488,359,998   651,146,579   162,786,582   7 NTFS / exFAT / HPFS
/dev/sda8         651,146,643   813,933,224   162,786,582   7 NTFS / exFAT / HPFS
/dev/sda9         813,933,288   976,751,999   162,818,712   7 NTFS / exFAT / HPFS
/dev/sda10         97,656,832   101,875,711     4,218,880  82 Linux swap / Solaris
/dev/sda11        101,877,760   162,785,279    60,907,520  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        a08cc4ab-5c89-4202-aae2-3c69b2401eed   ext4       
/dev/sda10       d810384b-b51f-4bd9-823b-45285ab65862   swap       
/dev/sda5        36A496B6A49677D7                       ntfs       Windows 7
/dev/sda6        B2DCEC4ADCEC0A85                       ntfs       Softwares
/dev/sda7        081C7C671C7C51A4                       ntfs       Games
/dev/sda8        AC30F8AE30F8809E                       ntfs       Movies & songs
/dev/sda9        C610987E109876E1                       ntfs       Photos & setup

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a08cc4ab-5c89-4202-aae2-3c69b2401eed
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a08cc4ab-5c89-4202-aae2-3c69b2401eed
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
if background_color 0,71,115; then
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a08cc4ab-5c89-4202-aae2-3c69b2401eed
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=a08cc4ab-5c89-4202-aae2-3c69b2401eed ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a08cc4ab-5c89-4202-aae2-3c69b2401eed
	echo	'Loading Linux 2.6.38-10-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=a08cc4ab-5c89-4202-aae2-3c69b2401eed ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a08cc4ab-5c89-4202-aae2-3c69b2401eed
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a08cc4ab-5c89-4202-aae2-3c69b2401eed
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=d810384b-b51f-4bd9-823b-45285ab65862 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.134063244 = 8.733883904    boot/grub/core.img                             1
   4.180221081 = 4.488478208    boot/grub/grub.cfg                             1
  38.876338482 = 41.743150592   boot/initrd.img-2.6.38-10-generic-pae          2
  38.582492352 = 41.427635712   boot/vmlinuz-2.6.38-10-generic-pae             1
  38.876338482 = 41.743150592   initrd.img                                     2
  38.582492352 = 41.427635712   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda11

00000000  20 2a 54 68 69 73 2c 0d  0a 20 20 20 20 49 52 70  | *This,..    IRp|
00000010  63 43 68 61 6e 6e 65 6c  42 75 66 66 65 72 20 2a  |cChannelBuffer *|
00000020  5f 70 52 70 63 43 68 61  6e 6e 65 6c 42 75 66 66  |_pRpcChannelBuff|
00000030  65 72 2c 0d 0a 20 20 20  20 50 52 50 43 5f 4d 45  |er,..    PRPC_ME|
00000040  53 53 41 47 45 20 5f 70  52 70 63 4d 65 73 73 61  |SSAGE _pRpcMessa|
00000050  67 65 2c 0d 0a 20 20 20  20 44 57 4f 52 44 20 2a  |ge,..    DWORD *|
00000060  5f 70 64 77 53 74 75 62  50 68 61 73 65 29 3b 0d  |_pdwStubPhase);.|
00000070  0a 0d 0a 0d 0a 2f 2a 20  5b 62 69 6e 64 61 62 6c  |...../* [bindabl|
00000080  65 5d 5b 64 69 73 70 6c  61 79 62 69 6e 64 5d 5b  |e][displaybind][|
00000090  69 64 5d 5b 70 72 6f 70  67 65 74 5d 20 2a 2f 20  |id][propget] */ |
000000a0  48 52 45 53 55 4c 54 20  53 54 44 4d 45 54 48 4f  |HRESULT STDMETHO|
000000b0  44 43 41 4c 4c 54 59 50  45 20 49 48 54 4d 4c 42  |DCALLTYPE IHTMLB|
000000c0  61 73 65 45 6c 65 6d 65  6e 74 5f 67 65 74 5f 68  |aseElement_get_h|
000000d0  72 65 66 5f 50 72 6f 78  79 28 20 0d 0a 20 20 20  |ref_Proxy( ..   |
000000e0  20 49 48 54 4d 4c 42 61  73 65 45 6c 65 6d 65 6e  | IHTMLBaseElemen|
000000f0  74 20 5f 5f 52 50 43 5f  46 41 52 20 2a 20 54 68  |t __RPC_FAR * Th|
00000100  69 73 2c 0d 0a 20 20 20  20 2f 2a 20 5b 6f 75 74  |is,..    /* [out|
00000110  5d 5b 72 65 74 76 61 6c  5d 20 2a 2f 20 42 53 54  |][retval] */ BST|
00000120  52 20 5f 5f 52 50 43 5f  46 41 52 20 2a 70 29 3b  |R __RPC_FAR *p);|
00000130  0d 0a 0d 0a 0d 0a 76 6f  69 64 20 5f 5f 52 50 43  |......void __RPC|
00000140  5f 53 54 55 42 20 49 48  54 4d 4c 42 61 73 65 45  |_STUB IHTMLBaseE|
00000150  6c 65 6d 65 6e 74 5f 67  65 74 5f 68 72 65 66 5f  |lement_get_href_|
00000160  53 74 75 62 28 0d 0a 20  20 20 20 49 52 70 63 53  |Stub(..    IRpcS|
00000170  74 75 62 42 75 66 66 65  72 20 2a 54 68 69 73 2c  |tubBuffer *This,|
00000180  0d 0a 20 20 20 20 49 52  70 63 43 68 61 6e 6e 65  |..    IRpcChanne|
00000190  6c 42 75 66 66 65 72 20  2a 5f 70 52 70 63 43 68  |lBuffer *_pRpcCh|
000001a0  61 6e 6e 65 6c 42 75 66  66 65 72 2c 0d 0a 20 20  |annelBuffer,..  |
000001b0  20 20 50 52 50 43 5f 4d  45 53 53 41 47 45 20 5f  |  PRPC_MESSAGE _|
000001c0  70 52 70 63 4d 65 73 73  61 67 65 2c 0d 0a 20 20  |pRpcMessage,..  |
000001d0  20 20 44 57 4f 52 44 20  2a 5f 70 64 77 53 74 75  |  DWORD *_pdwStu|
000001e0  62 50 68 61 73 65 29 3b  0d 0a 0d 0a 0d 0a 2f 2a  |bPhase);....../*|
000001f0  20 5b 62 69 6e 64 61 62  6c 65 5d 5b 64 69 73 70  | [bindable][disp|
00000200


=============================== StdErr Messages: ===============================

To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".


```

---

### Post by amjjawad on 2011-07-16
GRUB2 is not installed in the MBR of your HDD. It is installed in the /dev/sda1 which is the first partition in your HDD.

Try to Re-install GRUB2 to the MBR of your HDD: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---


---
title: "Reinstall grub without live cd"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by Fanas on 2011-05-14
I just reinstalled my double boot windows and of course it screwed up my grub. But I have no live cd at hand and only help I can find requires to use live cd. So is there a way to reinstall grub from windows.

---

### Post by corrytonapple on 2011-05-14
Well, if you have an USB Flash drive, and a ubuntu.iso, you can stick the iso on there with an application that makes it so it is bootable like a Live CD.  It works for Windows 7, and I think XP and Vista too.  I know it is for Fedora, but works for other Linux distros.  I am not in Windows, but if you want to find out the name, I will restart to find out the name of the application for you.
Okay, here is an easy link for if you get the "Live Flash Drive" to work.  Very simple and it works.
[http://themoth.wordpress.com/2009/03/25/reinstall-grub-after-windows-install-on-dual-boot-system/](http://themoth.wordpress.com/2009/03/25/reinstall-grub-after-windows-install-on-dual-boot-system/)

---

### Post by Fanas on 2011-05-14
> **corrytonapple said:**
> Well, if you have an USB Flash drive, and a ubuntu.iso, you can stick the iso on there with an application that makes it so it is bootable like a Live CD.  It works for Windows 7, and I think XP and Vista too.  I know it is for Fedora, but works for other Linux distros.  I am not in Windows, but if you want to find out the name, I will restart to find out the name of the application for you.
Okay, here is an easy link for if you get the "Live Flash Drive" to work.  Very simple and it works.
[http://themoth.wordpress.com/2009/03/25/reinstall-grub-after-windows-install-on-dual-boot-system/](http://themoth.wordpress.com/2009/03/25/reinstall-grub-after-windows-install-on-dual-boot-system/)

Yeah, I found old Ubuntu 9.04 live cd, reinstalled grub, but now it goes straight to grub rescue console.

---

### Post by corrytonapple on 2011-05-14
I am unsure, but you may be able to type at the GRUB recovery console:
```
FIXBOOT
```
and that should work.  What error is it?  For example:  "Error loading Grub Bootloader: Error 22" or something like that.
Hopefully that should work.  There is one more command if that does not work, but I really do not want to give it to you, since it can mess up the system.
Good Luck

---

### Post by Fanas on 2011-05-14
> **corrytonapple said:**
> I am unsure, but you may be able to type at the GRUB recovery console:
```
FIXBOOT
```
and that should work.  What error is it?  For example:  "Error loading Grub Bootloader: Error 22" or something like that.
Hopefully that should work.  There is one more command if that does not work, but I really do not want to give it to you, since it can mess up the system.
Good Luck

It's syntax error
line 74-78

I believe those are the 74-78 lines of grub.cfg:
```

if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep

```

---

### Post by madjr on 2011-05-14
doesnt ubuntu 9.04 has grub1 ?

i think 10.10 and 11.04 have grub2 ... so i read somewhere that they may have some incompatibility issues and that's why you are getting errors.

but still there may be some different commands you can use to reinstall it..

---

### Post by Fanas on 2011-05-14
> **madjr said:**
> doesnt ubuntu 9.04 has grub1 ?

i think 10.10 and 11.04 have grub2 ... so i read somewhere that they may have some incompatibility issues and that's why you are getting errors.

but still there may be some different commands you can use to reinstall it..

Yes, but I've downloaded the grub2 and installed it.

---

### Post by corrytonapple on 2011-05-14
What version of Ubuntu do you have?  If it is above 9.10, then you need to download an ISO of 10.04 or 11.04.  I say 10.04 because it is the LTS, and the 11.04 is the latest version.  So, try that on a flash drive or make it a live CD and then try restoring GRUB.  It is always good to have a Flash Drive or a CD with Ubuntu on it.  Also, if you make the Flash Drive bootable, you can wipe it later and use it for other things anyway.

---

### Post by Fanas on 2011-05-14
> **corrytonapple said:**
> What version of Ubuntu do you have?  If it is above 9.10, then you need to download an ISO of 10.04 or 11.04.  I say 10.04 because it is the LTS, and the 11.04 is the latest version.  So, try that on a flash drive or make it a live CD and then try restoring GRUB.  It is always good to have a Flash Drive or a CD with Ubuntu on it.  Also, if you make the Flash Drive bootable, you can wipe it later and use it for other things anyway.

There's the problem I have no empty cds or flash drives and my 11.04 cd wont run live for some reason.

---

### Post by corrytonapple on 2011-05-14
How are you using getting online right now?  Another computer I assume?
Your 11.04 CD won't run?  Did you install from it?  Where does the CD not work, like in the middle of bootup, or when you get to the desktop?

---

### Post by Fanas on 2011-05-14
> **corrytonapple said:**
> How are you using getting online right now?  Another computer I assume?
Your 11.04 CD won't run?  Did you install from it?  Where does the CD not work, like in the middle of bootup, or when you get to the desktop?

Ubuntu 9.04 live cd which works. I did install from that cd, only live wont work, probably something with unity. As it only shows black screen.

Found 10.04 cd, installed grub from it and now it wont load the rescue console, but it wont load anything else either. Just black screen flickering once in a while.

---

### Post by corrytonapple on 2011-05-14
Try hitting any key to see what happens.  I sometimes need to do that.  If not, are you sure you installed GRUB?  
I am out of ideas now.

---

### Post by Fanas on 2011-05-14
> **corrytonapple said:**
> Try hitting any key to see what happens.  I sometimes need to do that.  If not, are you sure you installed GRUB?  
I am out of ideas now.

It's so tragic, I'm beginning to laugh. Every time I try to fix it, it gets worse.
I install win7, lose access to ubuntu.
Edit win boot manager, lose access to win, gain to ubuntu.
Reinstall grub, lose any access.
Reinstall grub from live, get syntax error.
Reinstall grub from another live, get nothing.

I have a bad feeling that it will end in me in doing a hard wipe. :)


Gonna restart, try something. Maybe it will help, but I doubt it.

---

### Post by drs305 on 2011-05-14
> **Fanas said:**
> Ubuntu 9.04 live cd which works. I did install from that cd, only live wont work, probably something with unity. As it only shows black screen.

Found 10.04 cd, installed grub from it and now it wont load the rescue console, but it wont load anything else either. Just black screen flickering once in a while.

Did you chroot into your Ubuntu installation and then purge/reinstall Grub2?

Also, if you are at a black screen, it means that Grub2 probably passed control over to the kernel. When Grub fails it will either give you an error message or a grub or grub-rescue prompt.

If you have a blinking cursor, it's probably a video issue. If you can get to the grub menu (hold SHIFT during boot if necessary), press 'e', go to the end of the 'linux' line, remove 'quiet splash' and add 'nomodeset'. CTRL-x to boot. If it boots, install your video driver.

---

### Post by corrytonapple on 2011-05-14
What are you typing to reinstall GRUB?
How about I give you a how-to on reinstalling GRUB.  Even if you have done it, just do it again anyway.  You never know, I think and hope that everytime I see this thread in the User CP that it worked.  Here is the link:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting) the Master Boot Record
First mount your Ubuntu Drive, then do what is in the link down to where it says "Grub Legacy", then stop.
Good Luck and Report Back

Oh and follow drs305's advice.  He is the master of GRUB.  I know it, taking his advice to get a nice looking GRUB myself.

---

### Post by Fanas on 2011-05-14
Finally, grub from 10.10 cd worked!!!



Edit: Ubuntu works, but Windows still not loading up :(
Edit2: Wtf, happened to my windows partition, it's not showing up as a mountable partition.

---

### Post by corrytonapple on 2011-05-14
Go to GRUB and try to boot up into Windows.  Chances are good it will want to run a cdisk on itself.  If it is 7, it may even want you to put the recovery DVD in.  With GRUB being the main bootloader now it makes Windows think something is wrong.

---

### Post by Fanas on 2011-05-14
> **corrytonapple said:**
> Go to GRUB and try to boot up into Windows.  Chances are good it will want to run a cdisk on itself.  If it is 7, it may even want you to put the recovery DVD in.  With GRUB being the main bootloader now it makes Windows think something is wrong.

It says its missing mbr file and that I should go into recovery console and fix it there.

---

### Post by wilee-nilee on 2011-05-14
> **Fanas said:**
> It says its missing mbr file and that I should go into recovery console and fix it there.

Okay since we have the attention of drs305, lets do what needs to be done really to get to the heart of the matter.

So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will tell what is where and take out the guessing.

---

### Post by Fanas on 2011-05-14
> **wilee-nilee said:**
> Okay since we have the attention of drs305, lets do what needs to be done really to get to the heart of the matter.

So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will tell what is where and take out the guessing.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   163,842,047   163,635,200   7 HPFS/NTFS
/dev/sda3         163,844,094   625,141,759   461,297,666   5 Extended
/dev/sda5         163,844,096   167,747,583     3,903,488  82 Linux swap / Solaris
/dev/sda6         167,749,632   616,765,439   449,015,808  83 Linux
/dev/sda7         616,767,488   625,141,759     8,374,272  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        70B8CF59B8CF1D0A                       ntfs       System Reserved               
/dev/sda2        702AD49E2AD462A0                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        71ff8e1d-0054-4e4f-b10a-39bf0ad0d61e   swap                                     
/dev/sda6        267e210c-acd2-411d-849f-cfb1615d9e02   ext4                                     
/dev/sda7        565340b6-0b36-4af1-ab70-11eebee55f0b   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 267e210c-acd2-411d-849f-cfb1615d9e02
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 267e210c-acd2-411d-849f-cfb1615d9e02
set locale_dir=($root)/boot/grub/locale
set lang=en_SG
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
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 267e210c-acd2-411d-849f-cfb1615d9e02
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=267e210c-acd2-411d-849f-cfb1615d9e02 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 267e210c-acd2-411d-849f-cfb1615d9e02
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=267e210c-acd2-411d-849f-cfb1615d9e02 ro single 
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
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 267e210c-acd2-411d-849f-cfb1615d9e02
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 267e210c-acd2-411d-849f-cfb1615d9e02
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root F6726B0B726AD043
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=267e210c-acd2-411d-849f-cfb1615d9e02 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=565340b6-0b36-4af1-ab70-11eebee55f0b none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 313.6GB: boot/grub/core.img
 150.8GB: boot/grub/grub.cfg
 313.5GB: boot/grub/stage2
 114.3GB: boot/initrd.img-2.6.38-8-generic
 313.6GB: boot/vmlinuz-2.6.38-8-generic
 114.3GB: initrd.img
 313.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  25 ff ff ff ff ff ff ff  ff 87 5a 43 31 fc be fe  |%.........ZC1...|
00000010  5c ff ff ff ff ff ff ff  ff 05 4a 43 31 80 2a 2a  |\.........JC1.**|
00000020  ad ff ff ff ff ff ff ff  ff 05 4a 64 39 5f 58 c0  |..........Jd9_X.|
00000030  eb ff ff ff ff ff ff ff  ff c5 41 23 31 78 7f bf  |..........A#1x..|
00000040  ff ff ff ff ff ff ff ff  ff 63 39 e2 28 bb 7a be  |.........c9.(.z.|
00000050  70 ff ff ff ff ff ff ff  ff 46 52 e2 28 57 9d 37  |p........FR.(W.7|
00000060  0b ff ff ff ff ff ff ff  ff 46 5a 22 31 b7 dc 5c  |.........FZ"1..\|
00000070  f5 ff ff ff ff ff ff ff  ff 46 5a 43 39 55 0f 02  |.........FZC9U..|
00000080  5a ff ff ff ff ff ff ff  ff 87 62 22 31 f5 af f0  |Z.........b"1...|
00000090  7a ff ff ff ff ff ff ff  ff 26 52 84 41 af 7a 70  |z........&R.A.zp|
000000a0  3d ff ff ff ff ff ff ff  ff 46 52 22 31 d5 5a f8  |=........FR"1.Z.|
000000b0  58 ff ff ff ff ff ff ff  ff 67 52 22 31 ff b7 2e  |X........gR"1...|
000000c0  25 ff ff ff ff ff ff ff  ff a4 39 e2 28 b7 8a aa  |%.........9.(...|
000000d0  5c ff ff ff ff ff ff ff  ff a4 39 23 31 83 20 dc  |\.........9#1. .|
000000e0  de ff ff ff ff ff ff ff  ff 84 39 e2 28 2e fa d8  |..........9.(...|
000000f0  bf ff ff ff ff ff ff ff  ff 63 39 03 29 fc 7f 4f  |.........c9.)..O|
00000100  32 ff ff ff ff ff ff ff  ff 84 39 e2 28 d7 35 39  |2.........9.(.59|
00000110  96 ff ff ff ff ff ff ff  ff c5 41 c2 20 e0 b8 2e  |..........A. ...|
00000120  de ff ff ff ff ff ff ff  ff 84 39 e2 28 bb f0 e0  |..........9.(...|
00000130  60 ff ff ff ff ff ff ff  ff e5 49 23 31 37 1e 3b  |`.........I#17.;|
00000140  dd ff ff ff ff ff ff ff  ff a4 41 c1 28 88 a8 dc  |..........A.(...|
00000150  fe ff ff ff ff ff ff ff  ff a4 41 e2 28 2f 5e 57  |..........A.(/^W|
00000160  fd ff ff ff ff ff ff ff  ff a4 41 02 29 fe c9 89  |..........A.)...|
00000170  c9 ff ff ff ff ff ff ff  ff 23 31 c1 20 ce 75 0f  |.........#1. .u.|
00000180  eb ff ff ff ff ff ff ff  ff a4 41 c1 20 f5 b5 35  |..........A. ..5|
00000190  95 ff ff ff ff ff ff ff  ff 63 39 c1 20 f0 fa d6  |.........c9. ...|
000001a0  96 ff ff ff ff ff ff ff  ff 23 31 a0 20 80 a3 b5  |.........#1. ...|
000001b0  7a ff ff ff ff ff ff ff  ff 22 31 c1 20 35 00 fe  |z........"1. 5..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 3b 00 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 02 90  3b 00 00 78 c3 1a 00 00  |........;..x....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```



Now only windows won't load, it says no device found, no such disk.

---

### Post by wilee-nilee on 2011-05-14
I would follow drs305, always.;)

---

### Post by drs305 on 2011-05-14
The Windows UUID appears to be incorrect:
> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	[COLOR="DarkRed"]search --no-floppy --fs-uuid --set=root **F6726B0B726AD043**[/COLOR]
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
vs
> blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        **70B8CF59B8CF1D0A **                      ntfs       System Reserved               
/dev/sda2        702AD49E2AD462A0                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        71ff8e1d-0054-4e4f-b10a-39bf0ad0d61e   swap                                     
/dev/sda6        267e210c-acd2-411d-849f-cfb1615d9e02   ext4                                     
/dev/sda7        565340b6-0b36-4af1-ab70-11eebee55f0b   swap                                     
/dev/sda: PTTYPE="dos" 

If update-grub does not correct it (it should):
Manually edit grub.cfg (temporary fix) with:
```
gksu gedit /boot/grub/grub.cfg
```
Remove the entire search line, or change it to the correct UUID, and reboot **without** running update-grub.

---

### Post by Fanas on 2011-05-15
> **drs305 said:**
> The Windows UUID appears to be incorrect:

vs


If update-grub does not correct it (it should):
Manually edit grub.cfg (temporary fix) with:
```
gksu gedit /boot/grub/grub.cfg
```
Remove the entire search line, or change it to the correct UUID, and reboot **without** running update-grub.


It worked, thanks.

---

### Post by drs305 on 2011-05-15
> **Fanas said:**
> It worked, thanks.

Hopefully it was the 'update-grub' that fixed it. If it was only fixed by manually editing grub.cfg we will have to take steps to make sure it doesn't happen when the grub files are updated via 'update-grub', which would overwrite the changes.

If everything is now ok, pleased mark the thread solved via the 'Thread Tools' link near the top right of the first post.

Happy Ubuntu-ing !

---

### Post by Fanas on 2011-05-17
> **drs305 said:**
> Hopefully it was the 'update-grub' that fixed it. If it was only fixed by manually editing grub.cfg we will have to take steps to make sure it doesn't happen when the grub files are updated via 'update-grub', which would overwrite the changes.

If everything is now ok, pleased mark the thread solved via the 'Thread Tools' link near the top right of the first post.

Happy Ubuntu-ing !

Update-grub worked just fine.

---


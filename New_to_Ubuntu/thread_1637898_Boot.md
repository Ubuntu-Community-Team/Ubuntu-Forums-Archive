---
title: "Boot"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by ArmyDad on 2010-12-05
I guess I should have titled this thread "No Boot."

I have my computer set up with dual Hard Drives, one with Vista (boo, I know.  Looking to replace it.) and the other with ubuntu 10.10.  I installed the 10.10 version.  Everything was working well, but I was given a tip that the 10.04 version would work with my audio card better, so I format the HD with ubuntu and installed the 10.04.  The install went as smooth as possible, prompt me to reboot, so I did. POST ran fine, m.board splash showed, then this:

_


:shock:

And thats it.  It sat on a "_" screen until I reset.  Thinking I did something wrong, or the disk was bad, I repeat the process only with the 10.10 I had originally loaded.  And again, just the "_" screen.

Any idea what I did wrong?

---

### Post by sikander3786 on 2010-12-05
Welcome to the forums :-)

Can you see the Grub menu? Make sure boot order is correct in the Bios menu and you are booting from the same HDD that has Grub installed to it.

If that is not the issue here, boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us nearly everything we need to know about your setup.

Wrap your output with proper code tags # from post menu. [/code] at the end [code] at the beginning.

---

### Post by ArmyDad on 2010-12-05
No Grub menu.  It stops just before it.

I set the BIOS to boot from the HDD with all the ubuntu files.  Same result.

To make sure I did this correctly... the only way to get in was to change back was to boot from CD/DVD ROM.  I boot the CD, selected "test ubuntu" and insert a flash drive with the boot info su.  I ran the su, got the results:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,423,200,255 1,423,198,208  83 Linux
/dev/sdb2       1,423,202,302 1,465,147,391    41,945,090   5 Extended
/dev/sdb5       1,423,202,304 1,465,147,391    41,945,088  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4105 MB, 4105175040 bytes
37 heads, 37 sectors/track, 5856 cylinders, total 8017920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,760     8,017,919     8,015,160   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        E4C4DD7BC4DD5102                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        e5801901-f51b-4e33-a484-49820ad50960   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        666976be-abe6-42f1-99d6-9241057cd079   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        58A8-0523                              vfat       HP V125W                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/HP V125W          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set e5801901-f51b-4e33-a484-49820ad50960
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set e5801901-f51b-4e33-a484-49820ad50960
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e5801901-f51b-4e33-a484-49820ad50960
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e5801901-f51b-4e33-a484-49820ad50960 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e5801901-f51b-4e33-a484-49820ad50960
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e5801901-f51b-4e33-a484-49820ad50960 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e5801901-f51b-4e33-a484-49820ad50960
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e5801901-f51b-4e33-a484-49820ad50960
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e4c4dd7bc4dd5102
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=e5801901-f51b-4e33-a484-49820ad50960 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=666976be-abe6-42f1-99d6-9241057cd079 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  94.6GB: boot/grub/core.img
 296.4GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
  94.6GB: boot/vmlinuz-2.6.35-22-generic
    .9GB: initrd.img
  94.6GB: vmlinuz
```

---

### Post by sikander3786 on 2010-12-05
The problem lies here.

> => Grub 2 is installed in the MBR of **/dev/sda** and looks on the same drive in
partition **#1** for (,msdos1)/boot/grub.

So there are 2 solutions here.

First one is just to install Grub to the MBR of sda and point it to looks for /boot/grub in sdb1.

Second is to restore Windows boot loader on sda, once that is capable of booting independently, install Grub to the MBR of sdb and make your Ubuntu HDD, first boot device in the boot menu.

Both methods are acceptable. I feel the second one is better because if some time later, there is problem in Grub or even in your Ubuntu HDD, and Grub can't boot for any reason, you'll still be able to boot Windows just by switching boot device in Bios ;-)

If you want to adopt this solution, you'll need a Windows 7 recovery/repair disc (easily available on the net for download, if you don't have one). Then try startup repair from that disc, at least 3 times. Yes thats correct, 3 times. Once you are able to boot Windows successfully, go for installation of Grub.

For that, boot from an Ubuntu Live CD/USB as you did previously and install Grub to sdb.

```
sudo mount /dev/sdb1 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Note, for the second one it is just sdb without an integer and not sdb1.

Make your Ubuntu HDD first boot device and boot from it. If it hasn't yet detected Windows, from your Installed Ubuntu's Terminal,

```
sudo update-grub
```

And Windows should be added to Grub menu.

If you want to adopt solution no. 1, you just need to boot an Ubuntu Live CD/USB and just do these 2 commands. Simple.

```
sudo mount /dev/sdb1 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

There is just a minor change in the second command.

Feel free to ask if you've any queries.

And it would also be better if you could please edit your above post and wrap it with code tags #. [/code] at the end and [code] at the beginning.

---

### Post by ArmyDad on 2010-12-05
I'm sorry, first time posting here, didn't know about the code tags!

I'm assuming you meant a Vista recovery disk, so I'm getting that now.

Thank you very much for the advice.  I hope to have it up and running soon.  I'll be sure to post if I do something wrong or have a question. :)

---

### Post by sikander3786 on 2010-12-05
Yep Vista Recovery disk. Typo in my above post where I said Windows 7 recovery disc :-)

Open for any further queries :-)

Good Luck!

---

### Post by ArmyDad on 2010-12-05
No problem, I just wanted to make sure I was doing it right.  I am seeing a problem when trying to run repair on Vista.  (and yes, this was more than 3 tries into it. ;) )  Every time I click repair, I see this notification:

[IMG]http://img.photobucket.com/albums/v293/disturbedbass13/IMAG0049.jpg[/IMG]

---

### Post by sikander3786 on 2010-12-05
I am afraid I've never tried that Vista recovery ever.

Try to do it from the command prompt.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Simply running this command would be enough to do it. And just once only ;-)

```
BootRec.exe /fixmbr
```

---

### Post by ArmyDad on 2010-12-05
Haha, okay.  Why was it 3 previously?  Out of curiosity.

---

### Post by sikander3786 on 2010-12-05
> **ArmyDad said:**
> Haha, okay.  Why was it 3 previously?  Out of curiosity.
3 times for Startup Repair if you get a GUI option there.

And just 1 time for the command.

Was that successful and is Vista able to boot now?

---

### Post by ArmyDad on 2010-12-05
I used the startup repair, reboot, and GRUB loaded and ubuntu loaded just fine.  I have no idea why, but it works for me.

Now the issue is back to what I originally was changing versions of ubuntu for... I disabled the on-board audio, and I would like to use my M-Audio Delta 1010lt.  

There aren't any direct drivers from M-Audio itself. 
[http://www.m-audio.com/products/en_us/Delta1010LT.html](http://www.m-audio.com/products/en_us/Delta1010LT.html)

But there is a site it links to: [http://www.opensound.com/](http://www.opensound.com/)
OSS is supposed to support the 1010lt somehow?

Any idea how that is supposed to work?

---

### Post by sikander3786 on 2010-12-05
Not too experience with multimedia stuff at all :-)

You need to start a new thread under Multimedia & Video sub-forums.

If your issue regarding boot is solved, you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by ArmyDad on 2010-12-05
Awesome.  Thanks for your help.

---


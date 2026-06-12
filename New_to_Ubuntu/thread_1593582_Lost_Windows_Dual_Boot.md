---
title: "Lost Windows Dual Boot"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by ashwat on 2010-10-11
I had a HDD with a single partition WIN7 installation.

Using Partition Magic, I created another partition from the free space.

Using a Ubuntu 10.10 Live USB disk, I created a 1GB swap space and remaining partition as ext4 and installed. 

But I seem to have messed up the boot record because now GRUB doesn't load up assuming Ubuntu is the only OS installed. :(

Kindly direct me to redress this situation and get me some dual boot.:)

( I would have preferred wubi but it kept directing to the 64bit installation even though I had the 32bit iso in the same folder :confused:)

---

### Post by Temposs on 2010-10-11
I would suggest that you should try installing Ubuntu again via the Ubuntu LiveCD and use the Manual Installation option to view and set the partition options.

Are you sure that your Windows 7 partition still exists and that you didn't accidentally erase it during the Ubuntu installation?

---

### Post by ashwat on 2010-10-11
The partition is still there and gets mounted automatically in Ubuntu and is useable as well.

---

### Post by Temposs on 2010-10-11
It could just be that the GRUB menu isn't displaying as you're used to. I think if you hold down the Shift key as the machine boots, it may bring up the GRUB menu. Then look to see if Windows is shown as an option there.

---

### Post by ashwat on 2010-10-11
Grub does not have a mention of the Windows installation. Checked in /boot/grub as well as pressing shift while bootup.

---

### Post by Steam. on 2010-10-11
Your fault for installing GRUB.Windows's MBR is the one that shows Win7, GRUB doesn't.I suggest reinstalling Ubuntu, BUT don't make a partition, instead just install it from the LiveCD and choose to install it in free space.

---

### Post by BigRedButton on 2010-10-11
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by ashwat on 2010-10-11
So do I keep the NTFS partition as boot during the LiveUSB reinstallation?

---

### Post by cariboo on 2010-10-11
> **ashwat said:**
> So do I keep the NTFS partition as boot during the LiveUSB reinstallation?

Please don't re-install, you have the chance of doing even more damage. Just leave everything as it is.

Boot from the Live CD and once at the desktop, open an Applications->Accessories->Terminal and type:

```
sudo fdisk -l
```

The above command will list your partitions take note of which on is marked as linux, in your case it would more than likely be /dev/sda6, but make sure.

Next in the same terminal type:

[list]
[*] sudo mount /dev/sda6 /mnt and presss enter
[*] sudo mount /dev /mnt/dev, press enter
[*] sudo mount /sys /mnt/sys, press enter
[*] sudo mount /proc /mnt/proc, press enter
[*] sudo chroot /mnt
[/list]

Make sure that you enter your partition in stead of the one in the example above. Once you have entered the above commands, you should be at a root prompt, it should look something like this:

```
root@ubuntu:/mnt#
```

Next type at the prompt:

```
grub-install /dev/sda
```

It should give you a completed successfully message, next type:

```
update-install
```

You should see a list of your operating systems when the command is finished. Press Ctrl-d twice to exit the termianl and then reboot.

---

### Post by oldfred on 2010-10-11
Your install should have found the windows. If it was working.

Did you try this?

sudo update-grub

If that does not work run this, so we can see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by amjjawad on 2010-10-11
> **ashwat said:**
> I had a HDD with a single partition WIN7 installation.

Using Partition Magic, I created another partition from the free space.


Have you:

1- Deleted all the temp files, interent files, cookies, extra (usually CCleaner does the job).
2- Defragmented your HDD

Before creating the new partition?

---

### Post by ashwat on 2010-10-11
the linux partition is sda3 but > sudo mount /dev /mnt/dev, gives > /dev is not a block deviceerror

---

### Post by ashwat on 2010-10-11
> **oldfred said:**
> Your install should have found the windows. If it was working.

Did you try this?

sudo update-grub

If that does not work run this, so we can see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     1,955,172     1,953,125  82 Linux swap / Solaris
/dev/sda2          35,680,365   234,436,544   198,756,180   7 HPFS/NTFS
/dev/sda3           1,955,840    35,680,255    33,724,416  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4026 MB, 4026531328 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7864319 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3d963aef-1859-4e0e-94e9-1f3f4f12c016   swap                                     
/dev/sda2        EE90462C9045FC19                       ntfs                                     
/dev/sda3        618cc18a-04ea-4178-90c1-94af0cc696b7   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        49BE-5F60                              vfat       PKBACK# 001                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 618cc18a-04ea-4178-90c1-94af0cc696b7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 618cc18a-04ea-4178-90c1-94af0cc696b7
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 618cc18a-04ea-4178-90c1-94af0cc696b7
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=618cc18a-04ea-4178-90c1-94af0cc696b7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 618cc18a-04ea-4178-90c1-94af0cc696b7
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=618cc18a-04ea-4178-90c1-94af0cc696b7 ro single 
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 618cc18a-04ea-4178-90c1-94af0cc696b7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 618cc18a-04ea-4178-90c1-94af0cc696b7
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=618cc18a-04ea-4178-90c1-94af0cc696b7 /               ext4    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  10.0GB: boot/grub/core.img
   7.9GB: boot/grub/grub.cfg
   2.6GB: boot/initrd.img-2.6.35-22-generic
   9.9GB: boot/vmlinuz-2.6.35-22-generic
   2.6GB: initrd.img
   9.9GB: vmlinuz
```

---

### Post by oldfred on 2010-10-11
You did not have a single partition win7 install, although when in windows that was all you saw. Win7 new installs have a 100MB boot/repair partition at the beginning of the drive that has:
/bootmgr /Boot/BCD

You also have a wubi install.

You need to move boot flag to sda2 so the repair CD can find your main partition, and use a windows repair CD to fix the missing bootmgr and create a new BCD.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by ashwat on 2010-10-13
I have run into a different issue now. I do not have a CD drive but have a dump of the Win7 ISO which I used along with UNetbootin to make a bootable USB from within Ubuntu but upon booting from this disk, the Win7 Install option does not load up.

---

### Post by oldfred on 2010-10-13
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

I wanted to see if I could install the above to a USB flash from Ubuntu. I did not get it to work without creating a bootable CD and using that to install (copy) to USB. I was then able to install grub2 to the same partition and use grub to boot the repair.

---

### Post by the_jlx on 2010-10-13
> **Steam. said:**
> Your fault for installing GRUB.Windows's MBR is the one that shows Win7, GRUB doesn't.I suggest reinstalling Ubuntu, BUT don't make a partition, instead just install it from the LiveCD and choose to install it in free space.

uhumm bad advice and has nothing to do whit the problem.
BEST way if you know how is to manually create the partition etc if you know how.

---

### Post by ashwat on 2010-11-17
Finally got hold of a Win7 install disk. 

After the chkdsk routines and fix boot complete successfully, ScanOs found 0 windows installations. This in spite of the disk prompting auto repair for boot errors upon opening repair tools. What do I do now ?

EDIT: I think I rebuilt the bcd by entering the step by step Commands. Upon restart, grub update and restart, vista loader showed up in the grub menu. Selecting it kept giving error that winload32.exe is missing or corrupt. 

> **oldfred said:**
> You did not have a single partition win7 install, although when in windows that was all you saw. Win7 new installs have a 100MB boot/repair partition at the beginning of the drive that has:
/bootmgr /Boot/BCD

You also have a wubi install.

You need to move boot flag to sda2 so the repair CD can find your main partition, and use a windows repair CD to fix the missing bootmgr and create a new BCD.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---


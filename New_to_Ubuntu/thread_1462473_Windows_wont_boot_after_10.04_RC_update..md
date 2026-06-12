---
title: "Windows wont boot after 10.04 RC update."
date: 2010-04-25
forum: New to Ubuntu
---

### Post by JaxDragon on 2010-04-25
I just updated ubuntu to 10.04. But now, when I start my system, and select windows on the grub screen, all I get is this blinking underscore. I can't type anything there. I really need to fix this, as I have crucial things to do on windows.

---

### Post by oldfred on 2010-04-25
It may be just reinstalling the boot loader, but if you installed grub into the windows partition it will need repairs.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

To see all the details:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by JaxDragon on 2010-04-25
What do you mean? I still want to have the ability to boot ubuntu, and it looks like doing any of those will allow for only one bootable os.

---

### Post by oldfred on 2010-04-25
The boot script results.txt should give us more information on what is required to do.

If you have to repair windows, it is easier to run the fixmbr command with all the other windows repair commands to make sure windows boots on its own. Then you can reinstall grub and it will find windows and let you boot either one.

---

### Post by JaxDragon on 2010-04-25
Heres the results.txt thingy ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 279806 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 281238 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 275638 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    17,832,149    17,832,087   7 HPFS/NTFS
/dev/sda2    *     17,832,150   234,436,544   216,604,395   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   160,151,984   160,151,922   5 Extended
/dev/sdb5                 126   156,248,189   156,248,064  83 Linux
/dev/sdb6         156,248,253   160,151,984     3,903,732  82 Linux swap / Solaris
/dev/sdb2         160,153,600   312,578,047   152,424,448   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9E84DC5F84DC3C09                       ntfs       Recovery/Linux                
/dev/sda2        043CEEF53CEEE122                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        1C3A05333A050B88                       ntfs       Seagate Extra Disk Space      
/dev/sdb5        207742c4-3020-4b69-8159-9bdef3ec0df3   ext4                                     
/dev/sdb6        b3466948-be36-405d-9635-25d682d75cad   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            udf        (ro,nosuid,nodev,utf8,user=jaxdragon)
/dev/sda2        /media/043CEEF53CEEE122  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 207742c4-3020-4b69-8159-9bdef3ec0df3
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 207742c4-3020-4b69-8159-9bdef3ec0df3
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
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 207742c4-3020-4b69-8159-9bdef3ec0df3
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=207742c4-3020-4b69-8159-9bdef3ec0df3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 207742c4-3020-4b69-8159-9bdef3ec0df3
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=207742c4-3020-4b69-8159-9bdef3ec0df3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 207742c4-3020-4b69-8159-9bdef3ec0df3
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=207742c4-3020-4b69-8159-9bdef3ec0df3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 207742c4-3020-4b69-8159-9bdef3ec0df3
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=207742c4-3020-4b69-8159-9bdef3ec0df3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 207742c4-3020-4b69-8159-9bdef3ec0df3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 207742c4-3020-4b69-8159-9bdef3ec0df3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 043ceef53ceee122
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=207742c4-3020-4b69-8159-9bdef3ec0df3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=b3466948-be36-405d-9635-25d682d75cad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
    .1GB: boot/grub/grub.cfg
   7.2GB: boot/initrd.img-2.6.31-20-generic
   7.2GB: boot/initrd.img-2.6.32-21-generic
    .3GB: boot/vmlinuz-2.6.31-20-generic
   5.7GB: boot/vmlinuz-2.6.32-21-generic
   7.2GB: initrd.img
   7.2GB: initrd.img.old
   5.7GB: vmlinuz
    .3GB: vmlinuz.old
```

---

### Post by JaxDragon on 2010-04-25
Anyone?

---

### Post by oldfred on 2010-04-25
When you installed/updated did you get a checkbox to install grub. You only should have installed to one place the MBR of the same drive as the Ubuntu install. You installed it to all the drives and partitions which wiped out the windows boot loader in the windows partition.

You will need the windows CD or DVD.

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

You may not have to run the fixMBR but if windows then does not boot we have to go back and run that, but then will have to reinstall grub2.

---

### Post by JaxDragon on 2010-04-28
Well I had to use fixmbr, so now grub doesn't show up. How do I install it again? Keep in mind my windows partitions are on a totally separate hard disk than my ubuntu partitions. I have a 9.10 live cd, but I don't know if that can install grub on a 10.04 RC drive.

---

### Post by oldfred on 2010-04-28
this should get grub2 reinstalled.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You will then have to switch boot in BIOS. Did you have grub2 installed in the other drive already? If so you should not have to reinstall, just switch boot in BIOS.

---

### Post by JaxDragon on 2010-04-28
I do, in fact, believe I have grub on my ubuntu HD. Will grub still detect my windows loader, or will I have to switch boots in the bios every time I want to switch OS's?

---

### Post by vamc on 2010-04-28
May be you can install grub from live cd of karmic koala. Boot into the live environment, open up the terminal and try the following:

$ sudo fdisk -l

Then you will get some output regarding the Device boot. Clearly make note of the device (for ex: /dev/sda1) where system is installed. 

Then:

$ sudo mkdir /media/root

Next, link your Ubuntu installation and this new folder:

$ sudo mount /dev/sda1 /media/root

sda1 should be replaced with the appropriate device name.

If you’ve done this correctly, then you should see the following:

$ ls /media/root

bin dev home lib mnt root srv usr
boot etc initrd lib64 opt sbin sys var
cdrom initrd.img media proc selinux tmp vmlinuz

Now, you can reinstall grub:

$ sudo grub-install --root-directory=/media/root /dev/sda

Installation finished. No error reported.

This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect, fix it and re-run the script grub-install. 
(hd0) /dev/sda

Now reboot. grub should show its face.

---

### Post by theozzlives on 2010-04-28
You got Windows to boot, good. Now insert the live CD and go to the Terminal.

```
sudo -i
mount /dev/sdb1 /mnt/
install-grub /mnt/ /dev/sdb
```

Adjust to your settings

---

### Post by oldfred on 2010-04-28
With grub2 sudo update-grub almost always finds working windows installs.

---

### Post by JaxDragon on 2010-04-28
Well I tried following the terminal commands you all have given me, to no success. I also tried booting from my ubuntu hd, and it still just went to the windows hard drive and booted windows.

---

### Post by oldfred on 2010-04-28
If you have grub installed in sdb it will not directly boot windows if you boot from sdb.

Rerun the script if booting is not working so we can see what changes have been made.

---

### Post by linuxman94 on 2010-04-28
Should have been posted in the Lucid Dev forum. I'll have it moved for you.

---

### Post by JaxDragon on 2010-04-28
> **oldfred said:**
> If you have grub installed in sdb it will not directly boot windows if you boot from sdb.

Rerun the script if booting is not working so we can see what changes have been made.

Will the script still work on a livecd version?

---


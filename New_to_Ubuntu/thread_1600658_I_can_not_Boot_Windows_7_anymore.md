---
title: "I can not Boot Windows 7 anymore"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by Ymurti on 2010-10-19
I have Windows 7 and Ubuntu 10.10 in my netbook.

When I power on my netbook Advent after a while the Boot Menu appears with the options:

Ubuntu, with Linux 2.6.35-22-generic
Memory Test
Windows 7 (loader) (on/dev/sda1)

When I highlight  Windows 7 ,  I get the following message:

“This is not a bootable disk. Please insert a bootable floppy and press any key to try again.”

With Ubuntu 10.4 I did not have any problem.

Please help me to boot Windows 7 again.

:(

---

### Post by linux-hack on 2010-10-19
what is your partition scheme ? and did you try a ```
sudo update-grub
```

---

### Post by SuaSwe on 2010-10-19
Not personally familiar with this message but have you checked that the Windows drive is present in BIOS OK, so you know there isn't some other problem there? Similarly, can you mount and access the Windows drive from Ubuntu?

---

### Post by Hippytaff on 2010-10-19
> 
mount and access the Windows drive from Ubuntu

 
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
 
I think Windows 7 (loader) is an application to load windows?
 
when if ubuntu type 
 
```

df

```
 
in the ternminal - and post the output here - you can oprn a terminal with CTRL+ALT+T

---

### Post by Mark Phelps on 2010-10-19
Not familiar with that Win7 error message (and I thought I had encountered them all!) ... but it doesn't look good.

Ordinarily, I would tell you to go to the site below, download and burn the appropriate Win7 Repair CD, boot from that CD, and run Startup Repair three times:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

But, since your netbook most probably does NOT have an optical drive, unless you can boot from an external optical drive (and you have one), you're left having to create a Win7 Repair USB stick -- and I have no idea how to do that.

What I would suggest is that you check with a Win7 forum (sevenforums.com is one of the best).  They have tutorials on how to create boot media.  Perhaps they can help you create a Repair USB stick you can use.

Sorry I can't be of more help.

---

### Post by Hippytaff on 2010-10-19
I think it's possible to make a bootable usb (even for windows) with unetbootin...worth looking into
 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Ymurti on 2010-10-19
> **linux-hack said:**
> what is your partition scheme ? and did you try a ```
sudo update-grub
```
Dear linux-hack,

I updated grub and now the option to boot in Windows 7 is not there anymore???

How do I find out my partition scheme??? Sorry I am a begginer

---

### Post by Ymurti on 2010-10-19
> **SuaSwe said:**
> Not personally familiar with this message but have you checked that the Windows drive is present in BIOS OK, so you know there isn't some other problem there? Similarly, can you mount and access the Windows drive from Ubuntu?
Dear SuaSwe,

I can access Windows 7 from Ubuntu.

---

### Post by Ymurti on 2010-10-19
> **Hippytaff said:**
> [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
 
I think Windows 7 (loader) is an application to load windows?
 
when if ubuntu type 
 
```

df

```
 
in the ternminal - and post the output here - you can oprn a terminal with CTRL+ALT+T
Dear Hippytaff,

Here it is the result,


Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             63005620  42999760  16805300  72% /
none                    502536       248    502288   1% /dev
none                    508132       220    507912   1% /dev/shm
none                    508132       220    507912   1% /var/run
none                    508132         0    508132   0% /var/lock
/dev/sda2            105468744  38037740  67431004  37% /media/Windows

---

### Post by Hippytaff on 2010-10-20
Doesn't look like windows is there apart from on the optical disc!? :-s

---

### Post by SuaSwe on 2010-10-20
Looks the same as mine does with Windows mounted (when not mounted it doesn't appear in df at all). 

Am I the only one who thinks it looks like it's just the boot loader that's f00ked, seeing as Windows is accessible from Ubuntu? Did you use GRUB before, Ymurti? You should be able to reinstall it using a LiveCD, I believe, by just going through the install **without formatting** any of the drives and just opting for "boot loader" at the end. Anyone else, suggestions/thoughts?

---

### Post by kansasnoob on 2010-10-20
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

I'll check back later.

---

### Post by Ymurti on 2010-10-20
> **kansasnoob said:**
> Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

I'll check back later.
Here it is the result:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    11,266,047    11,264,000   7 HPFS/NTFS
/dev/sda2          11,266,048   222,203,547   210,937,500   7 HPFS/NTFS
/dev/sda3         222,211,080   354,835,151   132,624,072  83 Linux
/dev/sda4         354,836,478   488,396,799   133,560,322   5 Extended
/dev/sda5         354,836,480   482,859,007   128,022,528  83 Linux
/dev/sda6         482,861,056   488,396,799     5,535,744  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B929-9173                              vfat                                     
/dev/sda2        DC020768020746CC                       ntfs       Windows                       
/dev/sda3        8613c2b5-f911-4bf0-8f3b-b76fdb8ee7a8   ext2       Y                             
/dev/sda4: PTTYPE="dos" 
/dev/sda5        36fdb8d9-322e-47b7-ac57-cfc851877835   ext4                                     
/dev/sda6        8b4d3866-b11a-42b2-a32c-70d6fff32694   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835
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
	search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=36fdb8d9-322e-47b7-ac57-cfc851877835 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=36fdb8d9-322e-47b7-ac57-cfc851877835 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=36fdb8d9-322e-47b7-ac57-cfc851877835 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=36fdb8d9-322e-47b7-ac57-cfc851877835 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=36fdb8d9-322e-47b7-ac57-cfc851877835 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8b4d3866-b11a-42b2-a32c-70d6fff32694 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 235.5GB: boot/grub/core.img
 245.6GB: boot/grub/grub.cfg
 182.5GB: boot/initrd.img-2.6.32-25-generic
 194.4GB: boot/initrd.img-2.6.35-22-generic
 237.1GB: boot/vmlinuz-2.6.32-25-generic
 237.1GB: boot/vmlinuz-2.6.35-22-generic
 194.4GB: initrd.img
 182.5GB: initrd.img.old
 237.1GB: vmlinuz
 237.1GB: vmlinuz.old

---

### Post by oldfred on 2010-10-21
Your boot flag is on sda1, and it would require these two files to boot.
 Boot files/dirs:   [COLOR=Red]/bootmgr /Boot/BCD[/COLOR] 

But you do not have them in sda1. Did you delete another install of windows?  Often with separate boot partitions do not repair correctly. You may have to move boot flag to sda2 and run the windows repairs on that partition.

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

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by kansasnoob on 2010-10-21
Thanks olfred :)

---

### Post by Ymurti on 2010-10-22
> **oldfred said:**
> Your boot flag is on sda1, and it would require these two files to boot.
 Boot files/dirs:   [COLOR=Red]/bootmgr /Boot/BCD[/COLOR] 

But you do not have them in sda1. Did you delete another install of windows?  Often with separate boot partitions do not repair correctly. You may have to move boot flag to sda2 and run the windows repairs on that partition.

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

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Dear OldFred,

Thank you for your support.

I downloaded de iso and I tryed the repair CD and it is working. But I could not repair yet. I have one doubt. You told me to select the command prompt (console) and type in the following commands:

BootRec.exe /fixmbr #updates MBR master boot record do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

Question: Do I type everything and then press enter or should I type line by line pressing enter at the end of every line?

---

### Post by Mark Phelps on 2010-10-22
You type in the commands one at a time -- and type only the command.

This consists of the word on the left followed by one or more parms -- indicated by the slash "/".

The remainder of the commands are comments -- don't type them in.

And generally, the advice on the Windows 7 forum is to run Startup Repair three times, since that does the same thing and prevents mistakes from mistyping commands or their parms.

---

### Post by Ymurti on 2010-10-23
Dear oldfred and kansasnoob, Th.ank You very much for your support

I opened the command prompt and typed the commands.

The first one I did not typed as I want grub. 

BootRec.exe /fixmbr #updates MBR master boot record do not run if you still want grub

The second, third and fourth was successful,
  
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot #updates PBR partition boot sector
BootRec.exe /ScanOs

But from the last command,

BootRec.exe /RebuildBcd

I got the following:

Successfully scanned Windows installations.
Add installation to boot list?  Y
The file or directory is corrupted and unreadble.


What should I do next?

---

### Post by oldfred on 2010-10-23
Did the chkdsk run and you have to run chkdsk until there are no errors as it does not fix everything on one pass.

Run chkdsk several times, until no more errors are detected.
Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by Ymurti on 2010-10-24
> **oldfred said:**
> Did the chkdsk run and you have to run chkdsk until there are no errors as it does not fix everything on one pass.

Run chkdsk several times, until no more errors are detected.
Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
Dear Oldfred, 

I did as you told me but now I can not boot neither Windows or Ubuntu. When I power on my netbook I see this message:  
"Windows failed to start.   A recente hardware or software change might be the cause.
Status OXc000000e
info: The boot selection failed because a required device is inacessible."

 Please help!!! I am writing from an Internet Cafe!!!!
Bear in mind that I am an Absolute Beginner when you give some instructions.

---

### Post by oldfred on 2010-10-24
If you ran this:
BootRec.exe /fixmbr

then it put the windows boot loader in the MBR so it is trying to boot windows. And if the rest of the repairs did not repair windows then that is why you cannot boot at all. Did you move boot flag to sda2.

Use the Ubuntu liveCD to reinstall grub and in gparted to move the boot flag to sda2, click on partition and manage flags. 

To reinstall grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

### Post by Ymurti on 2010-10-25
I installed grub. 
But now when I turn on my netbook comes a terminal as follows:

GNU Grub Version 1.98-1ubuntu5

Minimal bash- like line editing is supported.

grub>


What to do next?

---

### Post by Ymurti on 2010-10-25
I run this command  "sudo fdisk -l"  again and got a different result from before:

ubuntu@ubuntu:~$ sudo fdisk -l



Disk /dev/sda: 250.1 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk identifier: 0x12e2e7b4



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1         702     5632000    7  HPFS/NTFS

Partition 1 does not end on cylinder boundary.

/dev/sda2             702       13832   105468750    7  HPFS/NTFS

/dev/sda3           13833       22088    66312036   83  Linux

/dev/sda4           22088       30402    66780161    5  Extended

/dev/sda5           22088       30057    64011264   83  Linux

/dev/sda6           30057       30402     2767872   82  Linux swap / Solaris



Obs.: I used the Ubuntu CD and opened a terminal

---

### Post by arju305 on 2010-10-25
> **Ymurti said:**
> Dear linux-hack,

I updated grub and now the option to boot in Windows 7 is not there anymore???

How do I find out my partition scheme??? Sorry I am a begginer

hi ymurti,
in termina try:
sudo os-prober
do u see:
:Windows 7 (loader):Windows:chain
 this type of output........
if u dont then i think u may have serious problem with your windows 7

do u see c:\ from your linux machine normal.............

---

### Post by Hippytaff on 2010-10-25
try this could try [http://ubuntuforums.org/showthread.php?t=1604123](http://ubuntuforums.org/showthread.php?t=1604123) post #2

fdisk -l should list partitions (might need to do sudo before, as I just discovered)

---

### Post by oldfred on 2010-10-25
How is your fdisk different? It still has the same partitions as shown in the boot info script.  Boot script output is the same as sudo fdisk -lu, so it outputs in sectors.

I see you have not even moved the boot flag so you can repair windows in sda2.

---

### Post by Ymurti on 2010-10-26
Please how to repair Grub? 


I installed grub. 
But now when I turn on my netbook comes a terminal as follows:

GNU Grub Version 1.98-1ubuntu5

Minimal bash- like line editing is supported.

grub>


What to do next?

---

### Post by aytech on 2010-10-26
Try reinstalling it: 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Ymurti on 2010-10-26
> **aytech said:**
> Try reinstalling it: 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
I reinstalled the Grub2 and when I restarted my net-book the same thing again:

GNU Grub Version 1.98-1ubuntu5

Minimal bash- like line editing is supported.

grub>


What to do next?????

---

### Post by Mark Phelps on 2010-10-26
Hacking around with one thing after another is only going to make the situation worse. You should stop doing everything that everyone posts.

The poster "oldfred" is a seasoned expert around here.  I would trust anything he says -- and do what HE says, not what the others tell you.

---

### Post by oldfred on 2010-10-26
Thanks for the support Mark but oldfred is not always right. I prefer to have many eyes on any problems and collectively we usually manage to solve them. Sometimes some advice is better than others.

If the simple two line grub reinstall does not work then the full chroot as explained by drs305 is the best choice to reinstall grub.

chroot & grub uninstall & reinstall drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Ymurti on 2010-10-27
> **oldfred said:**
> Thanks for the support Mark but oldfred is not always right. I prefer to have many eyes on any problems and collectively we usually manage to solve them. Sometimes some advice is better than others.

If the simple two line grub reinstall does not work then the full chroot as explained by drs305 is the best choice to reinstall grub.

chroot & grub uninstall & reinstall drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Dear Oldfred, 

Maybe I should call you Wisefred :)

Thank you for your patience with me.


As for your instructions I ran meierfra's boot info script and here it is the result. As I am a beginner please read it and tell me if I should continue with the instructions that you gave in the article: &#8220;Howto: Purge and Reinstall Grub 2 from the Live CD&#8221; .

Obs. I ran the command: sudo mount /dev/sdXY   for all the partitions separately and in the partition sda2 I got  this:  Inode is corrupt (9): Input/output error 

                Boot Info Script 0.55    dated February 15th, 2010                    



============================= Boot Info Summary: ==============================



 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 

    partition #3 for /boot/grub.

 => No boot loader is installed in the MBR of /dev/sdb



sda1: _________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows Vista/7

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  

    Boot files/dirs:   



sda2: _________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows Vista/7

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  

    Boot files/dirs:   



sda3: _________________________________________________________________________



    File system:       ext2

    Boot sector type:  -

    Boot sector info:  

    Operating System:  

    Boot files/dirs:   /boot/grub/core.img



sda4: _________________________________________________________________________



    File system:       Extended Partition

    Boot sector type:  -

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



    File system:       vfat

    Boot sector type:  -

    Boot sector info:  According to the info in the boot sector, sdb1 starts 

                       at sector 0. But according to the info from fdisk, 

                       sdb1 starts at sector 15.

    Operating System:  

    Boot files/dirs:   



=========================== Drive/Partition Info: =============================



Drive: sda ___________________ _____________________________________________________



Disk /dev/sda: 250.1 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors

Units = sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes



Partition  Boot         Start           End          Size  Id System



/dev/sda1    *          2,048    11,266,047    11,264,000   7 HPFS/NTFS

/dev/sda2          11,266,048   222,203,547   210,937,500   7 HPFS/NTFS

/dev/sda3         222,211,080   354,835,151   132,624,072  83 Linux

/dev/sda4         354,836,478   488,396,799   133,560,322   5 Extended

/dev/sda5         354,836,480   482,859,007   128,022,528  83 Linux

/dev/sda6         482,861,056   488,396,799     5,535,744  82 Linux swap / Solaris





Drive: sdb ___________________ _____________________________________________________



Disk /dev/sdb: 502 MB, 502923264 bytes

8 heads, 32 sectors/track, 3837 cylinders, total 982272 sectors

Units = sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes



Partition  Boot         Start           End          Size  Id System



/dev/sdb1    *             15       982,271       982,257   6 FAT16





blkid -c /dev/null: ____________________________________________________________



Device           UUID                                   TYPE       LABEL                         



/dev/loop0                                              squashfs                                 

/dev/sda1        FA9205319204F3C3                       ntfs       System                        

/dev/sda2        DC020768020746CC                       ntfs       Windows                       

/dev/sda3        8613c2b5-f911-4bf0-8f3b-b76fdb8ee7a8   ext2       Y                             

/dev/sda4: PTTYPE="dos" 

/dev/sda5        36fdb8d9-322e-47b7-ac57-cfc851877835   ext4                                     

/dev/sda6        8b4d3866-b11a-42b2-a32c-70d6fff32694   swap                                     

/dev/sda: PTTYPE="dos" 

/dev/sdb1                                               vfat                                     

/dev/sdb: PTTYPE="dos" 



============================ "mount | grep ^/dev  output: ===========================



Device           Mount_Point              Type       Options



aufs             /                        aufs       (rw)

/dev/sr0         /cdrom                   iso9660    (ro,noatime)

/dev/loop0       /rofs                    squashfs   (ro,noatime)

/dev/sda1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)

/dev/sda2        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)

/dev/sdb1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)





=================== sda3: Location of files loaded by Grub: ===================





 129.5GB: boot/grub/core.img



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

search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835

if loadfont /usr/share/grub/unicode.pf2 ; then

  set gfxmode=640x480

  load_video

  insmod gfxterm

fi

terminal_output gfxterm

insmod part_msdos

insmod ext2

set root='(hd0,msdos5)'

search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835

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

	search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835

	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=36fdb8d9-322e-47b7-ac57-cfc851877835 ro   quiet splash

	initrd	/boot/initrd.img-2.6.35-22-generic

}

menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {

	recordfail

	insmod part_msdos

	insmod ext2

	set root='(hd0,msdos5)'

	search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835

	echo	'Loading Linux 2.6.35-22-generic ...'

	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=36fdb8d9-322e-47b7-ac57-cfc851877835 ro single 

	echo	'Loading initial ramdisk ...'

	initrd	/boot/initrd.img-2.6.35-22-generic

}

menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {

	recordfail

	insmod part_msdos

	insmod ext2

	set root='(hd0,msdos5)'

	search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835

	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=36fdb8d9-322e-47b7-ac57-cfc851877835 ro   quiet splash

	initrd	/boot/initrd.img-2.6.32-25-generic

}

menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {

	recordfail

	insmod part_msdos

	insmod ext2

	set root='(hd0,msdos5)'

	search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835

	echo	'Loading Linux 2.6.32-25-generic ...'

	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=36fdb8d9-322e-47b7-ac57-cfc851877835 ro single 

	echo	'Loading initial ramdisk ...'

	initrd	/boot/initrd.img-2.6.32-25-generic

}

### END /etc/grub.d/10_linux ###



### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###



### BEGIN /etc/grub.d/20_memtest86+ ###

menuentry "Memory test (memtest86+)" {

	insmod part_msdos

	insmod ext2

	set root='(hd0,msdos5)'

	search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835

	linux16	/boot/memtest86+.bin

}

menuentry "Memory test (memtest86+, serial console 115200)" {

	insmod part_msdos

	insmod ext2

	set root='(hd0,msdos5)'

	search --no-floppy --fs-uuid --set 36fdb8d9-322e-47b7-ac57-cfc851877835

	linux16	/boot/memtest86+.bin console=ttyS0,115200n8

}

### END /etc/grub.d/20_memtest86+ ###



### BEGIN /etc/grub.d/30_os-prober ###

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

UUID=36fdb8d9-322e-47b7-ac57-cfc851877835 /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda6 during installation

UUID=8b4d3866-b11a-42b2-a32c-70d6fff32694 none            swap    sw              0       0



=================== sda5: Location of files loaded by Grub: ===================





 235.5GB: boot/grub/core.img

 245.6GB: boot/grub/grub.cfg

 182.5GB: boot/initrd.img-2.6.32-25-generic

 194.4GB: boot/initrd.img-2.6.35-22-generic

 237.1GB: boot/vmlinuz-2.6.32-25-generic

 237.1GB: boot/vmlinuz-2.6.35-22-generic

 194.4GB: initrd.img

 182.5GB: initrd.img.old

 237.1GB: vmlinuz

 237.1GB: vmlinuz.old

---

### Post by oldfred on 2010-10-27
When you post terrminal output or results.txt please use the code tags, which you add by highlighting the text with the cursor and then click on the # in the menu above on the right side of the menu. That preserves formating and makes it a lot easier to read.

It looks like we are going backwards. You have still not moved boot flag to sda2 so windows cannot repair it. You use gparted from liveCD and click on sda2, manage flags.

You now seem to be missing from sda2 which was in your first run of the  boot script:
Boot files/dirs:   /Windows/System32/winload.exe

I am not sure now if the windows is repairable as it looks like you somehow deleted it, if winload.exe is missing. Please check if windows folders are still in sda2.

Have you run chkdsk on sda2 until it had no errors?
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)


If the errors on on ext partitions (not NTFS) then you need a Ubuntu liveCD and run this - replace sdb1 in example with partition with error:
From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Mark Phelps on 2010-10-27
> **oldfred said:**
> Thanks for the support Mark but oldfred is not always right. I prefer to have many eyes on any problems and collectively we usually manage to solve them. Sometimes some advice is better than others.

Hey ... I'm not always right, either.  But it's generally better to follow the advice of one experience person rather than panicking and just doing everything that everyone suggests.

Just trying to get the OP to focus on the suggestions you were providing.

Sorry if I intruded.

---


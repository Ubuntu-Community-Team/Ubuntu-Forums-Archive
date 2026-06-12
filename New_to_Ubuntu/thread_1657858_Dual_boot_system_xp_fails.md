---
title: "Dual boot system xp fails"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by safeside on 2011-01-01
I have Ubuntu 10.10 on a harddrive and Xp on a seperate harddrive.  Grub2 installed and both systems worked until, last night.  I have Ubuntu, it loads fine, but the XP doesn't boot/load.  It goes to a black screen.  I have had this problem in the past, and solved it by re-installing both systems.  There has to be a better way.  I have just downloaded  the boot.info file, just not used it, yet.  I have used supergrub without success.  This is my first post, so bear with me, I will try to provide any info needed to fix my problem.

---

### Post by Bucky Ball on 2011-01-01
Get into Ubuntu, open a terminal (Applications->Accessories->Terminal) then paste in these commands, one at a time:

```
sudo apt-get install os-prober
sudo update-grub
```

---

### Post by safeside on 2011-01-01
Thanks for the response.  I did as suggested with the following results:

#Reading state information... Done
os-prober is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 140 not upgraded.
safeside@safeside-linux:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done#

These appear to be the same/identical settings that were available yesterday.  I am not totally knowledgeable of Linux, but, I am trying to convert.  Any, and all help is appreciated.  Thanks

---

### Post by wilee-nilee on 2011-01-01
If you have the bootscript run it and post all the text in code tags.

---

### Post by safeside on 2011-01-01
It took me a little bit of time to use the script, but, I think I have it.  Not sure what the problem is, if it could be identified for me, that would help.  Otherwise, you can fix it, but I won't have the knowledge I am looking for.  If I post this incorrectly, please correct me..

#
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    74,864,639    74,862,592  83 Linux
/dev/sda2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sda5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   781,401,599   781,401,537   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        686be229-4eda-478d-a309-d06532e44c9e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2684F87084F843B9                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
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
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2684f87084f843b9
    drivemap -s (hd0) ${root}
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=686be229-4eda-478d-a309-d06532e44c9e none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  25.9GB: boot/grub/core.img
  25.9GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
  26.0GB: boot/vmlinuz-2.6.35-22-generic
   1.2GB: initrd.img
  26.0GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
#

---

### Post by wilee-nilee on 2011-01-01
So you need grub in the sda mbr and the sda 40 gig HD being first in the bios being read.

So boot a live maverick cd and run these two commands.
```
sudo mount /dev/sda1 /mnt
```
then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

reboot to that 40 gig drive then choose ubuntu and when in run in its terminal
```
sudo update-grub
```

---

### Post by ktat on 2011-01-01
when I have boot problems I use grub-mkconfig & grub-install.  Specifically, open a terminal and enter:

```
grub-mkconfig > ~/grub.cfg
```

this will create a grub configuration file in your /home directory.

Now you can compare it with the configuration file that grub is currently using...

use gedit to open the newly created grub.cfg and, in another tab, open /boot/grub/grub.cfg (this is the current file that grub uses to boot the various operating systems you have)

If they are different it may be worth giving the other one a try, here are the steps:

```
sudo mv /boot/grub/grub.cfg /boot/grub/grub.cfg.bak
sudo mv /home/grub.cfg /boot/grub/
```

The first step effectively saves your original grub.cfg, in case you wish to return to it (just delet the new one and remove the .bak from the file name)

Then reboot, if this doesn't work then I would try:
```
sudo grub-install /dev/<MBR name here eg. sda>
```

note: it is important not to specify a partition (eg. /dev/sda1) for last command.

---

### Post by Bucky Ball on 2011-01-02
Might help if you run these two commands. One at a time hitting return after each. You have 140 packages to upgrade! That might fix your probs anyhow. It is gonna help:

```
sudo apt-get update
sudo apt-get upgrade
```Good luck and let us know.

---

### Post by oldfred on 2011-01-02
Do your drives come up at different times in different order? That seems to be the issue and we have seen that before. Sometimes drive order is different between cold boot & warm (reboot) boot. Something about drives, BIOS & power. Also mixed IDE & SATA seem to be an issue sometimes.

Script shows windows in sdb at the time you ran it, but the windows boot stanza says it saw windows in sda at the time it created the windows boot stanza. Windows boot.ini also thinks it is in drive 0 or sda.

Ubuntu is forgiving about drive order as it first uses drive order, but then does a search by UUID to find partition. Windows is less forgiving and if not correct drive will often give errors.

---

### Post by safeside on 2011-01-02
:confused:
  	 	 	 	pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }  400 gig ATA hard drive (sda1-xp) primary boot the 40 gig IDE (Ubuntu), the drives are set in bios as such.  I used  
 Code:
 sudo apt-get update sudo apt-get upgrade 

 The results were, I got upgraded/updated but still unable to boot XP.  My grub2 loader works, I have the option to load XP, Ubuntu is the default loader.  Would I still need a live cd to use the advise wilee-nilee gave?   
 

 Many thanks again

---

### Post by oldfred on 2011-01-02
Did you install grub to sda the 40GB drive?

If windows still does not boot I would try using the XP CD to repair windows. It is often better to have windows as sda, but it should work as sdb. Your boot.ini still thinks windows is drive 0 or sda when it is sdb. 

these commands should update the windows, if you run fixMBR it may write to sda or sdb, not sure how windows does it when it is sdb??

[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)

FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini

---

### Post by safeside on 2011-01-02
The saga continues, I disconnected the 40 gig hd and the 400 gig would not boot, I received a
 "no such device "
"grub rescue"

Reconnected the 40 gig hd, it loaded the grub, I examined it and found the following:

Ubuntu set root hd1
XP set root hd0

It would also appear, I cannot paste from officeorg.. lesson learned.

---

### Post by oldfred on 2011-01-02
Which drive is sda? Not sure what you did?

If you want you should install a windows boot loader to the windows drive. then if you disconnect the Ubuntu drive windows will boot.

Not sure which drive is windows drive, now but you want this in the 400GB drive. And keep grub in the 40GB drive. Change sda to sdb if still like boot script results originally posted.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/[COLOR=Red]sda[/COLOR] mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

If you have reversed drive boot order by changing SATA ports or BIOS run this in Ubuntu
sudo update-grub

---

### Post by safeside on 2011-01-03
I will try to explain.  I had Windows installed on the 400 GB, then I installed Ubuntu on a 40 GB hard drive.  Both we installed as a single drive and then I added, the 400 GB, the grub identified it and the OS.  I planned on using the bios to boot from either drive, but, this seemed so simple, and it worked until, now.  

I checked the diskmanager and the 40GB is identified as sda
                                                                                                      the 400GB is identified as sdb

The 400 was/is the primary boot drive (in bios) and the 40 was/is  the secondary boot device.  To help maintain my thought process, would using lilo correct this or would it be better to replace the XP boot.ini?

---

### Post by oldfred on 2011-01-03
Lilo boot loader is easy to install from Ubuntu and it boots windows just fine. Otherwise you need a windows repairCd and run fixMBR.

IF windows is [COLOR=Red]sdb[/COLOR]. Check with fdisk before running:

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/[COLOR=Red]sdb[/COLOR] mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

With grub you do not need to use BIOS to choose what to boot. Grub gives you a choice. So just set the 40GB drive as the boot drive in BIOS.

It just is that some users have had issues with windows in sdb. Windows always wants to think it is first and only. Grub usually adds a drive map (grub legacy) or devicemap (grub2) command to make windows think it is first.

---

### Post by safeside on 2011-01-03
Results were less than expected.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/[COLOR=Red]sda[/COLOR] mbr
May show error messages about the rest of lilo missing, ignore, we just  want MBR

Lost all, not data, just no grub2 and no XP or Ubuntu.  I am now running Ubuntu 10.4 live CD.  I used utilities supergrub in an effort to restore XP loader..didn't work, also tried to restore grub, didn't work (I believe this is because of grub/grub 2. 

I had just upgraded my kernel

---

### Post by oldfred on 2011-01-04
Did you install lilo to the windows drive (but whichever fdisk says is the 400GB drive), not sda unless you have swtiched drives? Then in BIOS, if you boot the 400GB drive, you should get windows. 

Then for sda the Ubuntu drive (the 40GB drive) you should reinstall grub2.

---

### Post by safeside on 2011-01-04
I have reinstalled grub2 and my Ubuntu is back and functional.  I am now back to where I started from, with the exception, that XP doesn't load.  I did however find a NTLDR missing error, which would be a XP problem.  I am provided with a minimal bash (?) grub command line.

Which would be the better of the two choices, having the grub on the Ubuntu drive and making it the primary boot. Or, having the XP drive the primary drive?

Aren't these computers, great toys?

---

### Post by oldfred on 2011-01-04
I would boot from BIOS the grub/Ubuntu drive as it lets you choose Ubuntu or windows. Only if you have issues with Ubuntu then you could directly boot windows from BIOS or one time boot key.

File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

The boot script showed you have a ntldr?? 

Is the error from directly booting the windows drive or from grub chainloading to the windows partition? Or both?

---

### Post by safeside on 2011-01-04
If I use the Ubuntu drive to boot from bios, I receive the grub2 menu, if I select the windows boot option--the screen goes black, no splash, no cursor.  All of the other selections work, fine.

If I use the XP drive to boot from bios, I now receive the minimal bash command.

I have downloaded a windows ultimate boot cd, which might (?) fix the problem.

---

### Post by oldfred on 2011-01-04
You can repair all of XP from Ubuntu except running chkdsk. To run chkdsk you need the XP install disk, but can use (only for chkdsk) Vista or 7 repair disks as the NTFS is still NTFS. 

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\.

---

### Post by safeside on 2011-01-04
Yes I can now boot into grub2 and load Ubuntu 10.10.  I copied the two files into the 400GB drive from Ubuntu, then I shut down the pc and started again.  The grub2 menu loaded, I selected the Windows Xp... the screen returned to black, no cursor and no spash screen.  I do not have a hard drive indicator light, but I do not hear it running, so I do not think it is accessing the drive.

---

### Post by oldfred on 2011-01-04
If you have installed lilo or the windows bootloader to the 40GB drive and you boot it directly with BIOS or one time boot key does it boot or does it give the same error?

---

### Post by safeside on 2011-01-05
I was getting confused with which drive is which.  At this time, the bios is set to boot from 40gb (which has Ubuntu) and then the 400gb (which has XP)

I can boot from the 40gb  (Ubuntu) which gives me the grub2 menu, the only selection that doesn't work is XP, that is what I am trying to fix/correct.

I changed the bios boot order (testing only), the 400gb (windows) gave me the minimal bash command line.
**I returned the bios back to 40 gb 1st, 400gb 2nd**

Since 3 or 4 pages have past, and I have tried suggestions, should I run another boot script?  I am sure that the system has changed since the beginning of this thread.

---

### Post by oldfred on 2011-01-05
Sure another copy of boot script will help see where we are now.  If you have a windows boot loader in the 400GB drive and it does not directly boot from BIOS nor from grub's entry then we have windows boot issues that need to be repaired.

Did you run all the windows repair commands from post #21? Those just about always work to fix XP issues. You could try them again, test booting & if not working rerun the boot script. Note that it will create a results1 or results2 and post the newest update it runs.

---

### Post by safeside on 2011-01-05
I copied the ntldr and ndetect files into the drive, the results were-no change.  I tried to use the XP install CD, but never got an option to use Recovery.  I have ran another boot script, to determine, where I am.     


         Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    74,864,639    74,862,592  83 Linux
/dev/sda2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sda5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   781,401,599   781,401,537   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        686be229-4eda-478d-a309-d06532e44c9e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2684F87084F843B9                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2684f87084f843b9
    drivemap -s (hd0) ${root}
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=686be229-4eda-478d-a309-d06532e44c9e none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  25.9GB: boot/grub/core.img
   4.6GB: boot/grub/grub.cfg
   1.3GB: boot/initrd.img-2.6.35-22-generic
   1.3GB: boot/initrd.img-2.6.35-24-generic
  26.0GB: boot/vmlinuz-2.6.35-22-generic
  26.0GB: boot/vmlinuz-2.6.35-24-generic
   1.3GB: initrd.img
   1.3GB: initrd.img.old
  26.0GB: vmlinuz
  26.0GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by oldfred on 2011-01-06
Could you please post in code tags, It is a lot easier to review and retains formating. It is the # in edit menu above on a new post. Highlight code and click on #. You can manually goes back and add them, but have to type [code ] before & [/code ] after but leave out spaces. If I did not have spaces you would not see text.

You now have two ntldrs and part of grub. Delete on ntldr and the /boot folder.

sdb1: _________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini [COLOR=Red]/ntldr /NTLDR[/COLOR] /NTDETECT.COM
[COLOR=Red]/boot/grub/core.img[/COLOR]

Then see if the windows repairs will run.

---

### Post by Bucky Ball on 2011-01-06
> **oldfred said:**
> Could you please post in code tags, It is a lot easier to review and retains formating. It is the # in edit menu above on a new post. Highlight code and click on #. You can manually goes back and add them, but have to type [code ] before & [/code ] after but leave out spaces. If I did not have spaces you would not see text.

You now have two ntldrs and part of grub. Delete on ntldr and the /boot folder.

sdb1: _________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini [COLOR=Red]/ntldr /NTLDR[/COLOR] /NTDETECT.COM
[COLOR=Red]/boot/grub/core.img[/COLOR]

Then see if the windows repairs will run.

Nicely picked, Fred, but the #  is only available when you click "Go Advanced" when posting on an existitng thread (starting a new thread then you are already in advanced). Otherwise you need to manually type the code tags. ;)

---

### Post by oldfred on 2011-01-06
I have never used the go advanced & will have to try that. I thought once you had posted, you had to manually type the code tags.
```

Go advanced does give full edit panel at top.
```

---

### Post by safeside on 2011-01-12
My apology, I couldn't take it any more.  I reformatted the 400gb and reinstalled XP, I am in the process of rebuilding all of the missing programs.  I have changed the bios to boot from either drive.  If the 40g (Ubuntu drive) boots, the grub loads, however it does not load the XP selection.  If the 400g (XP drive) boots, it does so correctly.  I have enjoyed the grub2 loader and would like to continue to use the 40g as the primary bios boot device  I have gained some knowledge and would like to thank everyone who has helped me.  If this would shed any light on my current situation, I would appreciate it.

#
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    74,864,639    74,862,592  83 Linux
/dev/sda2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sda5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   781,401,599   781,401,537   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        686be229-4eda-478d-a309-d06532e44c9e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7CB4B3F0B4B3AB52                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2684f87084f843b9
    drivemap -s (hd0) ${root}
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=686be229-4eda-478d-a309-d06532e44c9e none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  25.9GB: boot/grub/core.img
   4.6GB: boot/grub/grub.cfg
   1.3GB: boot/initrd.img-2.6.35-22-generic
   1.3GB: boot/initrd.img-2.6.35-24-generic
  26.0GB: boot/vmlinuz-2.6.35-22-generic
  26.0GB: boot/vmlinuz-2.6.35-24-generic
   1.3GB: initrd.img
   1.3GB: initrd.img.old
  26.0GB: vmlinuz
  26.0GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
#

---

### Post by oldfred on 2011-01-13
The results.txt lists the 40GB as sda and the 400GB as sdb with the windows install. But the way you installed windows it thinks it is drive 0 and the grub.cfg has Ubuntu in hd1. Grub will still work since it also does the search by UUID. Or everything is reversed.

It would just greatly simplify things if you reversed drives. If both are SATA or PATA reverse connections. Not sure if you can just change order in BIOS and it sees it that way or not.

Most users have windows as sda as it was the first system installed or on the first drive. So that works. Some users like you with windows on sdb seem to have problems, but I have seen it work, so I do not know why a difference.

---

### Post by Chazz44able on 2011-01-13
```

> **safeside said:**
> I copied the ntldr and ndetect files into the drive, the results were-no change.  I tried to use the XP install CD, but never got an option to use Recovery.  I have ran another boot script, to determine, where I am.     


         Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    74,864,639    74,862,592  83 Linux
/dev/sda2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sda5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   781,401,599   781,401,537   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        686be229-4eda-478d-a309-d06532e44c9e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2684F87084F843B9                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2684f87084f843b9
    drivemap -s (hd0) ${root}
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=b6a4a73e-fff3-4b7e-b9ac-b67a04a2601b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=686be229-4eda-478d-a309-d06532e44c9e none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  25.9GB: boot/grub/core.img
   4.6GB: boot/grub/grub.cfg
   1.3GB: boot/initrd.img-2.6.35-22-generic
   1.3GB: boot/initrd.img-2.6.35-24-generic
  26.0GB: boot/vmlinuz-2.6.35-22-generic
  26.0GB: boot/vmlinuz-2.6.35-24-generic
   1.3GB: initrd.img
   1.3GB: initrd.img.old
  26.0GB: vmlinuz
  26.0GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

```
Please use code tags

---

### Post by safeside on 2011-01-13
Yesterday, I had the bios set to start with either system.  I updated the Ubuntu last night.  Today... I can start the XP, using the bios, however, I can not start Ubuntu, even if I change the bios and make it the primary boot device.  I am posting this using live CD, I am now unable to start the Ubuntu system, I have tried the supergrub utility disc.  If by chance, I have downloaded an update that my system doesn't like, or if I have just confused the entire system.

---

### Post by oldfred on 2011-01-13
Is the 40GB drive IDE and the 400GB drive SATA? We have seen a few users where the drives booted with different order depending on how booted or if cold boot vs. warm boot, or even at random.

But Ubuntu should boot anyway as even if hd1 is wrong it then searches on UUID to find boot partition.

Did you try reinstalling grub2 to MBR from liveCD?

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

#Comments are anything after the #, enter commands in terminal session - Double check that install is in sdb1 not sda1 from liveCD. If it sees drive as sda then change all sdb to sda.
#Install MBR from LiveCD, Ubuntu install on sdb1 and want grub2 in drive sdb's MBR:
#Find linux partition, change sdb1 if not correct:
sudo fdisk -l
#confirm that linux is sdb1
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb
# After rebooting into working system
sudo update-grub

to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
sudo debconf-show grub-pc

---

### Post by safeside on 2011-01-13
I loaded live cd, I followed the thread and input as directed.  It said it was a "bad idea" (the bash),   Is this line the problem ```

```sudo grub-install --root-directory=/mnt/ /dev/sda```

```, I typed it exactly as shown, I am guessing that   root-directory is not what I should have entered?

Sorry about the lack of code on the other postings, I am a newbie, just trying to learn.

---

### Post by oldfred on 2011-01-14
The "BAD IDEA" is a typo. You tried to install to a partition.

Partition are sda1, sda2 etc with number of partition at end. The drives are sda, sdb etc where the letter is the drive number.

You have to install to sda not sda1.

It is better to copy & paste commands to avoid the typos. Even spaces are important.

---

### Post by safeside on 2011-01-14
I have to admit, I gave up.  It seemed that there should have been a method to correct the initial problem.  I tried to use the advise and guidance, but, finally, I reinstalled XP, then today, I reinstalled Ubuntu.  The grub2 loader works with both systems, which is what I had prior to starting this.  Having said that, I appreciate everyone's time and advice/guidance.  I am not sure, if this thread should be marked "solved" or end it as "resolved"

Thanks

---

### Post by Bucky Ball on 2011-01-17
'Solved' so people can direct their attention to other threads or come here to see how you solved it.

Adding 'Resolved' to 'Thread Tools' is not a bad idea ...

---


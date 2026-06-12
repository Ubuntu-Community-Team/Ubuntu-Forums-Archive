---
title: "Dual Boot Problems"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by Strychnine213 on 2010-11-21
First off, I am new to Linux as a whole, so please bare with me. I downloaded Ubuntu 10 today. I have Windows 7 64bit on a separate hard drive. I had planned on dual booting Windows 7 and Ubuntu; each from a separate drive. When I intstalled Unbuntu I unplugged my Windows 7 drive as to not screw it up; I then installed Ubuntu on a separate drive. When I restart my computer I don't get a GRUB menu by default. I hold shift and it brings up the menu but Windows 7 doesn't show up does anyone know how to add windows 7?

P.S. It boots into Ubuntu by default

Thanks,
Strych

---

### Post by Quackers on 2010-11-21
Welcome to UF :-)
From your Ubuntu installation (and with the Windows drive plugged in) open up a terminal (Applications menu > Accessories > Terminal) and type in or copy/paste in ```
sudo update-grub
``` and press enter and when required enter your password.
Then watch the terminal screen as grub.cfg is configured to see if the Windows loader is picked up.If it is you could then reboot and see if the grub menu appears with Windows as an option. Select Windows and see if it boots up.

---

### Post by Strychnine213 on 2010-11-21
When I run that command in terminal I receive: 

strychnine213@Strychnine:~$ sudo update-grub
[sudo] password for strychnine213: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
strychnine213@Strychnine:~$ 
  



When I restarted my PC I had to press shift for the menu to pop up and Windows 7 was not in the list. I had:
Ubuntu and Memtest86.

---

### Post by wilee-nilee on 2010-11-21
Click on the boot script link in my sig, and follow the instructions. Come back to the thread and open a reply and click on the # and paste the text from the generated file in between. If you hit the quick reply I think you have to hit the advanced button or just look at my sig it shows the code tag placement. 

This will give the duck in the pond across the pond from me something to work with.;)

---

### Post by sandyd on 2010-11-21
When grub is first installed, it creates a list of hard drives on the computer. When grub scans for operating systems, it scans according to that list.

Because the hard drive was not inserted during the installation of grub, the hard disk that holds windows 7 is not on that list.

You will have to install grub onto whatever drive/partition it shows grub to be on in the boot info script in order for the windows 7 drive to be added.

---

### Post by Strychnine213 on 2010-11-21
```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

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
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   299,730,943   299,728,896  83 Linux
/dev/sda2         299,732,990   312,498,175    12,765,186   5 Extended
/dev/sda5         299,732,992   312,498,175    12,765,184  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   312,496,379   312,496,317   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        f2badc1c-ec33-4759-9b87-e9ef0352f9dc   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ce4be16d-d3d1-4349-8147-bf1f2c0c8845   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0612B2C412B2B84F                       ntfs       Windows x64                   
/dev/sdb: PTTYPE="dos" 

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f2badc1c-ec33-4759-9b87-e9ef0352f9dc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f2badc1c-ec33-4759-9b87-e9ef0352f9dc
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f2badc1c-ec33-4759-9b87-e9ef0352f9dc
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f2badc1c-ec33-4759-9b87-e9ef0352f9dc ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f2badc1c-ec33-4759-9b87-e9ef0352f9dc
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f2badc1c-ec33-4759-9b87-e9ef0352f9dc ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f2badc1c-ec33-4759-9b87-e9ef0352f9dc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f2badc1c-ec33-4759-9b87-e9ef0352f9dc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f2badc1c-ec33-4759-9b87-e9ef0352f9dc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ce4be16d-d3d1-4349-8147-bf1f2c0c8845 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  98.9GB: boot/grub/core.img
 126.8GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
  99.0GB: boot/vmlinuz-2.6.35-22-generic
   1.2GB: initrd.img
  99.0GB: vmlinuz
```

---

### Post by wilee-nilee on 2010-11-21
**Yours**
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe


**Mine**
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   **/bootmgr /Boot/BCD** /Windows/System32/winload.exe

You are missing what I highlighted, you must have deleted a partition that had these files.

So here is the drill from a live install W7 DVD or a recovery which a link I provide run the auto repair 3 times with the Ubuntu drive unplugged. Your just trying to get the files installed to sdb1.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section.

---

### Post by Strychnine213 on 2010-11-21
I unplugged my Ubuntu drive and ran the system repair. Every time it says that it might have worked if it didn't repair will restart. Sadly this isn't working.

---

### Post by oldfred on 2010-11-21
It may be better to plug the Ubuntu drive in so it is sdb. Windows does not like changing from drive 0 to drive 1 which it looks like will happen when you plug the Ubuntu drive back in. On my system the drives are in SATA port order but that may not be true of all systems.

Ubuntu will not particularly care that you change from sda to sdb as it first looks at hd0 but then does a search on UUID and finds correct drive. If you set BIOS to boot the Ubuntu drive in grub that will be hd0, regardless of port order. My sdc boots as hd0.

After reinstalling both drives and rebooting into Ubuntu you will need to run this to find the windows install.

```
sudo update-grub
```

---

### Post by oldfred on 2010-11-21
You have to have a windows active partition to run the repairs. In gparted, disk Utility or command line you can set boot flag (active partition). Then windows repairs should work.

Sometimes command line (even in windows) works better. Also good idea to run chkdsk.

Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

set boot flag on for sdb1 (off on others)
sudo sfdisk -A1 /dev/sdb

---

### Post by Strychnine213 on 2010-11-21
I am running checkdisk now. I will post back when it is done (Could take forever)

By the way thanks all for the help!

---

### Post by wilee-nilee on 2010-11-21
> **Strychnine213 said:**
> I am running checkdisk now. I will post back when it is done (Could take forever)

By the way thanks all for the help!

@oldfred thanks for your input I neglected to mention the bootflag on sdb1 should be there. I also rather see the commands run but some like the auto repair function better.

OP this person is a great help so carry on.;)

---

### Post by Strychnine213 on 2010-11-21
Yea I saw the post he linked; looks like everything got solved so I am going on his word ;). The only thing I don't quite understand is how do I set the boot flags?

---

### Post by wilee-nilee on 2010-11-21
> **Strychnine213 said:**
> Yea I saw the post he linked; looks like everything got solved so I am going on his word ;). The only thing I don't quite understand is how do I set the boot flags?

The easiest way to put that boot flag is using gparted in Ubuntu. Make sure the sdb1 is not mounted then right click on it in gparted then manage flags then click on the boot flag. If you do this from the installed Ubuntu you may need to install gparted, so in the terminal run
```
sudo apt-get install gparted
```

gparted will then be in the menu admin area. Of course if the boot flag was put there by testdisk or another process , which would be unusual then your set if your able to boot to W7 from grub.

Don't forget the sudo update-grub in Ubuntu to load W7 to grub.

---

### Post by Strychnine213 on 2010-11-21
OK. I will give that a try after checkdisk is done. I am at 47% :/

---

### Post by wilee-nilee on 2010-11-21
> **Strychnine213 said:**
> OK. I will give that a try after checkdisk is done. I am at 47% :/

There will be others on line besides oldfred and myself soon so were all rooting for a safe working system. Now where did that person in the pond go;)

---

### Post by Strychnine213 on 2010-11-21
OK, here are the results for checkdisk. I think I got one error: "Failed to transfer logged messages to the vent log with status 50'

EDIT:
-BootRec /fixmbr <- The operation completed successfully
]
 BootRec.exe /FixBoot <-The volume does not contain a recongized file system. Please make sure that all required file system drivers are loaded and that the...

BootRec.exe /ScanOs<- SUccessfully scanned Windows installations. Total identifided WIndows installations: 1 C:\Windows - The operations completed successfully

BootRec.exe /RebuildBcd <- Successfully scanned WIndows installations. C:\Windows. Add installation to boot list? Y....The volume does not contain a recognised file system. Please make sure all drivers are loaded and that the volume is not corrupt

---

### Post by wilee-nilee on 2010-11-21
> **Strychnine213 said:**
> OK, here are the results for checkdisk. I think I got one error: "Failed to transfer logged messages to the vent log with status 50'

I'm just not familiar with testdisk other then suggesting its use in specific areas I know works. 

So besides that error, whats going on, have you tried to set the flag and boot into Ubuntu and run the sudo update-grub.

It may be that since the bootflag was not set when you ran the repairs that it didn't repair it, at this point another copy of the bootscript would be helpful.

---

### Post by Strychnine213 on 2010-11-21
I wish I could give you another log. I went to restart and it appears that it has now wiped my Ubuntu drive. I get a "Missing operations system" error

---

### Post by wilee-nilee on 2010-11-21
> **Strychnine213 said:**
> I wish I could give you another log. I went to restart and it appears that it has now wiped my Ubuntu drive. I get a "Missing operations system" error

Use a live Ubuntu cd or a Thumb loaded with Ubuntu, at this time lets not use the HD in the computer or the external if something has happened we want to stay off using them, to see if a recovery is possible. A live cd or thumb booted will not access the HD

---

### Post by Strychnine213 on 2010-11-21
I am on a thumb boot right now I am going to set the flags and shoot you a log

---

### Post by Strychnine213 on 2010-11-21
OK Flags have been set for boot. Here is the results:

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

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
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   299,730,943   299,728,896  83 Linux
/dev/sda2         299,732,990   312,498,175    12,765,186   5 Extended
/dev/sda5         299,732,992   312,498,175    12,765,184  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,496,379   312,496,317   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2002 MB, 2002747392 bytes
32 heads, 63 sectors/track, 1940 cylinders, total 3911616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     3,911,039     3,910,977   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        f2badc1c-ec33-4759-9b87-e9ef0352f9dc   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ce4be16d-d3d1-4349-8147-bf1f2c0c8845   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0612B2C412B2B84F                       ntfs       Windows x64                   
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        0808-1760                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f2badc1c-ec33-4759-9b87-e9ef0352f9dc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f2badc1c-ec33-4759-9b87-e9ef0352f9dc
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f2badc1c-ec33-4759-9b87-e9ef0352f9dc
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f2badc1c-ec33-4759-9b87-e9ef0352f9dc ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f2badc1c-ec33-4759-9b87-e9ef0352f9dc
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f2badc1c-ec33-4759-9b87-e9ef0352f9dc ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f2badc1c-ec33-4759-9b87-e9ef0352f9dc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f2badc1c-ec33-4759-9b87-e9ef0352f9dc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f2badc1c-ec33-4759-9b87-e9ef0352f9dc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ce4be16d-d3d1-4349-8147-bf1f2c0c8845 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  98.9GB: boot/grub/core.img
 126.8GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
  99.0GB: boot/vmlinuz-2.6.35-22-generic
   1.2GB: initrd.img
  99.0GB: vmlinuz

=========================== sdc1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 01 00  |.X.SYSLINUX..@..|
00000010  02 00 02 00 00 f8 ef 00  3f 00 20 00 3f 00 00 00  |........?. .?...|
00000020  41 ad 3b 00 00 00 29 60  17 08 08 20 20 20 20 20  |A.;...)`...     |
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 cd 18  |      FAT16   ..|
00000040  fa 33 c9 8e d1 bc fc 7b  16 07 bd 78 00 c5 76 00  |.3.....{...x..v.|
00000050  1e 56 16 55 bf 22 05 89  7e 00 fa fc 31 c9 8e d1  |.V.U."..~...1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 bf 00 16 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by wilee-nilee on 2010-11-21
Ubuntu appears to still be there it wont boot correctly as the repairs done without the boot flag set on sdb1=active reset the master boot record in sda no big deal. If you look Windows is in the mbr of sda but don't worry.

I think oldfred was correct about the having Ubuntu plugged in we can reload grub to the sda MBR=master boot record after getting windows running. So if you look your still missing those boot files in sdb1, so boot the W7 disc and make sure it is seeing sdb1=C in windows, and run the auto repair three times. We then can check if windows is booting correctly by just putting sdb first to be read in the bios, or using a per-session key prompt at startup like going to bios. My per-session key prompt for this boot from menu is f12 yours may be different hard to say. 

Does this all make sense if not ask more questions before acting.

It may be that since you have W7 in the secondary drive that a command set will have to run instead of the auto repair.

---

### Post by oldfred on 2010-11-21
The fixMBR put the windows boot loader into sda which is now the Ubuntu drive, so you must of still had the Ubuntu drive still plugged in.

To get grub2 reinstalled to the Ubuntu drive. (if still sda) Change to sdb1 and sdb if Ubuntu drive is sdb. 

#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:
#Find linux partition, change sda1 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

### Post by wilee-nilee on 2010-11-21
@oldfred whew glad to see you back.;)

---

### Post by Quackers on 2010-11-22
If you follow oldfred's advice it should re-install grub to the mbr of the Ubuntu drive.
Your Windows installation is not being seen by grub because of the 2 missing boot files that willee-nillee reported earlier.
However when you are running the Windows startup repair it appears that the Ubuntu drive is the one it's looking at. To counter this I would suggest that once grub is re-installed to the mbr of your Ubuntu drive I would disconnect that drive and then boot from the Windows dvd and run startup repair up to 3 times, as the boot flag has now been corrected.
At least then, both systems should boot independently.
Then I would re-connect the Ubuntu drive and boot ubuntu, then run sudo update-grub again and see if Windows is then picked up.

I hope I'm not causing confusion! And I hope I'm not wrong :-)

---

### Post by julio_cortez on 2010-11-22
> **sandyd said:**
> Because the hard drive was not inserted during the installation of grub, the hard disk that holds windows 7 is not on that list.
I thought it was different: when I installed Windows XP (I've explained everything [in this thread]("http://ubuntuforums.org/showthread.php?t=1580912")) I installed it on a drive that wasn't there when I first installed GRUB2.

I've removed sda (that held GRUB2, and on which Ubuntu and W7 were installed) and I've attached sdb (on which I installed Windows XP), then re-attached sda and updated GRUB2.

Well, it saw (and still manages) also sdb with no problem, even if sdb was not there when I installed GRUB2 at the beginning.

---

### Post by Strychnine213 on 2010-11-22
OK sorry to sound like an idiot. The only thing I don't quite understand is 
> To get grub2 reinstalled to the Ubuntu drive. (if still sda) Change to sdb1 and sdb if Ubuntu drive is sdb. If you could explain how to do this step-by-step, Everything else is a breeze!

EDIT; Ok I tried what Quackers recommenced. I disconnected my Ubuntu drive and ran system repair. It found my C:\Windows installation and repaired it. I ran the repair 2 more times and got an error that said no errors were found. With the Ubuntu drive still disconnected I restarted my pc to see if I could boot into the Windows 7, sadly it just hangs there I see the blinking while line and it just hangs there.

---

### Post by Strychnine213 on 2010-11-22
After much work I finally got Windows 7 to not only show up in the list, but boot. All I had to do was restore the MBR on the Windows drive and update grub!

With that being said I want to thank everyone for the help. I really appropriate it:popcorn:

P.S. Now who wants to teach me how to use Linux :/ I can't seem to figure out how to install programs and such lol ;)

---

### Post by wilee-nilee on 2010-11-22
> **Strychnine213 said:**
> After much work I finally got Windows 7 to not only show up in the list, but boot. All I had to do was restore the MBR on the Windows drive and update grub!

With that being said I want to thank everyone for the help. I really appropriate it:popcorn:

P.S. Now who wants to teach me how to use Linux :/ I can't seem to figure out how to install programs and such lol ;)

You must have run the auto repair again that will restore the MS bootloader and install those missing files. Glad it is working.

As far as installing programs it is best done from synaptic IMHO, which is in the menu and will tell you what is being done and dependencies. It also has a history so if you need to know what you have done there is a record. You will probably like the rest of us use a trial and error method of learning. I would start a thread if you have a problem with any specific install.

There are multiple ways of doing installs of programs so at this point recognize this and getting a little just plain experience by using it will be helpful. Your probably not going to get a definitive answer in this area that will cover everything.;)

---

### Post by oldfred on 2010-11-22
Glad it is working. :)

I agree with wilee-nilee on using synaptic in System, Administration for adding programs. Many top level programs are also shown in Ubuntu Software Center under Applications. I only occasionally use it. Until you are familiar with all the standard apps you can install, do not download apps like you used to with windows and install separately. I started really using Ubuntu in 2006 and how only downloaded one or two .debs and have not stayed with any of them. The apps that I can download have more than suffices for me.

---

### Post by wilee-nilee on 2010-11-22
> **oldfred said:**
> Glad it is working. :)

I agree with wilee-nilee on using synaptic in System, Administration for adding programs. Many top level programs are also shown in Ubuntu Software Center under Applications. I only occasionally use it. Until you are familiar with all the standard apps you can install, do not download apps like you used to with windows and install separately. I started really using Ubuntu in 2006 and how only downloaded one or two .debs and have not stayed with any of them. The apps that I can download have more than suffices for me.

I don't use synaptic as much as I used to as I know the apt-get method, but I use it quite often. I never go near the software center as it still needs some work to be fluid.

---


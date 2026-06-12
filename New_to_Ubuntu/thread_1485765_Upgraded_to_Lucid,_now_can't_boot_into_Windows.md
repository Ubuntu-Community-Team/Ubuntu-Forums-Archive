---
title: "Upgraded to Lucid, now can't boot into Windows"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by daisybell on 2010-05-17
I was successfully dual booting Karmic and Windows 7 (although I had not booted into Windows for a couple of months).

Last week I upgraded to Lucid using the upgrade option in Update Manager; and now I cannot boot into Windows- it just reboots and goes back to the grub menu screen. The upgrade process was simple enough until it asked me where I wanted to install grub. It gave me two options, and I can't remember properly what they were. I wonder now if I installed grub to every partition. 

What did I do wrong? And how do I fix it?

---

### Post by rbaleksandar on 2010-05-17
It asked you whether you want to install the GRUB at the beginning of the hard disk or in the same partition where your Ubuntu is installed. Usually when upgrading you don't have to change anything in grub.cfg (for GRUB 2) or menu.lst (for GRUB 1) because it's just an upgrade and not a new installation. Therefore when upgrading you should NOT reinstall the GRUB because it'll overwrite your current grub.cfg or menu.lst. A question: do you see WINDOWS in your GRUB or it just boots Ubuntu? If 'yes' than what I said in the above lines is true. All you have to do is to open the configuration file of your GRUB and add WINDOWS to the list (see the GRUB documentation or one of the many HowTo-s here in the forums). :)

---

### Post by daisybell on 2010-05-17
Results from the boot info script:

```
    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 504502617 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 504502617 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 504502361 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 504502361 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
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

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden HPFS/NTFS
/dev/sda2    *     31,459,328    31,664,127       204,800   7 HPFS/NTFS
/dev/sda3          31,664,128   504,215,551   472,551,424   7 HPFS/NTFS
/dev/sda4         504,216,090   976,768,064   472,551,975   5 Extended
/dev/sda5         504,216,153   959,016,239   454,800,087  83 Linux
/dev/sda6         959,016,303   976,768,064    17,751,762  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.1 GB, 16062087168 bytes
197 heads, 36 sectors/track, 4423 cylinders, total 31371264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192    31,371,263    31,363,072   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1CC4C15CC4C138B2                       ntfs       RECOVERY                      
/dev/sda2        4614C23614C2292F                       ntfs       SYSTEM                        
/dev/sda3        ACE0C41CE0C3EB22                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        82ce0576-f7ca-44de-a29b-f13aaba96cfd   ext4                                     
/dev/sda6        3103e92b-c113-4d8e-9370-4beb84191330   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FC30-3DA9                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/FC30-3DA9         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda3        /media/ACE0C41CE0C3EB22  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 82ce0576-f7ca-44de-a29b-f13aaba96cfd
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
search --no-floppy --fs-uuid --set 82ce0576-f7ca-44de-a29b-f13aaba96cfd
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 82ce0576-f7ca-44de-a29b-f13aaba96cfd
insmod tga
if background_image /boot/grub/TulipStair_QueensHouse_Greenwich.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 82ce0576-f7ca-44de-a29b-f13aaba96cfd
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=82ce0576-f7ca-44de-a29b-f13aaba96cfd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 82ce0576-f7ca-44de-a29b-f13aaba96cfd
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=82ce0576-f7ca-44de-a29b-f13aaba96cfd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 82ce0576-f7ca-44de-a29b-f13aaba96cfd
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=82ce0576-f7ca-44de-a29b-f13aaba96cfd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 82ce0576-f7ca-44de-a29b-f13aaba96cfd
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=82ce0576-f7ca-44de-a29b-f13aaba96cfd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 82ce0576-f7ca-44de-a29b-f13aaba96cfd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 82ce0576-f7ca-44de-a29b-f13aaba96cfd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4614c23614c2292f
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=82ce0576-f7ca-44de-a29b-f13aaba96cfd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3103e92b-c113-4d8e-9370-4beb84191330 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 258.3GB: boot/grub/core.img
 266.5GB: boot/grub/grub.cfg
 259.5GB: boot/initrd.img-2.6.31-21-generic
 259.5GB: boot/initrd.img-2.6.32-22-generic
 259.5GB: boot/vmlinuz-2.6.31-21-generic
 259.5GB: boot/vmlinuz-2.6.32-22-generic
 259.5GB: initrd.img
 259.5GB: initrd.img.old
 259.5GB: vmlinuz
 259.5GB: vmlinuz.old
```

So that looks like I did install grub to every partition...

---

### Post by daisybell on 2010-05-17
> **rbaleksandar said:**
>  A question: do you see WINDOWS in your GRUB or it just boots Ubuntu? If 'yes' than what I said in the above lines is true. 

I see Windows- when I try to boot it, the whole boot process starts again (at least, I'm assuming that's what it's doing, since it goes back to the initial manufacturer's splash screen).

---

### Post by bennachie on 2010-05-17
Boot into Lucid, then open a terminal and type:

sudo update-grub

You'll be asked for your administrator password. Type it in, then hit <return>. Nothing will appear in the terminal window - that's quite normal. Hopefully, the system will cogitate for a few moments, then provide a list of the available bootable systems. Don't worry too much about the odd error message. Once the command prompt appears again, type:

exit

which will close the terminal window. Then reboot. With any luck, Windows will now be available as an option on the boot screen.

---

### Post by daisybell on 2010-05-17
No, Windows is available as an option, it's just that when I choose it, the system reboots.

It was and is there as a menuentry in grub.cfg at the bottom of the code I pasted from the boot info script.

---

### Post by prenoob on 2010-05-17
I suggest you take a look at this Sourceforge link.  I had a very similar problem and it did the job for me.

[http://sourceforge.net/apps/mediawik...ms:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

---

### Post by daisybell on 2010-05-17
It didn't work.

I suppose I have to try with the Windows recovery cd now. If it is successful, will it remove grub? Could it damage my Ubuntu partition at all?

---

### Post by Mark Phelps on 2010-05-17
> **daisybell said:**
> It didn't work.

I suppose I have to try with the Windows recovery cd now. If it is successful, will it remove grub? Could it damage my Ubuntu partition at all?

Depends on what's on the "CD".  If it's just a Repair CD, not an installation DVD, nor a vendor-provided Restore CD, all it will do is allow you to repair the Win7 boot loader files -- and should do nothing to UBuntu at all.  But it will overwrite the GRUB stuff in the MBR with Win7 -- removing your ability to boot into GRUB.

If it's a vendor-provided Restore/Recovery CD, it's likely to wipe out and replace the drive partitions, restoring the machine to its original state.  That will most likely remove the Ubuntu partition(s).

---

### Post by oldfred on 2010-05-17
You have two windows partitions used for booting. Did you run repairs on both?

sda2 100mb win7 boot partition
sda3 win7 main partition

---

### Post by TorreyKite on 2010-05-17
I'm having the same exact problem (except with Win XP .. not Win 7)

I too see the windows option in grub when I boot but when i select it the screen goes blank for a moment then goes back to grub.
:( :confused: :(

---

### Post by TorreyKite on 2010-05-18
btw...   I was able to resolve my issue with the following advice...

> **drs305 said:**
> Try running the "How to restore the Windows XP bootloader" section of the link I provided. When you reinstalled Ubuntu it looks like it overwrote the information needed by Windows to boot. 

What is happening is that Grub is passing control to Windows, but Windows doesn't know what to do.

If that link doesn't work for you, go to this one:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")



see the whole thread here: [http://ubuntuforums.org/showthread.php?t=1485875]("http://ubuntuforums.org/showthread.php?t=1485875")


hope this helps.

---


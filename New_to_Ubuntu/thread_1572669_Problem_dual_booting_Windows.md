---
title: "Problem dual booting Windows"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by McTwitch on 2010-09-11
I have Windows Vista on the internal harddrive of my computer, and then have Ubuntu 10.04 on a portable harddrive that I use to boot from. I use the Portable all the time. The only time I use Vista is to sync my zune.
Anyway...
I tried messing with BIO's (I have a Dell), so that I could turn off my Internal drive, and not worry about some new install eating Windows. I don't know what it is that I did, but now Window's won't boot. I can still view Window's (And all of it's files) on my Ubuntu Install, but for what ever reason it won't boot. So how do I fix this, hopefully quickly?

---

### Post by abs_kkk on 2010-09-11
select ur internal hard drive as a booting device in BIOS

(reboot ur system and keep constantly pressing DELETE button to enter BIOS)

---

### Post by McTwitch on 2010-09-11
Right, how? Because I'm not even sure what I changed.

---

### Post by Jazzy_Jeff on 2010-09-11
Did you mess with the boot order in the BIOS? If so you may have to mess with it again so that your internal hard drives boots before your other devices. If not I have no idea what you did. Good luck.

---

### Post by McTwitch on 2010-09-11
> Did you mess with the boot order in the BIOS? If so you may have to mess  with it again so that your internal hard drives boots before your other  devices. If not I have no idea what you did. Good luck. 

Thanks, I need it. And I might have, but it's already set up to boot from a USB device before the Internal device, because of the External harddrive. I thought I had put it back the way it was supposed to be, but apparently not.

---

### Post by Silent Warrior on 2010-09-11
If you can't find what you changed, I think most BIOSes come with an option to 'restore factory settings'. Keep an eye out for that, just in case.

---

### Post by abs_kkk on 2010-09-11
keep the booting in this order 

1. {CD ROM}
2. {HDD-0}
3.USB

---

### Post by McTwitch on 2010-09-11
Wouldn't restoring factor settings erase my files and everything that I have on there? Although...I suppose that I could make a folder on my Ubuntu install, and store all of them there, and then just drag them back on when it was done...

---

### Post by McTwitch on 2010-09-11
I changed the boot order like was said, but then I got the error message:

error: file not found
grub rescue>_

---

### Post by Kixtosh on 2010-09-11
> **McTwitch said:**
> Wouldn't restoring factor settings erase my files and everything that I have on there? ...What Silent Warrior probably meant was to restore the BIOS to factory settings, not restore the O.S. (Windows). Once you have entered into the BIOS setup, there will typically be several screens of options you can change (this is different for every brand). Search around the options listed, often on the bottom of the screen, such as "ESC to exit without saving" or "END to save and exit". You may also see some option that mentions "restore default", or "restore to factory settings". If you can find that, you will be able to reset your BIOS to whatever it was originally set to do.

It also sounds as though you're having trouble with GRUB and/or the MBR (Master Boot Record), but you had better wait for someone with more knowledge of those problems when used in conjunction with an external HDD install of Ubuntu than I am or I could easily steer you in the wrong direction.

---

### Post by McTwitch on 2010-09-11
Oh, okay. So it wouldn't do anything but restore factory boot settings? That makes more sense. Yeah, I'll go check that out, thanks.

---

### Post by McTwitch on 2010-09-11
Right, I restored default settings. I got an error message, so I changed it to boot from my external harddrive first, again, so that I could get back on.

---

### Post by Kixtosh on 2010-09-11
> **McTwitch said:**
> Right, I restored default settings. I got an error message, so I changed it to boot from my external harddrive first, again, so that I could get back on.So, what is working now, and what is not working? I think what you are saying is that you CAN boot Ubuntu, from the external HDD, but you CANNOT boot Windows, from the internal HDD, or you get the Grub rescue message you posted earlier?

---

### Post by McTwitch on 2010-09-11
Well, the order that you gave me, nothing worked. But when I changed it to boot from USB first, I can now get on my Ubuntu portable harddrive. I can access my Window's files from here, and everything. So, the only problem is that I can't boot from Window's, the internal drive, for whatever reason.

---

### Post by wilee-nilee on 2010-09-11
Post the bootscript in my signature in code tags as described.

---

### Post by McTwitch on 2010-09-11
Um...so do what now?

---

### Post by Kixtosh on 2010-09-11
Okay, this doesn't sound too bad. Windows uses the MBR to start up, but when you're dual booting with Ubuntu, the Ubuntu installation process adds GRUB instead (GNU GRand Unified Bootloader).

- MBR: [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
- GRUB: [http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

You can repair the MBR to boot Windows correctly, using the repair function of your restore disk (if you have one), but that would mean that you would no longer be able to boot Ubuntu, so it sounds as though you're stuck waiting for someone to tell you if you can repair GRUB so that it will allow you to boot Windows again from there. I'm not familiar with this operation, so I won't attempt to advise you on it, but never fear: I suspect that it won't be very long before another member can help you find the solution!

---

### Post by McTwitch on 2010-09-11
Thanks Kixtosh. I do have the repair disk thing, but I'd prefer booting Ubuntu to booting Windows. I'll just wait until someone can help me fix Grub. The only reason I keep Windows around is because it's what my family uses.

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> Um...so do what now?

Click on the link in my signature download the script put it on the desktop, then run this command in the terminal.
```
sudo bash ~/Desktop/boot_info_script*.sh
``` 

This will make another file on the desktop, open it, copy the text to a reply highlight the text then click on the # in the reply panel. I am assuming your old enough to to read. ;)

Reloading the mbr is easy stuff just post the script .

---

### Post by McTwitch on 2010-09-11
Alright, just give me a few moments, and I'll give you the results..

---

### Post by McTwitch on 2010-09-11
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3    *     30,801,920   625,140,399   594,338,480   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    20,482,874    20,482,812  83 Linux
/dev/sdb2          81,915,559   625,137,344   543,221,786   5 Extended
/dev/sdb5         615,916,098   625,137,344     9,221,247  82 Linux swap / Solaris
/dev/sdb6          81,915,561   133,114,589    51,199,029  83 Linux
/dev/sdb7         133,114,653   440,309,519   307,194,867  83 Linux
/dev/sdb3          20,482,875    81,915,434    61,432,560  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        68D8B5A5D8B57244                       ntfs       RECOVERY                      
/dev/sda3        4028B7C928B7BBEA                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2136a7d2-11fa-4158-98ec-b577ba0d0ff5   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        01598a75-88b9-4bb2-a247-45c6c46ed04c   ext4                                     
/dev/sdb5                                               swap                                     
/dev/sdb6        fc534f08-16f9-49bb-b4a2-b67ec506eebc   ext4       10.04-root                    
/dev/sdb7        511b1c51-aab0-4f49-bb6b-a831ee53c9d4   ext4       10.04-home                    
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro)
/dev/sdb7        /home                    ext4       (rw)
/dev/sdb1        /media/2136a7d2-11fa-4158-98ec-b577ba0d0ff5 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb3        /media/01598a75-88b9-4bb2-a247-45c6c46ed04c ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 2136a7d2-11fa-4158-98ec-b577ba0d0ff5
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 2136a7d2-11fa-4158-98ec-b577ba0d0ff5
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
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2136a7d2-11fa-4158-98ec-b577ba0d0ff5
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2136a7d2-11fa-4158-98ec-b577ba0d0ff5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2136a7d2-11fa-4158-98ec-b577ba0d0ff5
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2136a7d2-11fa-4158-98ec-b577ba0d0ff5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2136a7d2-11fa-4158-98ec-b577ba0d0ff5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2136a7d2-11fa-4158-98ec-b577ba0d0ff5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 4028b7c928b7bbea
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdc6)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdc6)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdc6)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdc6)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=2136a7d2-11fa-4158-98ec-b577ba0d0ff5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc3 during installation
UUID=01598a75-88b9-4bb2-a247-45c6c46ed04c /home           ext4    defaults        0       2
/dev/sdc5       none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.4GB: boot/grub/core.img
   7.6GB: boot/grub/grub.cfg
   2.5GB: boot/initrd.img-2.6.32-21-generic
   2.5GB: boot/vmlinuz-2.6.32-21-generic
   2.5GB: initrd.img
   2.5GB: vmlinuz

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 4028b7c928b7bbea
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2136a7d2-11fa-4158-98ec-b577ba0d0ff5
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=2136a7d2-11fa-4158-98ec-b577ba0d0ff5 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2136a7d2-11fa-4158-98ec-b577ba0d0ff5
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=2136a7d2-11fa-4158-98ec-b577ba0d0ff5 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=511b1c51-aab0-4f49-bb6b-a831ee53c9d4 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=10fd3aa7-2241-45ed-b0bb-4299647b7950 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


  59.2GB: boot/grub/core.img
  59.7GB: boot/grub/grub.cfg
  59.4GB: boot/initrd.img-2.6.32-21-generic
  59.7GB: boot/initrd.img-2.6.32-24-generic
  59.3GB: boot/vmlinuz-2.6.32-21-generic
  59.6GB: boot/vmlinuz-2.6.32-24-generic
  59.7GB: initrd.img
  59.4GB: initrd.img.old
  59.6GB: vmlinuz
  59.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
that's a large bit of data there. Hope it's got what you need.

---

### Post by Kixtosh on 2010-09-11
Never mind ... you figured it out while I was typing!

---

### Post by McTwitch on 2010-09-11
Ah, crap. I put it as a quote, instead of a code. My bad. Apologize to anyone who has a problem with that.

---

### Post by McTwitch on 2010-09-11
Ah, crap. I put it as a quote, instead of a code. My bad. Apologies to anyone who has a problem with that.

---

### Post by wilee-nilee on 2010-09-11
[B]Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in
partition #6 for /boot/grub.[/B]

I would put this HD to be read first, I think that is your basic problem. If you look at the top of the script you have grub in sda looking at sda1 which is the firmware for the computer, not gonna work, but if you put sdb as first read you should be okay.

We could reinstall the Windows bootloader to that HD if you wanted to.

The other option is just reloading grub if the HD reading is checked and it still doesn't boot.

You have multiple Ubuntu installs; in sdb1 and sdb6 I assume sdb6 is the last install and grub is looking at that to boot with, in the sdb=mbr.

You also have a bootflag on sdb1 Ubuntu doesn't need a boot flag this can be removed with gparted from a live cd right click on partition then manage flags untick boot.

Quote is okay we all just want you up and running again, gives us time to bork our setups.;)

---

### Post by McTwitch on 2010-09-11
Yeah, SDB1 is my main install, then SDB6 is the one that I just kind of screw around with, and break things with, etc. So, how would I go about changing the things that you said?

I try to be caught up with the new language and everything, but what is bork?

---

### Post by wilee-nilee on 2010-09-11
Yeah if you have more then one OS using grub and it=Linux, if a grub upgrade comes through it can rewrite your mbr if you let it, no biggie follow this link and commands, from a live cd Karmic or later. I have Lucid and Maverick side by side and have seen grub upgrades in lately.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

So take a look at these commands they are straight from the link default; run them from a live cd except for the reboot to run the grub-update.

```
sudo mount /dev/sdb1 /mnt
```
Then
```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```
Reboot the computer making sure it is reading the sdb HD first, check your bios, then in the rebooted Ubuntu run.
```
sudo update-grub
```

---

### Post by McTwitch on 2010-09-11
I would do that, but for whatever reason, the computer won't boot the Livedisk.

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> I would do that, but for whatever reason, the computer won't boot the Livedisk.

Does your computer boot a thumb drive and can you load one. Except for going the total manual boot route to get into sdb1, there I think is no other way.

I have never used the manual boot method I'm lazy, so I have to look for the instructions.

You have changed sdb to be read first, I am assuming, as the script looks it should boot anyway. This is not always the case I'm just trying to see if we have gone through all the steps. The script shows sda as being first in line it should be sdb before sda in the bios boot.

Also your computer will boot a live disc if it is a good one with a key prompt, mine is f12, it could be any key in the row including esc. This is assuming the cd/dvd reader is working. Some computers jump past the cd boot even when it is put at the top of the list in the bios.

---

### Post by McTwitch on 2010-09-11
Interesting, so what am I supposed to do? My guess would change the BIO's boot order, but that's just a guess.

---

### Post by wilee-nilee on 2010-09-11
So here is a page on command line grub use so you can boot into sdb1 from the grub> prompt. Read carefully ask questions, there are regulars, on the forum who are very good at this I hope they stop by.
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html)

---

### Post by McTwitch on 2010-09-11
From what I can see, all of the links are for Ubuntu 9.10 and older. Will they still work for 10.04?

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> From what I can see, all of the links are for Ubuntu 9.10 and older. Will they still work for 10.04?

Why can't you boot a live cd?

---

### Post by McTwitch on 2010-09-11
No idea. It just gave me the same error message that it gave me when I returned by boot order to the default, and tried booting from the internal.

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> No idea. It just gave me the same error message that it gave me when I returned by boot order to the default, and tried booting from the internal.

Okay I think our basic problem here is user experience=yours. No big deal we want to just get you up and running. Do you understand what I mean by using a fkey prompt to have a choice of boot. You would start the computer, then click the appropriate key until you saw a boot order message then a screen to choose the boot. If you get there boot the cd, and run the commands I suggested.

To be honest here you want to always be able to boot a live Linux or other install discs, and know how, otherwise we end up with hours of instructions, and pages of communications. The problem in the end may be fixed in about 2 min, if you know some basic stuff.;)

Have you put sdb the first HD to be read in bios?

---

### Post by McTwitch on 2010-09-11
I know how to use a livedisk and everything, but normally I just put the bugger in, restarted the machine, and it would boot me to the livedisk. This time, however, it did not. And..I don't really know how to change the HD order or anything, so I could use a small walkthrough on that. And the fkey thing...is a foreign concept to me. I am fairly inexperienced, I will admit this.

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> I know how to use a livedisk and everything, but normally I just put the bugger in, restarted the machine, and it would boot me to the livedisk. This time, however, it did not. And..I don't really know how to change the HD order or anything, so I could use a small walkthrough on that. And the fkey thing...is a foreign concept to me. I am fairly inexperienced, I will admit this.

No big deal, So when I boot a live cd I hit the f12 repeatedly immediately this brings up a boot from screen that you use the arrow keys to go to what you want to boot. Your computer it might be a fkey or esc. You have gotten into your bios I believe probably with a f2 prompt.

So the only problem here may be that the hard drive with Ubuntu on it=sdb is not being read first, your computer will not boot unless it is; no matter what we do, other then loading the MS bootloader to sda to boot windows.

Now you also have a Dell computer, there is a program called Dell Data Safe in the Windows partition possibly that could be causing problems. We can worry about this by only getting into windows to look, by getting the Ubuntu bootloader to work or reloading the MS bootloader

So at this point we at the least want to get you booting a live Ubuntu or recovery/dvd/install/disc, for Windows, so we can load the appropriate bootloader and clean up if needed.

Your thread started out with you commenting on messing with your bios, can you go back in and just make sure in the booting order the sdb HD is before the sda one.

---

### Post by McTwitch on 2010-09-11
Oh, well put like that..Yeah, SDB boots before SDA right now. Do you want me to enter set up, or go to boot options? Because F2 is set up, and F12 is boot options.

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> Oh, well put like that..Yeah, SDB boots before SDA right now. Do you want me to enter set up, or go to boot options? Because F2 is set up, and F12 is boot options.

If f12 gets you to the boot chose the cd player boot the live disc and run the commands to set sdb1 as the mounted partition to reboot back to and run update grub.

If this works look in the control panel add remove in Vista for the Dell data Safe program, I don't think you have it but it messes up the mbr.

---

### Post by McTwitch on 2010-09-11
Right, apparently I am more inexperienced than I thought. I tried booting the cd/dvd player, and it brought me to the Grub menu for my External. I'll try again, though.

---

### Post by wilee-nilee on 2010-09-11
I think I see what the problem is here, I missed the external HD part. You just need to reload the MS bootloader to sda, to boot Vista without the external plugged in.

Just run the highlighted command. There is a http link for getting to the command line with a Vista recovery, or install disc.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

My mistake here I missed that it was windows that would not boot, but Ubuntu was, is this correct?

I think you had a grub update in the linux setup and it defaulted grub to the internal HD's mbr rather then to sdb so watch out for that.

So I am a little mixed up as to what you can boot as of now.

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> Right, apparently I am more inexperienced than I thought. I tried booting the cd/dvd player, and it brought me to the Grub menu for my External. I'll try again, though.

Since it is a external it is a USB plug correct Linux at times can not always differentiate a thumb from a HD from DVD player at times. Did you just try to boot from the grub menu you got, that must be sdb, I'm guessing here.

The above post #41 though will get the MS bootloader back in so that Vista should boot without the external plugged in. Run the Vista disc with the external unplugged and follow the http link if needed and just run the one highlighted command.

---

### Post by McTwitch on 2010-09-11
Well, there's another problem. I've looked around for it, but I can't find the darn disk for Vista. Are there any other alternatives?

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> Well, there's another problem. I've looked around for it, but I can't find the darn disk for Vista. Are there any other alternatives?

Lucky for you we have a vista recovery disc link this is just for this sort of thing, it is not a install disc. Down load it boot it follow the http link as I suggested if needed for getting to the command line and run that one command.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Hopefully this will get you up and running, sorry for not reading the thread more carefully, my bad.

---

### Post by McTwitch on 2010-09-11
Do I have to burn the bugger to a disk or anything?

64-Bit or 32-bit, does it matter?

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> Do I have to burn the bugger to a disk or anything?

64-Bit or 32-bit, does it matter?

Yes you have to burn it to a disc so you can boot it, and download the appropriate 32 or 64 bit which ever your running.

I have seen people try to get this recovery on a thumb but never any success, burn to a cd-r.

Interestingly if you run sudo update-grub in your Ubuntu OS it will put Vista in grub if it isn't already. Have you tried booting it that way, and if you can look for that Dell data Safe in add remove in Vista.

This would be just be a test to see if the grub on the external boots Vista and to look for the Data Safe program. We still need to reload the MS bootloader to sda with the recovery disc so you can boot Vista all by itself, with no external attached.

---

### Post by McTwitch on 2010-09-11
Right, well, there's another problem. I don't know what version of Vista I'm running. is there anyway to find out?

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> Right, well, there's another problem. I don't know what version of Vista I'm running. is there anyway to find out?

Version I assume you mean 32 bit or 64, other wise the recovery disc will work on home,pro...etc. If you have a OEM install look your computer up on the net or you could call customer service at Dell. I am not sure how to do this part you will have to cover this part unless others know how. You probably can get this information easily I just have never run into this knowing what I have at all times.

---

### Post by McTwitch on 2010-09-11
Hm. Well, wouldn't 32-bit work on 32 and 64? Because I know my computer can handle 64, but my Ubuntu install is 32-bit. Wish I knew a bit more about my vista install, though.

---

### Post by wilee-nilee on 2010-09-11
It just occurred to me that you may be able to boot Vista from the external grub menu, if you can boot in and right click on the computer in the menu then properties and it will tell you what version it is.

You may have to boot Ubuntu then run sudo update-grub to get the Vista stanza, put into grub.

This is kind of a long way around but it helps to understand or recognize boot stuff. In the end if we get you back in place you can set the external to not see Vista at all and your only worry really is watching for any grub update/upgrades and where it is put.

---

### Post by McTwitch on 2010-09-11
Right, I understand what I have to do, but I was wondering if you could give me a walk through.

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> Right, I understand what I have to do, but I was wondering if you could give me a walk through.

When you have booted the external you get a grub menu choose vista, and see if it boots. If this doesn't work boot Ubuntu then run then in the terminal run
```
sudo update-grub
```

Try to boot Vista again.

You see as it is the Linux grub bootloader is in place as it should be in the external and you should be seeing a Vista line to allow you to boot from the grub menu. 

I am assuming that you can get to this grub menu that boots the external, and that you can get into any distro as of now. You can still boot the external to Ubuntu I hope.

What is your computer model? and is it the factory install.

---

### Post by McTwitch on 2010-09-11
Right, I don't know about Vista, but my boot menu has a Windows Recovery Environment option, or something like that. Is that what you mean? Because other than that there is nothing about Windows, at all.

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> Right, I don't know about Vista, but my boot menu has a Windows Recovery Environment option, or something like that. Is that what you mean? Because other than that there is nothing about Windows, at all.

Some times it is the recovery that shows up lets not mess with anything in grub unless you know for sure that your booting straight to Vista.

Really the only thing holding you up is finding out the bit type or whether it matters with a recovery disc. Personally I think it would be unproductive to not know this and possibly dangerous to your setup, erring on the side of common sense.

---

### Post by McTwitch on 2010-09-11
Right. Story of my life. Everything is halted by the lack of one tiny, unbelievably important detail. I have a good friend that I asked about the 32-bit and the 64-Bit thing. Hoping he gets back to me soon.

Alright, I found a Vista disk, but it says that "This DVD is not for reinstallation of programs or drivers.". Would it still be the disk that I needed, or is that something else?
Nevermind. On the disk, it says that that stuff is already installed on the program, also, it is 64 bit. So I'll go with the 64-bit.

---

### Post by McTwitch on 2010-09-11
Right, the download link isn't working. I'm not a fan of torrents, but this one says I have 0 peers, and hasn't downloaded anything yet. I have the starter thing, but...yeah. It doesn't appear to be working.

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> Right, the download link isn't working. I'm not a fan of torrents, but this one says I have 0 peers, and hasn't downloaded anything yet. I have the starter thing, but...yeah. It doesn't appear to be working.

Some times it takes a few minutes, I loaded my torrent program and it is almost done.

---

### Post by McTwitch on 2010-09-11
Got it downloaded. Now for the burning..hope you're still around.

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> Got it downloaded. Now for the burning..hope you're still around.

I'm on the west coast US so I'll be around for awhile, it is still early for me.

---

### Post by McTwitch on 2010-09-11
Oh, awesome. Well, I've now got myself a nice Vista, 64-Bit repair disk. What do I do with it?

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> Oh, awesome. Well, I've now got myself a nice Vista, 64-Bit repair disk. What do I do with it?

So you will boot it from that fkey prompt or if it boots from it being first in bios. 

Here is a link that explains getting to the command line in Vista.
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

**You will only need to run the command I have put in bold lettering.** I have included the whole or some of the boot repair kit these other commands have importance at other stages, hopefully not needed at this time.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by McTwitch on 2010-09-11
I want to make sure that I don't screw this up, so please bear with me. I put in the disk, restart, press F12, choose to boot from the disk. Then, click install now, choose language, hit next, choose to repair now, and then choose to use the Command Prompt. From there, I type in "BootRec.exe /fixmbr".

But, I have a question, because it says:

> updates MBR master boot record...do not run if you still want grub
So, if I unplug my External, I should still be able to boot onto my two ubuntu installs, right?

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> I want to make sure that I don't screw this up, so please bear with me. I put in the disk, restart, press F12, choose to boot from the disk. Then, click install now, choose language, hit next, choose to repair now, and then choose to use the Command Prompt. From there, I type in "BootRec.exe /fixmbr".

But, I have a question, because it says:

updates MBR master boot record...do not run if you still want grub 


**So, if I unplug my External**, I should still be able to boot onto my two ubuntu installs, right?

So what your doing with this command yes you have it correct is reloading the MS bootloader to the master boot record of the internal sda hard drive. Do this with the external unpluged.

As of now your Ubuntu installs are booting with the grub bootloader in the master boot record of the external sdb, so if you boot from the USB external Ubuntu should boot up as it has **if it is as of now**.

Is this highlighted section in your quote a misstype, your Ubuntu installs are on the external, am I correct.

I can see way the line about overwriting grub is scary; you actually are, grub got installed in the internal sda HD overwriting the MS bootloader in the mbr. Grub on the external should be fine.

---

### Post by McTwitch on 2010-09-11
Yessir. My Ubuntu's are on an External, Maxtor 300 and some gigabyte external harddrive. Pretty useful little bugger. I think I can handle this then. Thanks a bunch for all of the help. As one of the few Ubuntu/Window's users, I was wondering if I could add you.

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> Yessir. My Ubuntu's are on an External, Maxtor 300 and some gigabyte external harddrive. Pretty useful little bugger. I think I can handle this then. Thanks a bunch for all of the help. As one of the few Ubuntu/Window's users, I was wondering if I could add you.

I have a maxtor of the same size, works great, and yes add me. Sorry for misreading the post then questioning your level of ability, not very pretty now is it.;)

Just let us know if this all works.

---

### Post by McTwitch on 2010-09-11
Yes, worked beautifully. Everything boots as it should now, all thanks to you. Plus, I have a Vista disk to add to my collection. That makes Vista, Ubuntu 10.04, Fedora 13, and Wolvix...whatever version they have now.

---

### Post by wilee-nilee on 2010-09-11
> **McTwitch said:**
> Yes, worked beautifully. Everything boots as it should now, all thanks to you. Plus, I have a Vista disk to add to my collection. That makes Vista, Ubuntu 10.04, Fedora 13, and Wolvix...whatever version they have now.

Yay, my inept reading probably ran you through more tasks then needed, hopefully that was helpful. You succeeded in spite of my help, or at least kept with it.

---

### Post by McTwitch on 2010-09-11
It was very helpful. I don't mind that we ran through all that stuff. To be quite honest, probably the only reason I succeeded was because I was trying harder because you said I was inexperienced. I am, but every now and then, you've gotta pop up, and show improvement.

---

### Post by Kixtosh on 2010-09-12
Good job guys! Well done to both of you!

---


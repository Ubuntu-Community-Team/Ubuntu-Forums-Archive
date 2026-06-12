---
title: "Windows fails to boot after Lucid 10.04 install"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by doninsa on 2010-12-26
I just installed Lucid Lynx on my primary computer and now Windows XP will not start.  Two instances of Windows XP show on the Grub boot menu, but when I select them all I get is a flashing cursor.

I had two copies of Windows XP on the computer before installing Ubuntu.  One copy was on a 500 Gig drive 0 and the other copy was on an 80 Gig drive 1.  Both show up on the Grub menu, but neither one will start.  When selected the screen clears and all I see is a flashing cursor.  I used the Disk Utility and both copies copies of WinXP are still on the drives.  Any help would be appreciated.

---

### Post by Rubi1200 on 2010-12-26
Hi,
please run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

This can be done either from within Ubuntu or from a LiveCD.

Thanks.

---

### Post by doninsa on 2010-12-26
> **Rubi1200 said:**
> Hi,
please run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

This can be done either from within Ubuntu or from a LiveCD.

Thanks.

Okay I managed to run the boot info script and I've attached the results.

---

### Post by Rubi1200 on 2010-12-26
Thanks for the results; can you post the output of > sudo update-grub please.
Also, how is BIOS set to boot? From sda or sdb?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   518,790,215   518,790,153   7 HPFS/NTFS
/dev/sda2         518,791,166   976,773,119   457,981,954   5 Extended
/dev/sda5         518,791,168   964,702,207   445,911,040  83 Linux
/dev/sda6         964,704,256   976,773,119    12,068,864  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8CC46059C4604812                       ntfs       Segate 500 gig                
/dev/sda2: PTTYPE="dos" 
/dev/sda5        94f9d735-0a5a-4bcb-92e4-987d51543fc1   ext4                                     
/dev/sda6        47df15ed-5bb0-47d4-894e-32806a614547   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8CC46059C4604812                       ntfs       Segate 80 gig                 
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /usepmtimer /NoExecute=OptIn 

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
search --no-floppy --fs-uuid --set 94f9d735-0a5a-4bcb-92e4-987d51543fc1
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
search --no-floppy --fs-uuid --set 94f9d735-0a5a-4bcb-92e4-987d51543fc1
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 94f9d735-0a5a-4bcb-92e4-987d51543fc1
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=94f9d735-0a5a-4bcb-92e4-987d51543fc1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 94f9d735-0a5a-4bcb-92e4-987d51543fc1
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=94f9d735-0a5a-4bcb-92e4-987d51543fc1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 94f9d735-0a5a-4bcb-92e4-987d51543fc1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 94f9d735-0a5a-4bcb-92e4-987d51543fc1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8cc46059c4604812
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8cc46059c4604812
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=94f9d735-0a5a-4bcb-92e4-987d51543fc1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=47df15ed-5bb0-47d4-894e-32806a614547 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 321.6GB: boot/grub/core.img
 270.2GB: boot/grub/grub.cfg
 321.6GB: boot/initrd.img-2.6.32-21-generic
 321.5GB: boot/vmlinuz-2.6.32-21-generic
 321.6GB: initrd.img
 321.5GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /usepmtimer /NoExecute=OptIn
```

---

### Post by amjjawad on 2010-12-26
To make it easier for everyone else, I'm going to post it here:

You need to use "CODE" tags or "#".



```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   518,790,215   518,790,153   7 HPFS/NTFS
/dev/sda2         518,791,166   976,773,119   457,981,954   5 Extended
/dev/sda5         518,791,168   964,702,207   445,911,040  83 Linux
/dev/sda6         964,704,256   976,773,119    12,068,864  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8CC46059C4604812                       ntfs       Segate 500 gig                
/dev/sda2: PTTYPE="dos" 
/dev/sda5        94f9d735-0a5a-4bcb-92e4-987d51543fc1   ext4                                     
/dev/sda6        47df15ed-5bb0-47d4-894e-32806a614547   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8CC46059C4604812                       ntfs       Segate 80 gig                 
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /usepmtimer /NoExecute=OptIn 

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
search --no-floppy --fs-uuid --set 94f9d735-0a5a-4bcb-92e4-987d51543fc1
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
search --no-floppy --fs-uuid --set 94f9d735-0a5a-4bcb-92e4-987d51543fc1
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 94f9d735-0a5a-4bcb-92e4-987d51543fc1
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=94f9d735-0a5a-4bcb-92e4-987d51543fc1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 94f9d735-0a5a-4bcb-92e4-987d51543fc1
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=94f9d735-0a5a-4bcb-92e4-987d51543fc1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 94f9d735-0a5a-4bcb-92e4-987d51543fc1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 94f9d735-0a5a-4bcb-92e4-987d51543fc1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8cc46059c4604812
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8cc46059c4604812
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=94f9d735-0a5a-4bcb-92e4-987d51543fc1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=47df15ed-5bb0-47d4-894e-32806a614547 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 321.6GB: boot/grub/core.img
 270.2GB: boot/grub/grub.cfg
 321.6GB: boot/initrd.img-2.6.32-21-generic
 321.5GB: boot/vmlinuz-2.6.32-21-generic
 321.6GB: initrd.img
 321.5GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /usepmtimer /NoExecute=OptIn
```

---

### Post by amjjawad on 2010-12-26
> **Rubi1200 said:**
> Thanks for the results; can you post the output of please.
Also, how is BIOS set to boot? From sda or sdb?


You beat me to it just because my connection is slow :P hehehehe. Never mind ;)

I'll leave it between your capable hands!

---

### Post by doninsa on 2010-12-26
The system is set to boot from the 500 gig drive which I think is sda.  The output of sudo update-grub is as follows:
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Microsoft Windows XP Home Edition on /dev/sdb1
done
don@don-desktop:~$ ^C
don@don-desktop:~$ 

Sorry about not using code #.  Not sure how it works.

---

### Post by amjjawad on 2010-12-26
[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7174[/IMG]

Sorry Rubi, I'm going to post this then fade away.

To the OP:
Make sure sda (HDD1) is the first HDD to boot from in your BIOS
and
sdb (HDD2) is the second one.

Good luck!

---

### Post by doninsa on 2010-12-26
I checked the bios and HDD1 is the first HDD and HDD2 is the second.  That is the 500 gig is first and the 80 gig is the second.  I've had that problem before with another insallation of Ubuntu.  Good thought tho.

---

### Post by Rubi1200 on 2010-12-26
And it still does not work? You are unable to boot into either Windows installation?

Funny, because the results of the script seem quite normal.

@amjjawad:
your input is always welcome :)

---

### Post by doninsa on 2010-12-26
It's true. Neiher one of the selections on the grub menu will boot.  When selecting either one the screen clears and I'm left with a flashing cursor in the upper left corner.  

Is there a utility I can run to find and install other operating systems?  I'm hoping that might work.

---

### Post by amjjawad on 2010-12-26
> **doninsa said:**
> It's true. Neiher one of the selections on the grub menu will boot.  When selecting either one the screen clears and I'm left with a flashing cursor in the upper left corner.  

Is there a utility I can run to find and install other operating systems?  I'm hoping that might work.

What about Ubuntu? does it work? I mean, can you login to Ubuntu?

As Rubi said and I already noticed that too, nothing is wrong with your boot script. You already did "grub-update" and still nothing.

I guess it's Windows thing more than an Ubuntu issue.
Do you need your both XP Installation? if so, I'm afraid you need to restore MBR and give the control to Windows Boot Loader then re-Install GRUB2 again.

Let's see what Rubi thinks :)

Rubi, appreciate that mate :)
I couldn't resist ... whenever there's Dual-Booting issue, I can't stop myself :D

---

### Post by doninsa on 2010-12-26
Is there a command or utility that I can run that looks for operating systems and installs them?  Perhaps that would clear up the problem.  I'd hate to go through uninstalling Ubuntu again.  The fix mbr is tricky and I risk losing everything.

---

### Post by Rubi1200 on 2010-12-26
Two more things we can try:

1. run this command:
```
sudo os-prober
```
Reboot and see if you can get in.

if not, go to 2.

2. reinstall GRUB:
```
sudo grub-install --recheck /dev/sda
sudo update-grub
```

Let's see if that works.

Let us know please.

---

### Post by amjjawad on 2010-12-26
> **doninsa said:**
> Is there a command or utility that I can run that looks for operating systems and installs them?  Perhaps that would clear up the problem.  I'd hate to go through uninstalling Ubuntu again.  The fix mbr is tricky and I risk losing everything.

Fixing MBR approach will not re-install the whole OS. You have 2 copies of XP and you have Ubuntu. I understand it's hard to re-install that again.

However, it's your call.
Do you need both Copies of XP?

---

### Post by doninsa on 2010-12-26
> **amjjawad said:**
> [IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7174[/IMG]

Sorry Rubi, I'm going to post this then fade away.

To the OP:
Make sure sda (HDD1) is the first HDD to boot from in your BIOS
and
sdb (HDD2) is the second one.

Good luck!

> **amjjawad said:**
> What about Ubuntu? does it work? I mean, can you login to Ubuntu?

As Rubi said and I already noticed that too, nothing is wrong with your boot script. You already did "grub-update" and still nothing.

I guess it's Windows thing more than an Ubuntu issue.
Do you need your both XP Installation? if so, I'm afraid you need to restore MBR and give the control to Windows Boot Loader then re-Install GRUB2 again.

Let's see what Rubi thinks :)

Rubi, appreciate that mate :)
I couldn't resist ... whenever there's Dual-Booting issue, I can't stop myself :D

I was hoping it wouldn't come to this.  Looks like the only solution is to restore the mbr.  I don't think I'm up to doing another Grub install

---

### Post by doninsa on 2010-12-26
I need to take a break from this for a few minutes and see if the other drive will boot Windows.  Be back in a few.

---

### Post by amjjawad on 2010-12-26
> **doninsa said:**
> I was hoping it wouldn't come to this.  Looks like the only solution is to restore the mbr.  I don't think I'm up to doing another Grub install

Forget my suggestions now and go for Rubi's one.
[http://ubuntuforums.org/showpost.php?p=10281261&postcount=14](http://ubuntuforums.org/showpost.php?p=10281261&postcount=14)

Let's see what will happen then we can decide what's the next step.

---

### Post by doninsa on 2010-12-26
Well, I gave up on Ubuntu on this machine.  This is the second time I've had this problem installing Ubuntu Lucid Lynx 10.04.  The install goes fine and Ubuntu loads just fine, but Windows XP will not load.  It appears on the menu, but will not load.  Thanks for all the help.  Sorry it dinn't work out.  I've used Seagate Disk Wizard to clone my backup drive over my primary drive.  Hopefully not much data lost as I do a routine backup from one drive to the other.  At least I have one copy of Ubuntu running on one of my old computers.  This could be a serious problem for anyone who doesn't have a real good backup system.  One thing I will say. The help is much appreciated.

---

### Post by amjjawad on 2010-12-26
> **doninsa said:**
> Well, I gave up on Ubuntu on this machine.  This is the second time I've had this problem installing Ubuntu Lucid Lynx 10.04.  The install goes fine and Ubuntu loads just fine, but Windows XP will not load.  It appears on the menu, but will not load.  Thanks for all the help.  Sorry it dinn't work out.  I've used Seagate Disk Wizard to clone my backup drive over my primary drive.  Hopefully not much data lost as I do a routine backup from one drive to the other.  At least I have one copy of Ubuntu running on one of my old computers.  This could be a serious problem for anyone who doesn't have a real good backup system.  One thing I will say. The help is much appreciated.

I'm sorry to hear you gave up. We still could help you and walk you through step by step but of course it's your call. If you want that, we'll be more than glad to help :)

Lately, I got the same issue with XP.
I had Ubuntu and XP on one HDD. XP failed to load while Ubuntu was loading just perfect. I checked the boot script that we asked you to run and ... there was absolutely nothing wrong. I even tried to fix the MBR using XP Disk but nothing happened. It worked once then stopped again. I ended up formatting the HDD because I was writing one of my guides in my signature and I needed to format. However, that was my test PC so no losses at all.


Let us know if you need anything.
I still think it's a Windows issue not Ubuntu.

---

### Post by doninsa on 2010-12-27
> **Rubi1200 said:**
> Two more things we can try:

1. run this command:
```
sudo os-prober
```
Reboot and see if you can get in.

if not, go to 2.

2. reinstall GRUB:
```
sudo grub-install --recheck /dev/sda
sudo update-grub
```

Let's see if that works.

Let us know please.

Wish I'd seen this before deciding to trash the whole install and go back to Windows XP.  Anyway, I wanted to tell you what I did try.  This morning I disconnected HDD #2 and tried to install Ubuntu 10.04 again.  This time I got a CD read error about two-thirds of the way through the install.  Trying not to give up, I tried another install on the same drive but this time it wanted to divide my hard drive into three parts, two Ubuntu partitions and one NTFS.  Not knowing how to set up the partitions manually I gave up for the second time.  All is not lost though because I have an older computer with Lucid Lynx and Windows XP running on it.  In this case I have one drive with Windows and the other drive with Ubuntu.  Once again I'd like to say thanks for the help.

---

### Post by Rubi1200 on 2010-12-27
On behalf of amjjawad and myself, you are more than welcome :)

I cannot explain to you why some configurations are easy to get up and running while others require an awful lot of work.

In any event, I am glad you got something sorted out and that you have not given up completely on Ubuntu, and Linux in general.

Good luck and enjoy!

---

### Post by amjjawad on 2010-12-27
> **Rubi1200 said:**
> On behalf of amjjawad and myself, you are more than welcome :)

I cannot explain to you why some configurations are easy to get up and running while others require an awful lot of work.

In any event, I am glad you got something sorted out and that you have not given up completely on Ubuntu, and Linux in general.

Good luck and enjoy!

Ditto :)

---

### Post by doninsa on 2010-12-27
> **Rubi1200 said:**
> On behalf of amjjawad and myself, you are more than welcome :)

I cannot explain to you why some configurations are easy to get up and running while others require an awful lot of work.

In any event, I am glad you got something sorted out and that you have not given up completely on Ubuntu, and Linux in general.

Good luck and enjoy!

Success!!  I tried one more time and this time everything works.  I can boot into Ubuntu or either of the Windows XP installs.  Perseverance pays off once again.  :)

---

### Post by amjjawad on 2010-12-27
> **doninsa said:**
> Success!!  I tried one more time and this time everything works.  I can boot into Ubuntu or either of the Windows XP installs.  Perseverance pays off once again.  :)

Great job :)
See? we told you that you can do it ;)

---


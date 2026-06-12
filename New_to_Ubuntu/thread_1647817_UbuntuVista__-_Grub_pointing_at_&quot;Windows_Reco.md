---
title: "Ubuntu/Vista  - Grub pointing at &quot;Windows Recovery&quot;"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by davidmclifton on 2010-12-17
I've read a dozen threads on this topic, most of which either had some sort of complete loss issue where the person apparently just up and decided Ubuntu would not be for them, or others where the issue was solved 'in IRC' with no posted actual resolution.

That said - I had an extra partition on my disk already which I nixed and replaced with Ubuntu's requirements - so no adjusting of the original Vista partitions occurred. I used the manual/advanced partition screen and created a 4GB swap space (to match my 4GB RAM) and the rest of the free disk to Ubuntu /. Install went fine, and I am still able to access both Windows and Ubuntu.

However, for Windows it says it is the "Windows Recovery" partition, and when I select it I get a text menu defaulting to 'recover' though it also has the option to 'startup normally' - selecting startup normally seems to work ok, however the problem is that the default is recover and there is a timer on it. It isn't a situation my wife is going to be able to figure out/live with on the same computer unfortunately. I somehow need to get it to recognize the regular boot for Vista rather than just the recover option.

I would greatly appreciate some assistance in fixing my boot loader issue - I'm at a loss on what to try.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
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
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2             129,024    31,586,303    31,457,280   7 HPFS/NTFS
/dev/sda3    *     31,586,304   767,279,858   735,693,555   7 HPFS/NTFS
/dev/sda4         767,281,150   976,771,071   209,489,922   5 Extended
/dev/sda5         767,281,152   775,280,639     7,999,488  82 Linux swap / Solaris
/dev/sda6         775,282,688   976,771,071   201,488,384  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D8-061E                              vfat       DellUtility                   
/dev/sda2        6202462F0246088D                       ntfs       RECOVERY                      
/dev/sda3        52E44884E4486C73                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        20c8757b-4761-428f-bec0-838311abf620   swap                                     
/dev/sda6        37cf806e-d74d-4adb-b7de-fc7619b49cef   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 37cf806e-d74d-4adb-b7de-fc7619b49cef
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 37cf806e-d74d-4adb-b7de-fc7619b49cef
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 37cf806e-d74d-4adb-b7de-fc7619b49cef
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=37cf806e-d74d-4adb-b7de-fc7619b49cef ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 37cf806e-d74d-4adb-b7de-fc7619b49cef
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=37cf806e-d74d-4adb-b7de-fc7619b49cef ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 37cf806e-d74d-4adb-b7de-fc7619b49cef
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 37cf806e-d74d-4adb-b7de-fc7619b49cef
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 52e44884e4486c73
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
UUID=37cf806e-d74d-4adb-b7de-fc7619b49cef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=20c8757b-4761-428f-bec0-838311abf620 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 414.2GB: boot/grub/core.img
 450.8GB: boot/grub/grub.cfg
 397.3GB: boot/initrd.img-2.6.35-22-generic
 414.2GB: boot/vmlinuz-2.6.35-22-generic
 397.3GB: initrd.img
 414.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by davidmclifton on 2010-12-17
I attempted this unsuccessfully:

```
maestro@notaname:~$ sudo apt-get install os-prober
Reading package lists... Done
Building dependency tree       
Reading state information... Done
os-prober is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 196 not upgraded.
maestro@notaname:~$ sudo os-prober
/dev/sda3:Windows Recovery Environment (loader):Windows:chain
maestro@notaname:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda3
done
maestro@notaname:~$ 
```

Still doesn't see the real windows environment.

---

### Post by Quackers on 2010-12-17
/dev/sda3 is your real Vista partition. Grub sometimes labels them wrongly with Vista. If it's offering the F8 recovery/Last good configuration/startup normally screen, Windows thinks there's a small problem with itself. I would suggest running a chkdsk on C: and if there are errors reported keep running it until there are no errors reported.
Here's how
[http://www.windows-help-central.com/windows-vista-chkdsk.html](http://www.windows-help-central.com/windows-vista-chkdsk.html)

---

### Post by oldfred on 2010-12-17
Grub2 does not directly let you edit the menu. 

drs305 has a lot of grub2 pages and this goes over the main issues of editing titles.

Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

But I just brute force it by copying the windows boot stanza into 40_custom, edit it, and turn off osprober so you only have the one entry.

One way to fix the descriptions is to move the windows entries to 40_custom and edit title at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit title only:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

Boot and you should have two entries, test your new entry.

If it works we can turn off the osprober.
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
sudo update-grub

If you ever update or add a system change true to false and it will run the osprober again.

---

### Post by wilee-nilee on 2010-12-18
Let me see if I get this right if you click on the vista grub boot menu selection, which is the next default. You only have one vista entry in grub and the recovery name is a problem can be changed.

So is the screen after choosing the vista recovery from the grub menu defaulting to the OS, rather then the actual recovery. Two choices right one or the other.

---

### Post by oldfred on 2010-12-18
If issue is part of windows choices then it is the BCD.

I do not know BCD well as I have XP which uses boot.ini. You guys may know more about how the BCD handles boot choices.

I have saved some links on BCD editing.

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

How to fix Vista/Window 7 when the boot files are missing manual copy  & BCD edit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)

---

### Post by wilee-nilee on 2010-12-18
> **oldfred said:**
> If issue is part of windows choices then it is the BCD.

I do not know BCD well as I have XP which uses boot.ini. You guys may know more about how the BCD handles boot choices.

I have saved some links on BCD editing.

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

How to fix Vista/Window 7 when the boot files are missing manual copy  & BCD edit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)

bcdedit.exe  I think and change the boot stanzas if its not defaulting to the OS.

---

### Post by davidmclifton on 2010-12-23
Seems the chkdsk stuff worked - quirky Windows. Thanks guys!

---

### Post by garvinrick4 on 2010-12-23
Are you all sure that when OP installed Ubuntu he wanted Windows to be first in boot order
so used GUI interface Startup-manager and choose wrong boot preference. Had to make some sort of change after grub2 started ubuntu first in order. But then aqain is a Dell they
get some weird things going on with a Dell. Seems you get to far away from Dell they crack you on the knuckles.

---

### Post by davidmclifton on 2010-12-23
Nah - it still shows windows recovery as the option, just windows acts fine - it has always been pointing at the correct boot option.

---

### Post by Quackers on 2010-12-23
> **davidmclifton said:**
> Nah - it still shows windows recovery as the option, just windows acts fine - it has always been pointing at the correct boot option.

Correct. It's pointing to sda3 and that's where Vista is. The problem is that Vista wanted to run a chkdsk, it seems.
The recovery loader entry can be changed by using drs305's Title Tweaks guide (number 7) but I can't link you to it because right-click/copy is crashing firefox at the moment! I'll type it and see if it's ok

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---


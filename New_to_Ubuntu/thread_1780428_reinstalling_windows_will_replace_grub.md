---
title: "reinstalling windows will replace grub ?"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by neil_1 on 2011-06-12
i want to re install windows on the windows partition (i have a dual boot), 
my q:
will the windows install replace GRUB with its own bootloader ?
if so , how do i re-install GRUB ?

---

### Post by papibe on 2011-06-12
Yes, grub will be replaced.

Check this help page: [Recovering Ubuntu After Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

Regards.

---

### Post by sikander3786 on 2011-06-12
Yeah, installing Windows would replace Grub thus leaving your access to Windows only.

Before installation, remember that you can install Windows to a primary partition only.

After installation, you can either post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

And we would be able to give you the exact commands, just to copy&paste to your Live CD Ubuntu Terminal.

If you want to do it yourself, there is a GUI method of repairing Grub from Live CD.

[https://help.ubuntu.com/community/Grub2#Use%20Boot-Repair%20Graphical%20Tool](https://help.ubuntu.com/community/Grub2#Use%20Boot-Repair%20Graphical%20Tool)

But, most of us prefer this one.

[https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files](https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files)

---

### Post by neil_1 on 2011-06-12
if im going to use boot-repair, 
how do i know where my GRUB is installed?
this is my partition list in gparted
[http://ubuntuforums.org/attachment.php?attachmentid=194449&d=1307435120](http://ubuntuforums.org/attachment.php?attachmentid=194449&d=1307435120)

edit:
will this also work?
[http://www.bleepingcomputer.com/forums/topic244714.html](http://www.bleepingcomputer.com/forums/topic244714.html)
edit:
also , which is my boot partition ?

---

### Post by neil_1 on 2011-06-13
*bump*
sorry :(
impatient on this one cuz my dads making me install win again :/

---

### Post by wildmanne39 on 2011-06-13
> **neil_1 said:**
> *bump*
sorry :(
impatient on this one cuz my dads making me install win again :/
Boot Script

Hi, post the information from this script so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by neil_1 on 2011-06-13
> **wildmanne39 said:**
> Boot Script

Hi, post the information from this script so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   322,472,744   322,265,897   7 NTFS / exFAT / HPFS
/dev/sda3         322,472,806   534,466,484   211,993,679   5 Extended
/dev/sda5         322,472,808   364,450,589    41,977,782  83 Linux
/dev/sda6         364,450,653   372,836,519     8,385,867  82 Linux swap / Solaris
/dev/sda7         372,836,583   534,466,484   161,629,902  83 Linux
/dev/sda4         534,466,560   976,769,023   442,302,464   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        44AC0951AC093EC4                       ntfs       System Reserved
/dev/sda2        4AD40CFDD40CED4F                       ntfs       
/dev/sda4        70D2269870516F51                       ntfs       Shared
/dev/sda5        08105fb7-e050-4db4-a2c1-e625084e366f   ext4       root
/dev/sda6        6eec2b95-bc63-4e4d-ab99-b86a57ce2164   swap       
/dev/sda7        2032f439-d005-4e64-8f6c-f71cdcc5ec73   ext4       home

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set 08105fb7-e050-4db4-a2c1-e625084e366f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768
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
search --no-floppy --fs-uuid --set 08105fb7-e050-4db4-a2c1-e625084e366f
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 08105fb7-e050-4db4-a2c1-e625084e366f
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=08105fb7-e050-4db4-a2c1-e625084e366f ro   quiet splash nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 08105fb7-e050-4db4-a2c1-e625084e366f
    echo    'Loading Linux 2.6.32-32-generic ...'
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=08105fb7-e050-4db4-a2c1-e625084e366f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 08105fb7-e050-4db4-a2c1-e625084e366f
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=08105fb7-e050-4db4-a2c1-e625084e366f ro   quiet splash nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 08105fb7-e050-4db4-a2c1-e625084e366f
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=08105fb7-e050-4db4-a2c1-e625084e366f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 08105fb7-e050-4db4-a2c1-e625084e366f
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=08105fb7-e050-4db4-a2c1-e625084e366f ro   quiet splash nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 08105fb7-e050-4db4-a2c1-e625084e366f
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=08105fb7-e050-4db4-a2c1-e625084e366f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 08105fb7-e050-4db4-a2c1-e625084e366f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=08105fb7-e050-4db4-a2c1-e625084e366f ro   quiet splash nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 08105fb7-e050-4db4-a2c1-e625084e366f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=08105fb7-e050-4db4-a2c1-e625084e366f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 08105fb7-e050-4db4-a2c1-e625084e366f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 08105fb7-e050-4db4-a2c1-e625084e366f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 44ac0951ac093ec4
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=08105fb7-e050-4db4-a2c1-e625084e366f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=2032f439-d005-4e64-8f6c-f71cdcc5ec73 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=6eec2b95-bc63-4e4d-ab99-b86a57ce2164 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 155.978626251 = 167.480774656  boot/grub/core.img                             1
 170.652183533 = 183.236386816  boot/grub/grub.cfg                             2
 156.087284088 = 167.597445120  boot/initrd.img-2.6.32-24-generic              1
 156.107192993 = 167.618822144  boot/initrd.img-2.6.32-30-generic              1
 155.398193359 = 166.857539584  boot/initrd.img-2.6.32-31-generic              2
 154.399803162 = 165.785526272  boot/initrd.img-2.6.32-32-generic              2
 156.036323547 = 167.542726656  boot/vmlinuz-2.6.32-24-generic                 1
 156.042114258 = 167.548944384  boot/vmlinuz-2.6.32-30-generic                 1
 156.095016479 = 167.605747712  boot/vmlinuz-2.6.32-31-generic                 1
 156.061477661 = 167.569735680  boot/vmlinuz-2.6.32-32-generic                 1
 154.399803162 = 165.785526272  initrd.img                                     2
 155.398193359 = 166.857539584  initrd.img.old                                 2
 156.061477661 = 167.569735680  vmlinuz                                        1
 156.095016479 = 167.605747712  vmlinuz.old                                    1


```

---

### Post by gandaran on 2011-06-13
> **neil_1 said:**
> i want to re install windows on the windows partition (i have a dual boot), 
my q:
will the windows install replace GRUB with its own bootloader ?
if so , how do i re-install GRUB ?
maybe the easiest way for you is to install [easyBCD]("http://neosmart.net/dl.php?id=1") on windows to repair the dual boot grub, also another easy way is the [rescatux]("http://www.supergrubdisk.org/category/download/rescatuxdownloads/") live cd/usb, it just takes a couple clicks to fix grub.

---

### Post by coffeecat on 2011-06-13
Hi, your boot info script output (thanks for posting the link, wildmanne39 :)) shows that your Ubuntu root partition is /dev/sda5. So after you've re-installed Windows, follow sikander3786's third link. The commands for your situation would be:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

**EDIT**: forgot to mention. If you re-install Windows, the UUID of the Windows C: partition may change which means that the grub Windows entry won't work at first. What you need to do is:

1 - not panic. :wink:

2 - boot into Ubuntu on the hard drive, open a terminal, and:

```
sudo update-grub
```

Then your Windows entry *should* work.

---

### Post by neil_1 on 2011-06-13
thanks :)
from sikanders third link i have to only follow "copy livecd files " right and not "copy partition files " etc ?

---

### Post by coffeecat on 2011-06-13
Yes, that's right. Except don't bother with the 'sudo fdisk -l' in 3. We've already got that information from your boot script output. Have a look at the commands in 4 and 5, and now look at the first two commands I've posted. All I've done is to copy those commands from the link page, but adapt them for your situation: "/dev/sda5" in the first and "/dev/sda" in the second.

After you've done those two commands, all you have to do is to reboot, choose Ubuntu from the restored grub menu, boot into Ubuntu on your hard drive and then run:

```
sudo update-grub
```... to get the Windows entry working properly.

Of course, that's all after you've re-installed Windows - if you haven't done that already. :)

---

### Post by neil_1 on 2011-07-21
just for future refrence , how did you find out this
> **coffeecat said:**
> Hi, your boot info script output (thanks for posting the link, wildmanne39 :smile:)  shows that your Ubuntu root partition is /dev/sda5. So after you've  re-installed Windows, follow sikander3786's third link. The commands for  your situation would be:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by coffeecat on 2011-07-21
> **neil_1 said:**
> just for future refrence , how did you find out this

Here's a uesful link for you (instructions to reinstall grub from the live CD after Windows has overwritten the mbr):

[https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files](https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files)

All you need to do is to substitute your root partition for /dev/sdXY and hard drive designation for /dev/sdX. In your case /dev/sda5 and /dev/sda respectively.

Good luck!

---

### Post by tommpogg on 2011-07-21
> **coffeecat said:**
> Hi, your boot info script output (thanks for posting the link, wildmanne39 :)) shows that your Ubuntu root partition is /dev/sda5. So after you've re-installed Windows, follow sikander3786's third link. The commands for your situation would be:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```**EDIT**: forgot to mention. If you re-install Windows, the UUID of the Windows C: partition may change which means that the grub Windows entry won't work at first. What you need to do is:

1 - not panic. :wink:

2 - boot into Ubuntu on the hard drive, open a terminal, and:

```
sudo update-grub
```Then your Windows entry *should* work.

I have just tried this method yesterday and it worked!
So my suggestions is to do as coffeecat says

---

### Post by neil_1 on 2011-07-21
umm sorry , what i meant to ask was how coffeecat got that information from the boot info script that i posted ?:)

---

### Post by coffeecat on 2011-07-21
> **neil_1 said:**
> umm sorry , what i meant to ask was how coffeecat got that information from the boot info script that i posted ?:)

OK. :wink:

The /etc/fstab contents in the boot script output identifies your Ubuntu root partition (/) as sda5 (also a double-check with the UUID information). The menu entries in the grub.cfg file correlate with this and there is no information in the boot script output that contradicts this assumption.

---


---
title: "Windows 7 (Loader) became Windows Recovery Console (eRecovery)"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by MelvinCD7 on 2011-04-10
[B]I have installed Windows 7 Starter (factory) and Ubuntu 10.10,
 the problem is that the GRUB shows the partition of Ubuntu, the W7 and the recovery console W7, when attempting to login to Ubuntu no problem, but when trying to enter W7 it enters the recovery console as well as which is especially for recovery .. I have an Acer Aspire one Mini 532h[/B]

---

### Post by Rubi1200 on 2011-04-10
Just to be clear about this:

you have 3 entries on your GRUB menu:

1. Ubuntu --- boots normally

2. W7 --- boots to the recovery console

3. W7 Recovery --- boots to...?

So far so good?

I recommend you try booting into the entry labeled as W7 Recovery and see what happens.

If I am right, GRUB got confused between the actual Windows install and the recovery partition.

If you are able to boot into Windows normally from the recovery partition, I think we can find a way to fix it so that becomes the default and is less confusing.

Let me know what happens please.

---

### Post by MelvinCD7 on 2011-04-10
The (3) W7 Recovery and (2) W7 boots to Recovery, both of them boot to the Recovery console.
I have tried reinstalling the W7 and it doesn't fix it!

---

### Post by Rubi1200 on 2011-04-10
If a reinstall didn't help, then that is rather strange.

The best thing to do right now is post the results of a diagnostic script that will help us figure out what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by MelvinCD7 on 2011-04-11
I almost forget it, my Ubuntu system is working well, the problem is in W7

```
     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /GRLDR

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    25,382,699       208,845   7 HPFS/NTFS
/dev/sda3          25,382,700   270,357,884   244,975,185   7 HPFS/NTFS
/dev/sda4         270,358,526   312,580,095    42,221,570   5 Extended
/dev/sda5         270,358,528   312,580,095    42,221,568  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5A18E85218E82EA7                       ntfs       PQSERVICE                     
/dev/sda2        E4F4E89EF4E873E8                       ntfs       SYSTEM RESERVED               
/dev/sda3        3C9AA3469AA2FC10                       ntfs       Acer                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        d5ada098-10eb-41eb-a650-3668825771e7   ext4                                     
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
search --no-floppy --fs-uuid --set d5ada098-10eb-41eb-a650-3668825771e7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set d5ada098-10eb-41eb-a650-3668825771e7
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d5ada098-10eb-41eb-a650-3668825771e7
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=d5ada098-10eb-41eb-a650-3668825771e7 ro  vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d5ada098-10eb-41eb-a650-3668825771e7
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=d5ada098-10eb-41eb-a650-3668825771e7 ro single  vga=773
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d5ada098-10eb-41eb-a650-3668825771e7
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=d5ada098-10eb-41eb-a650-3668825771e7 ro  vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d5ada098-10eb-41eb-a650-3668825771e7
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=d5ada098-10eb-41eb-a650-3668825771e7 ro single  vga=773
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d5ada098-10eb-41eb-a650-3668825771e7
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=d5ada098-10eb-41eb-a650-3668825771e7 ro  vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d5ada098-10eb-41eb-a650-3668825771e7
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=d5ada098-10eb-41eb-a650-3668825771e7 ro single  vga=773
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d5ada098-10eb-41eb-a650-3668825771e7
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=d5ada098-10eb-41eb-a650-3668825771e7 ro  vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d5ada098-10eb-41eb-a650-3668825771e7
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=d5ada098-10eb-41eb-a650-3668825771e7 ro single  vga=773
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d5ada098-10eb-41eb-a650-3668825771e7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d5ada098-10eb-41eb-a650-3668825771e7 ro  vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d5ada098-10eb-41eb-a650-3668825771e7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d5ada098-10eb-41eb-a650-3668825771e7 ro single  vga=773
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d5ada098-10eb-41eb-a650-3668825771e7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set d5ada098-10eb-41eb-a650-3668825771e7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5a18e85218e82ea7
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set e4f4e89ef4e873e8
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
UUID=d5ada098-10eb-41eb-a650-3668825771e7 /               ext4    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 151.4GB: boot/grub/core.img
 151.1GB: boot/grub/grub.cfg
 142.3GB: boot/initrd.img-2.6.35-22-generic
 141.9GB: boot/initrd.img-2.6.35-24-generic
 141.8GB: boot/initrd.img-2.6.35-25-generic
 148.3GB: boot/initrd.img-2.6.35-27-generic
 144.7GB: boot/initrd.img-2.6.35-28-generic
 152.1GB: boot/vmlinuz-2.6.35-22-generic
 152.1GB: boot/vmlinuz-2.6.35-24-generic
 152.2GB: boot/vmlinuz-2.6.35-25-generic
 153.2GB: boot/vmlinuz-2.6.35-27-generic
 152.2GB: boot/vmlinuz-2.6.35-28-generic
 144.7GB: initrd.img
 148.3GB: initrd.img.old
 152.2GB: vmlinuz
 153.2GB: vmlinuz.old
```

---

### Post by drs305 on 2011-04-11
The two Windows entries in the Grub2 menu point to different partitions, so I think the problem is with the information in the Windows boot files. Since Vista/7 don't use boot.ini the boot info script can't read what the Windows boot files are telling the system to do.

I believe you have to use bcedit.exe or EasyBCD to inspect/alter this information, but if you aren't familiar with these please wait until a Windows user posts here.

---

### Post by Its_Rishi on 2011-04-11
If you have a windows 7 disk then boot your system with it and select "Repair your Computer" at the front page after booting from cd and select "Startup Problem" wait for a while it resolves your problem....

---

### Post by MelvinCD7 on 2011-04-11
Thanks [[COLOR=#D40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945") I will wait
I cant do it [Its_Rishi]("http://ubuntuforums.org/member.php?u=1166974") my computes is an Mine Acer, i have not Optical ROMS, i just can reinstall it from the eReovery partition

---

### Post by Mark Phelps on 2011-04-12
So, if you have Ubuntu in its own partition, then why is there a GRLDR folder in your Win7 partition? 

That folder holds the GRUB4DOS loader -- a version of GRUB that runs in Windows and is used to launch Ubuntu when it is installed via Wubi.

---

### Post by David_UK on 2011-04-12
I have 10.10 dual booted with Win7 on Acer Aspire One D250 netbook.
My Vista entry is the acer recovery partition.
My Win7 entry is windows 7.
If I enter the vista entry from grub, the recovery console over-writes the grub chain and the multiboot breaks.
MelvinCD7 - did the same thing happen to you in post #3?

---

### Post by jtarin on 2011-04-12
> **MelvinCD7 said:**
> Thanks [[COLOR=#D40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945") I will wait
I cant do it [Its_Rishi]("http://ubuntuforums.org/member.php?u=1166974") my computes is an Mine Acer, i have not Optical ROMS, i just can reinstall it from the eReovery partitionHow did you install Ubuntu? USB stick?

---

### Post by MelvinCD7 on 2011-04-12
[Mark Phelps]("http://ubuntuforums.org/member.php?u=311399") I don't know why it is there! The last thing I did to my windows 7 was try to crack it, that was the last time i saw W7
[David_UK]("http://ubuntuforums.org/member.php?u=215794") that never happen to me, but I used to have the same GRUB configuration as you have
[jtarin]("http://ubuntuforums.org/member.php?u=738123") Yes, this is how I installed Ubuntu

Guys, I think my GRUB configuration is not good, because my windows is in the SDA3 but the GRUB only boot to SDA1(Recovery) and SDA2(a partition named SYSTEM RESERVED), so how can I add SDA3 to my GRUB entries?

---

### Post by jtarin on 2011-04-12
> **MelvinCD7 said:**
> [Mark Phelps]("http://ubuntuforums.org/member.php?u=311399") I don't know why it is there! The last thing I did to my windows 7 was try to crack it, that was the last time i saw W7
[David_UK]("http://ubuntuforums.org/member.php?u=215794") that never happen to me, but I used to have the same GRUB configuration as you have
[jtarin]("http://ubuntuforums.org/member.php?u=738123") Yes, this is how I installed Ubuntu

Guys, I think my GRUB configuration is not good, because my windows is in the SDA3 but the GRUB only boot to SDA1(Recovery) and SDA2(a partition named SYSTEM RESERVED), so how can I add SDA3 to my GRUB entries?Here's a [link]("https://help.ubuntu.com/community/Grub2") to Grub2 Ubuntu documentation. You might try to reinstall Grub and see if it picks up your sda3. You might also boot with the USB (as a Live CD) and when on the desktop use Gparted to look at your partitions and see which ones are marked active.

---

### Post by David_UK on 2011-04-13
> **MelvinCD7 said:**
> The last thing I did to my windows 7 was try to crack it, that was the last time i saw W7
Can you give us details of what you tried to do to windows, and was this before or after GRUB2 was installed?
Also, can you confirm if there was (even if it had not been set up) a dual boot with Android on your computer when you first had it (there may be a sticker on the front with the green android man on it)?  Thanks

---

### Post by oldfred on 2011-04-13
Windows has to boot to the system/recovery partition sda2 which is normally hidden in windows. But the /grldr in your windows is evidence of you trying to modify windows.

We cannot help you unless you have a full legal copy of windows.

---

### Post by MelvinCD7 on 2011-04-13
Thanks [jtarin]("http://ubuntuforums.org/member.php?u=738123"), you're the man! I'm OK now everything is working well, that help me... 

[oldfred]("http://ubuntuforums.org/member.php?u=852711") I have an full legal copy (Starter Ed) , I've erased the the old (the Illegal one W7 Ultimate) and reinstalled the one who comes with my laptop
[David_UK]("http://ubuntuforums.org/member.php?u=215794") haha no, there's not the green android man behind what I've done hahaha

How can I close this thread?

---

### Post by drs305 on 2011-04-13
> **MelvinCD7 said:**
> How can I close this thread?

You can mark the thread 'Solved' via the 'Thread Tools' link near the upper right of the first post if you have no more issues you would like to discuss here. 

We generally prefer not to close threads. Of course, as *oldfred* has touched on, a thread discussing matters not permitted by the Forum Code of Conduct can and will be closed or jailed for that reason. ;-)

---


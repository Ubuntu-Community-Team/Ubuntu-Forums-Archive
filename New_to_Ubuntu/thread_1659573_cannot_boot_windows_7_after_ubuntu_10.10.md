---
title: "cannot boot windows 7 after ubuntu 10.10"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by ptoul on 2011-01-04
Hello everyone, 
 
I have a problem with win7 after installing Ubuntu 10.10 in my mini notebook. First i had only XP and migrate to Win7. Then install Ubuntu and now i can't boot Win7. 
The win7 partition is located on the same disk (Mounted from ubuntu desktop, 102GB Filesystem).
Attached is the bootscript result:
 
Please Help !!!

---

### Post by Hippytaff on 2011-01-04
Hello and welcome
 
For some reason I can't view the attched file, you might want to post the results in code tags using # icon.
 
In the mean time try opening a terminal (CTRL+ALT+T) and typing
```

sudo update-grub

```

---

### Post by coffeecat on 2011-01-04
@ptoul, as Hippytaff says, it is better to post output from scripts like the boot script in code tage, but I have had more luck in reading it. For the benefit of anyone else helping, here it is:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 42535160 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

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

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     8,390,655     8,388,608  12 Compaq diagnostics
/dev/sda2           8,392,702   113,248,255   104,855,554   5 Extended
/dev/sda5          97,247,232   113,248,255    16,001,024  82 Linux swap / Solaris
/dev/sda6           8,392,704    97,245,183    88,852,480  83 Linux
/dev/sda3         113,248,256   312,578,047   199,329,792   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16039018496 bytes
255 heads, 63 sectors/track, 1949 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    31,326,207    31,326,145   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        94207EF3207EDC24                       ntfs       RECOVERY                      
/dev/sda2: PTTYPE="dos" 
/dev/sda3        0E165361165348BB                       ntfs                                     
/dev/sda5        5d4cc7ac-5c3c-4bde-af0b-f39f633f4228   swap                                     
/dev/sda6        ddb6cef5-c47c-4780-bbda-35dd759e70bf   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        90B0-2F64                              vfat       CORSAIR                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/CORSAIR           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
search --no-floppy --fs-uuid --set ddb6cef5-c47c-4780-bbda-35dd759e70bf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set ddb6cef5-c47c-4780-bbda-35dd759e70bf
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set ddb6cef5-c47c-4780-bbda-35dd759e70bf
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=ddb6cef5-c47c-4780-bbda-35dd759e70bf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set ddb6cef5-c47c-4780-bbda-35dd759e70bf
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=ddb6cef5-c47c-4780-bbda-35dd759e70bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set ddb6cef5-c47c-4780-bbda-35dd759e70bf
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ddb6cef5-c47c-4780-bbda-35dd759e70bf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set ddb6cef5-c47c-4780-bbda-35dd759e70bf
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ddb6cef5-c47c-4780-bbda-35dd759e70bf ro single 
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
    search --no-floppy --fs-uuid --set ddb6cef5-c47c-4780-bbda-35dd759e70bf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set ddb6cef5-c47c-4780-bbda-35dd759e70bf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 94207ef3207edc24
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
UUID=ddb6cef5-c47c-4780-bbda-35dd759e70bf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5d4cc7ac-5c3c-4bde-af0b-f39f633f4228 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  28.4GB: boot/grub/grub.cfg
   5.0GB: boot/initrd.img-2.6.35-22-generic
   5.1GB: boot/initrd.img-2.6.35-23-generic
  17.3GB: boot/vmlinuz-2.6.35-22-generic
  17.3GB: boot/vmlinuz-2.6.35-23-generic
   5.1GB: initrd.img
   5.0GB: initrd.img.old
  17.3GB: vmlinuz
  17.3GB: vmlinuz.old
```Your Windows 7 installation is on sda1 and sda3, sda1 presumably being the Windows 7 boot partition. The immediate problem seems to be that grub code has somehow got into the boot sector of sda1. It has no business being there and is probably interfering with the Windows 7 boot files. You need to run the recovery utility from your Windows 7 installation or repair disc. What I think you need to do is to choose the command prompt and run 'bootrec /FixBoot' to repair the boot sector. See:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Be careful not to run fixmbr, otherwise this will overwrite grub stage 1 in the mbr (where it needs to be) and you'll then have to repair grub.

---

### Post by ajgreeny on 2011-01-04
I have also looked at the fdisk output of the boot script file and niote that maybe the Windows OS is on a logical partition.
Partition  Boot         Start           End          Size  Id System

> /dev/sda1    *          2,048     8,390,655     8,388,608  12 Compaq diagnostics
/dev/sda2           8,392,702   113,248,255   104,855,554   5 Extended
/dev/sda5          97,247,232   113,248,255    16,001,024  82 Linux swap / Solaris
/dev/sda6           8,392,704    97,245,183    88,852,480  83 Linux
/dev/sda3         113,248,256   312,578,047   199,329,792   7 HPFS/NTFS

sda1 is the compaq disgnostics partition, unless fdisk has got that wrong, sda2 is an extended partition, and therefore, I think, sda3, your windows OS must be in a logical partition, which as I understand things will mean that it is (almost) impossible to boot.  I believe windows in a logical partition can be forced to boot, but it is certainly not straightforward, nor easy.

How to deal with that, I haven't the faintest idea, I'm afraid.  However I have posted here in the hope that others that come upon this thread may be able to help you in much more detail.

---

### Post by coffeecat on 2011-01-04
> **ajgreeny said:**
> sda1 is the compaq disgnostics partition,

Oops, you're quite right - missed that.

> **ajgreeny said:**
>   unless fdisk has got that wrong, sda2 is an extended partition, and  therefore, I think, sda3, your windows OS must be in a logical  partition, 

No. By convention, and by the way the mbr  partition table works, partitions numbered 1 - 4 are either primary or  extended. logicals are always numbered 5 and upwards. The fdisk output in the bootscript output shows sda3 as being outside sda2, so we don't have one of these spurious primary within an extended partition problems that have been cropping up recently.

@ptoul, I'll have another look at your bootscript.

**EDIT**: The problems with Windows in sda3 are that a> there are no boot files in the boot sector in sda3 and, b> there is no grub menu entry for sda3. The second is a result of the first. You'll need to use the Windows 7 repair disc as before to install boot files into sda3, I guess.

---

### Post by ajgreeny on 2011-01-04
> No. By convention, and by the way the mbr  partition table works,  partitions numbered 1 - 4 are either primary or  extended. logicals are  always numbered 5 and upwards. The fdisk output in the bootscript output  shows sda3 as being outside sda2, so we don't have one of these  spurious primary within an extended partition problems that have been  cropping up recently.
Thanks for that Coffeecat.

I did wonder about the order in which the partitions were listed, ie sda3 after all those other higher numbered partitions, but I admit I was not aware of the conventions in enough detail to be certain about things.

---

### Post by coffeecat on 2011-01-04
> **ajgreeny said:**
> I did wonder about the order in which the partitions were listed, ie sda3 after all those other higher numbered partitions, but I admit I was not aware of the conventions in enough detail to be certain about things.

Yes, the partitions are quite out of order - even to the extent of sda6 coming before sda5 on the disc. How that happened I cannot guess. The numbering convention is hugely useful in tracking down these problems.

Can you see anything else in the bootscript output that may be relevant?

---

### Post by oldfred on 2011-01-04
We have seen where the script for some reason has missed  seeing
/Windows/System32/winload.exe
But if it is not in sda3, then sda3 was just a data partition and the full install was in sda2 which would be where in a normal layout it would be. Check and see if you have /window/system32 folder in your sda3 partition?

Somehow the main install was then overwritten, and converted to the extended partition.

---

### Post by Bucky Ball on 2011-01-04
> **oldfred said:**
> We have seen where the script for some reason has missed  seeing
/Windows/System32/winload.exe
But if it is not in sda3, then sda3 was just a data partition and the full install was in sda2 which would be where in a normal layout it would be. Check and see if you have /window/system32 folder in your sda3 partition?

Somehow the main install was then overwritten, and converted to the extended partition.

A known issue with current 10.10 kernel. It is screwing up a few things. Avoid. Kernel in question is:

2.6.35-24

Go for 10.04 LTS for the moment or avoid updating the kernel to this one. There is a bug report regarding this issue and unfortunately there are a few new users dropping into the pit. That pit being that the Ubuntu 10.10 install is killing Windows (especially when choosing install side by side with other OS). :confused:

---

### Post by coffeecat on 2011-01-04
> **Bucky Ball said:**
> A known issue with current 10.10 kernel. It is screwing up a few things. Avoid. Kernel in question is:

2.6.35-24

Go for 10.04 LTS for the moment or avoid updating the kernel to this one. There is a bug report regarding this issue and unfortunately there are a few new users dropping into the pit. That pit being that the Ubuntu 10.10 install is killing Windows (especially when choosing install side by side with other OS). :confused:

Do you have a link to a bug report for a kernel destroying Windows? How would a kernel destroy Windows? Perhaps the  bug that you're  referring to is the design flaw in the Ubiquity installer - the install side-by-side option. In fact there are several bugs registered on Launchpad for this issue.

---

### Post by Bucky Ball on 2011-01-04
> **coffeecat said:**
>  Perhaps the  bug that you're  referring to is the design flaw in the Ubiquity installer - the install side-by-side option. In fact there are several bugs registered on Launchpad for this issue.

In this instance, yep, that's what I'm referring to. There is also the small issue of that kernel killing Broadcom wireless card config and other oddities. I have seen bug report for that one, sure you won't have too much trouble finding it (I don't have it bookmarked).

There is a rather long thread on the forums with the title something like:

> Kernel 2.6.35-24 is WRONG!!!

... or words to that effect. There is a link to bug reports there.

---

### Post by dsmo223 on 2011-01-04
I am currently running that kernel, with a dual boot with windows 7 and a broadcom card, but haven't had any problems yet, should I change kernels somehow, or just go with it since it hasn't messed up anything yet?

---

### Post by Bucky Ball on 2011-01-04
I'd say go with it if you have no problems. It doesn't seem to be all Broadcom cards but lots.

---

### Post by milkrut on 2011-01-05
Hi guys,

I just installed ubuntu 10.10 yesterday. And it boots straight into ubuntu instead of offering me a choice of OS (might be one of the few noobies to be caught up in this).

What can I do to get the windows 7 boot up?

Cheers.

---

### Post by oldfred on 2011-01-05
milkrut, Please start a new thread and post your results.txt from boot script. This thead is not solved and we do not want to have two different sets of questions & answers in one thread.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---


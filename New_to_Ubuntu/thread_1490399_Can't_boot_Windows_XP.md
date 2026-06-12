---
title: "Can't boot Windows XP"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by Imatech64 on 2010-05-22
Hello everyone,

I made the huge mistake of updating 9.10 on both my laptop and my desktop before reading any threads in the forum.....

Laptop
Total mess, sytem frozen ...generally after the update the whole system crashed. I tried reinstall from LiveCD as well the alternate without any success.
Result: I formatted the HD with XP and reinstalled 9.10.....everything back to normal and I will not change that. 

Desktop
The updated went right, I am in fact now typing through it.
The trouble here is that even if I see the XP in the Grub command...but when trying to run XP the screen goes black with the cursor up left and freeze.

Anybody has any ideas or relevant posts/threads to propose?


Thanks

---

### Post by vooolt on 2010-05-22
Try to insert the windows CD and choose R to repair the operating system.

---

### Post by Elfy on 2010-05-22
Can you go here - [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions there please.

---

### Post by strom83 on 2010-05-22
Note, if you use Windows Setup to repair your boot record it is very likely to overwrite your boot-manager. This again means you might not be able to start Ubuntu. In that case you would have to reinstall Grub which is probably the solution in your case anyway. I wouldn't recommend using Windows Setup.

Probably, you should first find out why Grub is freezing. To do this you might want to know which version of Grub you are using. This would also help us to help you solve your problem.

bye

strom

---

### Post by rayoung02 on 2010-05-22
I have the same problem now after I upgraded to 10.04. I'll let you know if I get anywhere.

---

### Post by bcbc on 2010-05-22
> **rayoung02 said:**
> I have the same problem now after I upgraded to 10.04. I'll let you know if I get anywhere.

See this: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)


Imatech64: when you formatted your drive with XP - do you mean you reinstalled XP? Or are you referring to erasing Ubuntu. If the latter, this doesn't fix windows if you've overwritten the boot sector.

---

### Post by Imatech64 on 2010-05-23
First of all thanks for the kind replies...

When I say I reinstalled XP , I mean I formatted the whole (and unique) HD of the laptop with the windows XP setup CD... and then reinstalled ubuntu 9.10 as dual boot with XP. 
The vice versa operation , i.e. formatting the whole HD in XP is simply ...impossible. I have tried various liveCD (having check them all) without success.

The trouble is not on my laptop though, but on the desktop where the upgrade to 10.04 worked (apparently) OK up to the point of the none running XP.

The answers on that point are comfusing...do you mean I should repair XP with the R key and then reinstall grub of ubuntu?

Thanks again

---

### Post by Imatech64 on 2010-05-23
Sorry , I just found an error on my post... please read :

formatting the whole disk in ubuntu (only) is impossible

---

### Post by geeklove2rock on 2010-05-23
in my opinion why don't you go for you window repair option by inserting windows cd!!!!!!!!!
if that didn't work then go for format and that may be better
newly fresh window 
enjoy

---

### Post by bcbc on 2010-05-23
> **Imatech64 said:**
> First of all thanks for the kind replies...

When I say I reinstalled XP , I mean I formatted the whole (and unique) HD of the laptop with the windows XP setup CD... and then reinstalled ubuntu 9.10 as dual boot with XP. 
The vice versa operation , i.e. formatting the whole HD in XP is simply ...impossible. I have tried various liveCD (having check them all) without success.

The trouble is not on my laptop though, but on the desktop where the upgrade to 10.04 worked (apparently) OK up to the point of the none running XP.

The answers on that point are comfusing...do you mean I should repair XP with the R key and then reinstall grub of ubuntu?

Thanks again

Right - I reread your post and that's what you said... so it seems likely that you overwrote the windows boot sector with grub. If this is the case, then you don't have to reinstall grub or ubuntu - you need to fix windows.

So that link I gave tells you a) how to confirm the problem by running the bootinfoscript and b) how to fix it. 

Go to that link, and if you find that's not your problem, post back the results of the bootinfoscript (forestpiskie also provided a direct link for the script).

If you have trouble with any part of the fix or don't understand something, post back here.

---

### Post by Imatech64 on 2010-05-23
Here is the result.txt:

     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 272351 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 272351 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 272351 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   303,532,109   303,532,047  83 Linux
/dev/sdc2         303,532,110   312,576,704     9,044,595   5 Extended
/dev/sdc5         303,532,173   312,576,704     9,044,532  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4013 MB, 4013948928 bytes
5 heads, 32 sectors/track, 48998 cylinders, total 7839744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          8,064     7,839,743     7,831,680   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        94A8764DA8762DBC                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1878CA7678CA5264                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        a3fa4338-d69d-444a-b2ba-900a47e75793   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        7b6934df-40fa-4bf5-8733-a80899f64565   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        F4AB-C9B4                              vfat       KINGSTON                      
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sdd1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set a3fa4338-d69d-444a-b2ba-900a47e75793
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set a3fa4338-d69d-444a-b2ba-900a47e75793
set locale_dir=($root)/boot/grub/locale
set lang=el
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
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a3fa4338-d69d-444a-b2ba-900a47e75793
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a3fa4338-d69d-444a-b2ba-900a47e75793 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.32-22-generic (&#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a3fa4338-d69d-444a-b2ba-900a47e75793
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a3fa4338-d69d-444a-b2ba-900a47e75793 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a3fa4338-d69d-444a-b2ba-900a47e75793
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=a3fa4338-d69d-444a-b2ba-900a47e75793 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.31-21-generic (&#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a3fa4338-d69d-444a-b2ba-900a47e75793
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=a3fa4338-d69d-444a-b2ba-900a47e75793 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a3fa4338-d69d-444a-b2ba-900a47e75793
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a3fa4338-d69d-444a-b2ba-900a47e75793
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 94a8764da8762dbc
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=a3fa4338-d69d-444a-b2ba-900a47e75793 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=7b6934df-40fa-4bf5-8733-a80899f64565 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   5.0GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.31-21-generic
   1.5GB: boot/initrd.img-2.6.32-22-generic
   1.1GB: boot/vmlinuz-2.6.31-21-generic
   1.5GB: boot/vmlinuz-2.6.32-22-generic
   1.5GB: initrd.img
   1.5GB: initrd.img.old
   1.5GB: vmlinuz
   1.1GB: vmlinuz.old

---

### Post by Imatech64 on 2010-05-23
Problem is now solved through the second link given...

Thank you so much for the support

---

### Post by bcbc on 2010-05-23
Yes you installed grub2 in the windows partition. You need to repair the boot sector.

There are two methods described in this [link]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector"). The first uses the tool 'testdisk' - it allows you to simply copy the backup boot sector over the damaged boot sector - problem solved.

In some cases, perhaps due to some prior corrective action attempts, the backup boot sector is the same as the damaged sector. In this case, you need to use the windows repair cd or install dvd. The link describes what to do. With XP you have to run fixboot (not fixmbr).

If you have any questions about the repair steps, post back here i.e. don't do something if you are not sure.

---

### Post by Imatech64 on 2010-05-23
Thanks again for the valuable answer and link.

In my case , I installed testdisk through the synapicts and followed the different steps mentioned in you link.

Already booted twice with 100% success in both XP and ubuntu 10.04.

---

### Post by bcbc on 2010-05-23
> **Imatech64 said:**
> Problem is now solved through the second link given...

Thank you so much for the support

Oh great - that was quick :) I was still typing instructions.

---


---
title: "Can I make this drive bootable (again) without losing data?"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by Glkanter on 2011-04-16
It's a long story, but this drive won't boot. It's not even a week old.

It worked just fine until I decided to load Ubuntu 10.10 onto a 2nd hard drive on my system. (Please don't ask why I did that. It's a long story.) The install completed normally, but the restart hung up with the cursor blinking just below the top left corner of the monitor. No matter what combination of the 2 drives or single drive I tried, I couldn't get booted.

I tried changing flags with G-Parted, but that didn't help either. I certainly may have set the flags wrong.

So, is there anything I can do that will make this drive bootable again, without losing any configuration settings or other data? I've attached a photo from Clonezilla which I think is very readable.

At this point, the other drive boots into Linux, and this drive can be seen by Linux. It just won't boot, and yes, it has Linux loaded on it.

Thanks so much!

---

### Post by lmarmisa on 2011-04-16
The size of the damaged partition /dev/sda1 seems very small (only 1 Mbyte). I suppose there is no data stored there.

Do you have an Ubuntu Live CD?. You will need one for fixing your problem.

Best regards,

Luis

---

### Post by lmarmisa on 2011-04-16
Did you install Ubuntu with a separate boot partition?. Is /dev/sda1 the boot partition?

---

### Post by Glkanter on 2011-04-16
> **lmarmisa said:**
> The size of the damaged partition /dev/sda1 seems very small (only 1 Mbyte). I suppose there is no data stored there.

Do you have an Ubuntu Live CD?. You will need one for fixing your problem.

Best regards,

Luis

Is this it: "Ubuntu 10.10 "Maverick Meerkat" - Release i386"? It's the disk I used to install, and it also runs Ubuntu without installing. I didn't see anything else on the internet.

I had Ubuntu partition the drive when it was installed last wek. Unless Ubuntu put something in that 1 MB, it's empty.

Thanks, again!

---

### Post by lmarmisa on 2011-04-16
You say that "the other drive boots into Linux (Ubuntu?) and this drive can be seen from Linux".

I would like to know if both drives have installed the same version of Ubuntu 10.10.

If both versions are the same you will not need to use the Ubuntu Livd CD because you could use the Ubuntu operating system that is running on the second drive.

---

### Post by Glkanter on 2011-04-16
Yes, the exact same disk was used for both.

Thanks,

Garry

---

### Post by lmarmisa on 2011-04-16
Thanks for your info.

Please, boot your system from the Ubuntu stored in your second hard drive, open a terminal, type this command and post here the result (using copy & paste):

```

sudo fdisk -l

```

I will recommend later a first command trying to repair the partition and a diagnosis for your system.

---

### Post by Glkanter on 2011-04-16
You know, I left out one part of the story...

For 5 days, the system booted directly into Ubuntu. Then Friday, I believe, I downloaded and installed some updates. At that point (and probably because the 1 TB drive had Windows Vista on it from it's previous life - this is the drive that now boots into Ubuntu), I had to respond to a Grub menu each time.

That's how it was just prior to me causing both drives to be unbootable.

And to clarify, the system would not boot *or* go to the Grub selector, rather, the cursor in the top left corner just blinked endlessly.

Thanks!

---

### Post by lmarmisa on 2011-04-16
Ok, Garry.

Then boot into the Ubuntu Live CD and type the command:

```

sudo fdisk -l

```

---

### Post by Glkanter on 2011-04-16
> **lmarmisa said:**
> Thanks for your info.

Please, boot your system from the Ubuntu stored in your second hard drive, open a terminal, type this command and post here the result (using copy & paste):

```

sudo fdisk -l

```I will recommend later a first command trying to repair the partition and a diagnosis for your system.

Here are the results...

glkanter@Garry-System:~$ sudo fdisk -l
[sudo] password for glkanter: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00055b37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      118255   949880832   83  Linux
/dev/sda2          118255      121602    26878977    5  Extended
/dev/sda5          118255      121602    26878976   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT
glkanter@Garry-System:~$

---

### Post by Glkanter on 2011-04-16
Let me try to clarify again:

The system was working fine, booting to Ubuntu.

Updates caused Grub to show up.

With my 2.0 TB in the PC, I loaded Ubuntu on the 1 TB from the Live disk. This wiped out the old Windows disk - as intended. It also made both drives unbootable, which was not intended.

I installed Ubuntu, once again, from the Live disk onto the 1 TB drive. This time, there were no other drives in the system.

The 1 TB Ubuntu works fine. It boots without Grub. I reconnected the 2.0 TB drive, and Ubuntu sees it, but I don't believe it is part of the file system.

The copy & paste above is from the system being booted normally by the 1 TB drive.

Hope this makes things easier to follow.

Thanks!

---

### Post by lmarmisa on 2011-04-16
Well.

I see two hard drives. Their sizes are 1 Tbyte (/dev/sda) and 2 Tbytes (/dev/sdb).

The problem of the "damaged" partition is located in the 2 Tbytes unit. This hard drive is using a strange [GUID partition table]("http://en.wikipedia.org/wiki/GUID_Partition_Table").

I would like to get more information about your system. Please, visit the page [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) run the Boot Info Script and post here the results (follow the instructions).

---

### Post by K_45 on 2011-04-16
Run

gksu gparted

then format the 2TB drive. That should fix it. Its using GPT instead of MBR because MBR cannot boot off 2TB disks and Fdisk does not "understand" this GUID. So use Gparted.

---

### Post by lmarmisa on 2011-04-16
> **K_45 said:**
> Run

gksu gparted

then format the 2TB drive. That should fix it. Its using GPT instead of MBR because MBR cannot boot off 2TB disks and Fdisk does not "understand" this GUID. So use Gparted.

Hmmm. I see a partition named Gerry Data on the 2 TB drive. So, do not format anything at the moment.

---

### Post by K_45 on 2011-04-16
> **lmarmisa said:**
> Hmmm. I see a partition named Gerry Data on the 2 TB drive. So, do not format anything at the moment.

The screenshot isn't very clear. If that partition is on the 2TB drive, then I'd copy it to the 1TB drive and then format.

---

### Post by lmarmisa on 2011-04-16
I have found the tool gptsync that could solve the problem.

This is its man:

```

gptsync(8)                           rEFIt                          gptsync(8)

NAME
       gptsync - GPT partition table to MBR partition table synchronisation

SYNOPSIS
       gptsync [-q] [-t] device

DESCRIPTION
       gptsync  reads  the  GPT partition table on device and synchronises the
       legacy MBR partition table with the GPT partition table. The MBR parti&#8208;
       tion table can hold only 4 partitions.

       Legacy bootloaders or operating systems that do not support GPT require
       an MBR partition table; this is typically the case when using  GRUB  or
       LILO on an Intel-based Apple machine.

OPTIONS
       -q     Do not print any message, do not prompt to modify the MBR.

       -t     Truncate partitions starting or expending beyond 2 TiB (MBR lim&#8208;
              itation).  Default is to ignore such partitions.

AUTHOR
       gptsync was written by Christoph Pfisterer.

       This manual page was written by Junichi Uekawa <dancer@debian.org>  and
       Julien  BLACHE <jblache@debian.org>, for the Debian Project (but may be
       used by others).

Debian                           2008 July 24                       gptsync(8)


```The tool gptsync is included in the repositories of Ubuntu 10.10.

You can install it typing this command:

```

sudo apt-get install gptsync

```I think that this command could repair the problem related to the 2TB hard drive:

```

sudo gptsync /dev/sdb

```

---

### Post by Glkanter on 2011-04-16
I can't thank you all enough for the help. I have to take a break to visit with some real life human beings. I'm not sure when I will return.

Thank you!

Garry

---

### Post by yetiman64 on 2011-04-16
> **lmarmisa said:**
> Well.

I see two hard drives. Their sizes are 1 Tbyte (/dev/sda) and 2 Tbytes (/dev/sdb).

The problem of the "damaged" partition is located in the 2 Tbytes unit. This hard drive is using a strange [GUID partition table]("http://en.wikipedia.org/wiki/GUID_Partition_Table").

I would like to get more information about your system. Please, visit the page [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) run the Boot Info Script and post here the results (follow the instructions).

The script linked above is a very good idea to use here OP, It gives out a lot of important system info for any boot related problems. If you use it please put the output in code tags (use the # button in the reply editor to do so).

A good guide to its use, is linked to in my sig, link No. 1.

---

### Post by Glkanter on 2011-04-17
So, should I run that infoscript, or should I attempt the fix using gptsync?

Thank you,

Garry

---

### Post by Glkanter on 2011-04-17
I haven't mentioned it on this thread, but my main goal is to use the 2 TB as my primary drive. It is SATA 3.0, running at 6 Gbits/sec. That's twice the throughput of SATA 2.0. Yes, my MB supports SATA 3.0.

Then, since I have the 1 TB drive (plus another 250 GB drive), I want to make an exact bootable backup copy of my entire Ubuntu system (including data) on the 1 TB drive.

I figure I could make that backup once a week (using Clonezilla, it will take an hour or so), and copy any new or changed data to the 250 GB automatically each night. Or a strategy similar to this.

But my first priority is to make the 2 TB my functioning system again. I've customized it and tweaked it for almost a week (many fun, late nights), and I would hate to lose all that.

Once this drive is back on line, I'll return to my original thread about the best use of Clonezilla.

Thanks, everyone!

---

### Post by yetiman64 on 2011-04-17
> **Glkanter said:**
> So, should I run that infoscript, or should I attempt the fix using gptsync?

Thank you,

Garry

Having looked over the thread again I would suggest you run the boot info script and post the output here as it will give helpers a much fuller picture of your setup.

 You mention in the first post loading Ubuntu to a second drive, do you have any other OSes installed? (not mentioned so far). The boot infoscript will fill in any gaps for us. If nothing bad shows up with it besides the presence of a GPT then the other tool may then be of use. 

My opinion is for you to gather as much useful data on your setup rather than running tools that may or may not be necessary. Good luck. yetiman64

---

### Post by oklokl on 2011-04-17
[http://cafe.daum.net/candan/HfuW/29](http://cafe.daum.net/candan/HfuW/29) 
Korean My Homepage

---

### Post by Glkanter on 2011-04-17
I tried to use 'code'. I've also attached the results file. Should report only Ubuntu 10.10 on each drive...

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 1296335536 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1           2,048         4,095         2,048 System/Boot Partition
/dev/sda2           4,096   102,404,095   102,400,000 Linux or Data
/dev/sda3   3,853,268,992 3,907,028,991    53,760,000 Linux Swap
/dev/sda4     102,404,096   921,604,095   819,200,000 Linux or Data

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,899,763,711 1,899,761,664  83 Linux
/dev/sdb2       1,899,765,758 1,953,523,711    53,757,954   5 Extended
/dev/sdb5       1,899,765,760 1,953,523,711    53,757,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        e5a23a3c-cbda-4272-a235-305857ed8e7d   ext4                                     
/dev/sda3        cc091b49-62b3-498d-ad61-4a75133eac4a   swap                                     
/dev/sda4        0365a596-3260-4e6b-be15-4b1e5d2c318c   ext4       Garry Data                    
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        13a53736-8419-43e7-918c-de0c404a148e   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        5a1c51ad-aacc-4fa2-88aa-7284c38f7585   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda2/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set e5a23a3c-cbda-4272-a235-305857ed8e7d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set e5a23a3c-cbda-4272-a235-305857ed8e7d
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set e5a23a3c-cbda-4272-a235-305857ed8e7d
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=e5a23a3c-cbda-4272-a235-305857ed8e7d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set e5a23a3c-cbda-4272-a235-305857ed8e7d
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=e5a23a3c-cbda-4272-a235-305857ed8e7d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set e5a23a3c-cbda-4272-a235-305857ed8e7d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set e5a23a3c-cbda-4272-a235-305857ed8e7d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdc2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 1b5cb5aa6194c90a
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# Commented out by Dropbox
# /dev/sda2       /               ext4    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/sda2 / ext4 errors=remount-ro,user_xattr 0 1

=================== sda2: Location of files loaded by Grub: ===================


    .9GB: boot/grub/core.img
   1.1GB: boot/grub/grub.cfg
   5.2GB: boot/initrd.img-2.6.35-28-generic-pae
   4.3GB: boot/vmlinuz-2.6.35-28-generic-pae
   5.2GB: initrd.img
   4.3GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 13a53736-8419-43e7-918c-de0c404a148e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 13a53736-8419-43e7-918c-de0c404a148e
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 13a53736-8419-43e7-918c-de0c404a148e
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=13a53736-8419-43e7-918c-de0c404a148e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 13a53736-8419-43e7-918c-de0c404a148e
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=13a53736-8419-43e7-918c-de0c404a148e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 13a53736-8419-43e7-918c-de0c404a148e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 13a53736-8419-43e7-918c-de0c404a148e
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=13a53736-8419-43e7-918c-de0c404a148e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5a1c51ad-aacc-4fa2-88aa-7284c38f7585 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 897.7GB: boot/grub/core.img
 764.7GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-28-generic-pae
 897.7GB: boot/vmlinuz-2.6.35-28-generic-pae
    .8GB: initrd.img
 897.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 2e 00 20 08  |.............. .|
00000200

Unknown BootLoader  on sdb2

00000000  13 93 d8 1f 20 c4 57 ef  48 e7 8e 83 dd 60 ec de  |.... .W.H....`..|
00000010  53 0c 9b 24 1a 8e 75 ca  f6 94 b1 c0 b4 c5 f4 c2  |S..$..u.........|
00000020  6a 6c ed 2d 6e 18 a1 9a  1a b7 e9 47 e5 73 a8 7a  |jl.-n......G.s.z|
00000030  47 93 87 04 35 d5 48 48  ed 50 d6 6b 15 ac 47 fe  |G...5.HH.P.k..G.|
00000040  cf a3 a6 e1 8b ac 01 40  ed 74 48 d9 f0 92 ce 94  |.......@.tH.....|
00000050  1d e0 d4 1e 04 fd a2 99  72 5c 71 2c 09 aa 37 31  |........r\q,..71|
00000060  37 db 4b 89 ed 5f 14 f8  e2 cc 20 43 71 cb 67 c0  |7.K.._.... Cq.g.|
00000070  3a 71 2f ca 53 33 9c 27  f9 76 c0 50 16 16 dd 59  |:q/.S3.'.v.P...Y|
00000080  06 ae de bd 88 3b 7b 19  bb d8 55 a6 1b 73 14 66  |.....;{...U..s.f|
00000090  03 95 9f 31 60 17 8a 98  3d 6f 79 d9 8f 4d 80 5e  |...1`...=oy..M.^|
000000a0  c2 70 93 8a 6e 20 55 4a  e2 13 f4 5d 3c bb b3 db  |.p..n UJ...]<...|
000000b0  79 1a e6 01 00 96 61 60  28 18 88 3a 51 78 b4 64  |y.....a`(..:Qx.d|
000000c0  db a2 db ac 19 20 a9 95  e9 85 bf 0d f6 7a f2 9b  |..... .......z..|
000000d0  86 51 0d 09 d6 2d 85 0c  9b 90 06 d2 ae cf 77 83  |.Q...-........w.|
000000e0  b2 db 9f 4c 8f 5b 99 57  d8 7d 65 4c 71 4e 90 2d  |...L.[.W.}eLqN.-|
000000f0  4a 19 c2 bf c8 33 8f af  66 1f 23 e9 14 00 82 d2  |J....3..f.#.....|
00000100  46 13 a1 e5 94 04 a8 0c  02 cb 51 c8 ab 5d 5e 64  |F.........Q..]^d|
00000110  94 66 95 c1 28 4c 74 66  20 8a e5 37 c8 f3 a5 96  |.f..(Ltf ..7....|
00000120  af 59 32 69 4d d0 9d 46  81 34 25 dc 7d 81 8c 43  |.Y2iM..F.4%.}..C|
00000130  8b ab c1 41 56 23 55 0b  47 c8 a2 0d d7 2a ee 28  |...AV#U.G....*.(|
00000140  8c d5 8b 59 4d 98 4c 7e  7c d6 e0 1e a2 05 e2 f3  |...YM.L~|.......|
00000150  bf 45 cc 97 28 2b 16 f9  0c 35 e8 e0 99 e1 23 84  |.E..(+...5....#.|
00000160  b2 4a 35 2a bf bb a1 8f  3d f4 5c ee 0d f8 9e 99  |.J5*....=.\.....|
00000170  c3 49 59 80 68 a1 1f 9e  73 8d c6 c9 76 08 fe 1f  |.IY.h...s...v...|
00000180  34 09 33 52 15 73 5a b3  ce cd 51 4f b7 1e 74 e3  |4.3R.sZ...QO..t.|
00000190  fa f9 13 9c c0 59 28 1f  f8 15 0c e2 91 71 4d 3e  |.....Y(......qM>|
000001a0  14 f6 93 db 07 56 7e b4  5a fd 9a 60 9a 07 25 e9  |.....V~.Z..`..%.|
000001b0  cf 8f f2 1d c4 68 50 7f  88 50 65 6a 64 f2 00 fe  |.....hP..Pejd...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 48 34 03 00 00  |...........H4...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by srs5694 on 2011-04-17
First, ***do not run gptsync!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!***

That program creates a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which is an ugly and dangerous hack that is almost certainly not required or helpful for the situation described here. Running that program will just dig you deeper into trouble.

Some more background: GPT is an alternative to the dated Master Boot Record (MBR) partitioning system. Soon enough we'll all be using GPT, since MBR can't handle drives with more than 2^32 sectors (2 TiB, assuming a 512-byte sector size). See my ["What's a GPT?"](http://www.rodsbooks.com/gdisk/whatsgpt.html) page for details. As it is, you've got one GPT disk and one MBR disk. This is fine, although some versions of GRUB can get confused by this, but IIRC that's been fixed in the version shipped with Ubuntu 10.10.

The "unknown" partition in the screen shot is misidentified as an EFI System Partition, when it should in fact be a BIOS Boot Partition. It probably got changed when you were futzing around with the "boot flag," which libparted-based tools (such as GParted) use to identify EFI System Partitions on GPT disks. I recommend resetting the type to BIOS Boot Partition, which GParted identifies by a "bios_grub" flag (or you can use [GPT fdisk](http://www.rodsbooks.com/gdisk/) and set the type code to EF02).

The drive identifications (/dev/sda vs. /dev/sdb) are different in your fdisk output in post #10 and in your Boot Info Script results in post #23. This suggests that you've got some sort of race condition going on or configuration weirdness that's causing the drives to be identified differently from boot to boot or depending on boot conditions. This is an important clue. Probably what happened was that when you added the new drive, your BIOS saw the system differently, and/or when you installed the new version of Ubuntu, it overwrote the boot loader code in the MBR with code that saw the disks differently. The Boot Info Script also says that GRUB is installed in the MBRs of both disks, but that on the 2 TB (GPT) disk, it's searching in the wrong place for its second-stage code. This could be a consequence of re-installing GRUB after improperly changing the type code of the BIOS Boot Partition. I'd focus on the GRUB aspect of the problem. I can't offer a simple sure-fire way to fix it, but I can suggest several avenues to pursue:


[list]
[*]Fix the BIOS Boot Partition problem and re-install GRUB. This suggestion is *not* optional; in some configurations, having the BIOS Boot Partition specified correctly is very important. The following three suggestions are all optional, though; try them in whatever order you like.
[*]Try swapping the way the drives are attached to  the motherboard (unplug the cables at the motherboard end and reverse which one is attached to which connector).
[*]Try attaching the drives to different motherboard connectors, particularly if your board has more than four. Consult your computer's or motherboard's manual to determine which connectors use which ATA chipsets.
[*]Use the boot order options in the BIOS to change which drive boots first.
[*]Re-install GRUB after making any of the above changes.
[/list]


Unfortunately, my suggestions are a bit hit-or-miss. In principle, you could work it out a bit more systematically by observing the drive identification (/dev/sda vs. /dev/sdb) given to each drive when you boot in various ways and matching that up with the BIOS boot order, to get GRUB on /dev/sda and get the drives mapping consistent. If you've got a race condition, though, the drive identification in Linux simply won't become consistent, so the hit-or-miss approach may be the best way to go.

---

### Post by Glkanter on 2011-04-17
Great stuff! I can't thank you enough.

My system has 5 SATA connections, and I have:[INDENT]1 blu ray DVD
1 250 GB HD
1 2 TB HD
1 1 TB HD
[/INDENT]The connections are numbered and as far as I can tell completely interchangeable.

Separately from the connectors, the BIOS lets me order the hard drives any way I want. Only the first one can be part of the CD/USB/HD boot sequence.

So, is there a particular outcome I'm trying to achieve?

If I understand correctly, I am to:[INDENT]Fix the BIOS Boot Partition on the 2 TB drive using GPARTED
Make it so that the 2 TB boots first - I can be certain of this by making it first in the BIOS as I described above - is that all that is needed?
Re-install GRUB. On both drives? Have you told me how to do that?
[/INDENT]My goal is to make the 1 TB an exact copy of the entire Ubuntu area of the 2 TB, so that if the 2 TB fails, I just make the 1 TB the first HD in sequence, and it boots with no other adjustments.

Once again, thanks to everybody.

---

### Post by oldfred on 2011-04-17
While you can copy your data easily, because one drive is MBR(msdos) and the other gpt your boot configurations will be different. You really cannot easily copy the Ubuntu install as grub settings, fstabs, UUIDs are all different.

I have different installs on each drive. I keep windowsXP on my old drive, and have Ubuntu old install, current install and new(beta) install on my other two drives. That way I can boot something. My configurations are similar but not identical and my data is in a separate /data partition.

It is best to boot by UUID and use UUIDs in fstab. You have in your fstab drive entries, so any swapping of drives will confuse the boot (sda becomes sdb etc). If you use UUIDs you can change drive boot order and have no issues.

# /dev/sda2       /               ext4    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/sda2 / ext4 errors=remount-ro,user_xattr 0 1

Use sda1 or sdb2 or if drives are switched then even that changes. You want to install to the MBR of the same drive as the system is installed to and then test booting by changing boot order in BIOS or with one time boot (f12on mine)  key.
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by Glkanter on 2011-04-17
It seems like I have 3 very qualified people giving me good guidance.

I've been messing with PCs at one level or another since the beginning. Self-taught, so I'm dangerous. But I've never heard of UUIDs or fstab entries before.

So, could someone please describe a little more clearly exactly what steps I am to take, and what the expected outcome is? I'm sure you all can appreciate that spinning wheels, making mistakes, and making things worse due to my inexperience doesn't help any of us.

Thanks, again. This level of interest and expertise was not expected at all, and it is greatly appreciated!

Garry

---

### Post by oldfred on 2011-04-17
If you reinstall grub2's boot loader to the MBR, you may be able to reboot, or as srs5694's suggest swap drives. Your setting of sda in files means the system has to see it as sda on boot. It will work if it is sda, but not  if sdb.  The same for your drive sdb.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

If you can get one or the other to boot it is easier to update, but you can use liveCD to make all edits/repairs.

---

### Post by srs5694 on 2011-04-17
Glkanter,

I'm afraid we don't know what precise steps you should take, although oldfred has provided a procedure for re-installing GRUB. The trouble is that we don't know precisely how your BIOS, GRUB, and Linux are perceiving your drives. It will take experimentation to determine that information. Any one of us could probably figure it out in a few minutes if we had physical access to your computer, but making the determination is not a simple linear procedure; it's a branching decision tree with quite a few possible outcomes.

The /etc/fstab file controls how Linux mounts partitions. You can specify partitions by device node (/dev/sda2, for instance) or by UUID (e5a23a3c-cbda-4272-a235-305857ed8e7d, for instance). A UUID is a 128-bit number that uniquely identifies a filesystem. When your drives' identities are changing (as yours seem to be, as I noted earlier), using UUIDs in /etc/fstab and in the GRUB configuration makes much more sense than using device nodes. Ordinarily, Ubuntu uses UUIDs in /etc/fstab, so if your /etc/fstab file uses device nodes (as it does on /dev/sda2 but not on /dev/sdb1), it means it's not a recent Ubuntu installation or someone or something has changed it.

---

### Post by lmarmisa on 2011-04-17
I have done some tests about GPT and GRUB using a virtual machine and Ubuntu 10.10.

Gparted seems able to work fine with GPT (the image of the initial post of this thread belongs to Gparted running under Clonezilla).

So, I defined a 20 Gbytes hard drive for tests and, using Gparted, I created its partition table selecting the format GPT (image 1).

Then I defined a couple of partitions in that hard drive (image2) .

The command **fdisk -l** was unable to read correctly the info of this hard drive (image 3).

Finally, the command **grub-install** did not run properly on that hard drive with GPT:

```

luis@UB1010ENG:~$ sudo grub-install /dev/sdc
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
luis@UB1010ENG:~$

```So, according to my tests, the only program of Ubuntu that seems adapted to GPT is Gparted.

---

### Post by Glkanter on 2011-04-17
How about if I take this one step at a time? (Like I should have done before I caused all this aggravation.)

In order to minimize the chance for system (and user) confusion, I'd like to do any and all 'work' with just one of the drives in the PC at a time.[INDENT]So, step one would be to: Fix the BIOS Boot Partition problem on the 2 TB drive. Since that drive doesn't boot, I would do the fixing with the Ubuntu Live cd.

[What would indicate that I should go ahead and re-install Grub? Or do I have that out of sequence, already?]

Once that is complete, should I try booting with that drive (the 2 TB) as the only drive in the system? What other info should I gather in order to report it to you guys?
[/INDENT]Thanks,

Garry

---

### Post by Glkanter on 2011-04-17
Please be advised I had not seen Imarmisa's posting before I posted the above suggestion. I do not know what impact it has on my suggested approach.

But I *do* appreciate all the effort you went to in order to do that testing.

Thanks!

---

### Post by K_45 on 2011-04-17
I'd do post No #31, and install Grub. Solve this first. I'd also connect the drive to SATA_0, as a boot drive and set the BIOS to boot that HDD first.

---

### Post by lmarmisa on 2011-04-17
Hi Garry,

you posted an image of Gparted running on Clonezilla. Could you post the same GParted capture of your 2 TB hard drive running on Ubuntu 10.10?.

Use Applications -> Accessories -> Take ScreenShot

Thanks.

---

### Post by Glkanter on 2011-04-17
> **lmarmisa said:**
> Hi Garry,

you posted an image of Gparted running on Clonezilla. Could you post the same GParted capture of your 2 TB hard drive running on Ubuntu 10.10?.

Use Applications -> Accessories -> Take ScreenShot

Thanks.

Here's 2 ScreenShots, 1 for each warning.

---

### Post by lmarmisa on 2011-04-17
> **Glkanter said:**
> Here's 2 ScreenShots, 1 for each warning.

This image is a bit different from the first one. And it seems even worse.

This is a bit confusing. Gparted says that he is unable to read the file system associated to **/dev/sdb4** but this partition seems mounted.

Are you able to see the files stored in that partition?. Is the partition really mounted?.

Do you have important files (documents, music, photos, videos) stored in that partition?.

---

### Post by K_45 on 2011-04-17
What is the output of

```
mount
```

---

### Post by Glkanter on 2011-04-17
> **lmarmisa said:**
> This image is a bit different from the first one. And it seems even worse.

This is a bit confusing. Gparted says that he is unable to read the file system associated to **/dev/sdb4** but this partition seems mounted.

Are you able to see the files stored in that partition?. Is the partition really mounted?.

Do you have important files (documents, music, photos, videos) stored in that partition?.

Yes I can see the files stored in that partition. I can click on documents, and they open, as expected. I believe it is mounted as in 'Places' it has that symbol to the right of the label. When I ckick it, it asks if I want to clean out the trash before unmounting.

Yes, there are legacy documents & files on that drive. I have already copied them onto the 1 TB drive.

You know, my (slightly revised) goals can be re-stated:[INDENT]I want to use the 2 TB as my system and data drive
I want to be able to copy it to the 1 TB, and use the 1 TB as a ready-to-go backup. [This backup would take place maybe once a week]
I want to use my 250GB drive for daily data backup in some way.
I want to use the Linux system as it is already configured from either the 1 TB or the 2TB going forward.
[/INDENT]Thanks,

Garry

---

### Post by Glkanter on 2011-04-17
> **K_45 said:**
> What is the output of

```
mount
```

```

glkanter@Garry-System:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/glkanter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=glkanter)
/dev/sdb2 on /media/e5a23a3c-cbda-4272-a235-305857ed8e7d type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb4 on /media/Garry Data type ext4 (rw,nosuid,nodev,uhelper=udisks)
glkanter@Garry-System:~$ 

```

---

### Post by lmarmisa on 2011-04-17
I have done two more tests:

1) I installed Ubuntu 10.10 on a hard drive with a GPT partition table. The installation and all the updates (including the update of the kernel) were completed successfully.

The system run properly with some exceptions. I was able to check that the commands fdisk and grub-install did not work. I thought that the update of the kernel uses the command grub-install but maybe this is not correct.

Maybe my opinion is not very founded, but I think that GPT is the future, but Ubuntu 10.10 is not completely ready for that new standard.

2) I have created a virtual disk with a size of 2 TB (the disk is virtual because I have no such space available :)). I have checked that MBR can be used in such hard drive. 2 TB is close to the maximun size supported by MBR, but this size is apparently supported by MBR.

```

luis@UB1010ENG:~$ sudo fdisk -l

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e99fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2497    20051968   83  Linux
/dev/sda2            2497        2611      916481    5  Extended
/dev/sda5            2497        2611      916480   82  Linux swap / Solaris

Disk /dev/sdb: 2199.0 GB, 2199022206976 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4a16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      267350  2147481600    7  HPFS/NTFS
luis@UB1010ENG:~$ 


```

---

### Post by K_45 on 2011-04-17
What happens when you

```
cd /media/Garry\ Data
```

---

### Post by oldfred on 2011-04-17
It looks like you have booted sda and have mounted some partitions from sdb. Which drive is sda now?

I have used gpt on my 160GB drive with both 10.04 and 10.10 and installed gpt on my 16GB Flash drive and booted 10.10 and 11.04. The issues were with grub on 10.04 not working with a MBR drive but setting a parameter in the grub file fixed that. If not using windows gpt is considered a better way to configure a hard drive. Arch recommends it for all SSD installs.

Some tools (fdisk for one) are known not to display gpt data correctly but everything works. I will only use gpt for all future drives and do not expect to ever install windows again.

sdb1 is my bios_grub partition:
fred@fred-MavericDT:~$ sudo parted /dev/sdb unit s print
[sudo] password for fred: 
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sdb: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size        File system     Name      Flags
 1      34s        16064s      16031s
 2      16065s     51215219s   51199155s   ext4            MAVERICK
 3      51215220s  57352049s   6136830s    linux-swap(v1)
 4      57352050s  312576704s  255224655s  ext4

fred@fred-MavericDT:~$

---

### Post by lmarmisa on 2011-04-17
I would like to make a proposal and a little comment to your goals.

If you are 100% sure all your legacy documents and files are stored in the 1 TB hard drive, I recommend to change the partition table of the 2 TB hard drive to MBR/DOS (GParted -> Device -> Create Partition Table). You can use Gparted for that purpose. **Warning: all data stored on the 2 TB hard drive will be lost.**

Then you will be free to define new partitions in that 2TB hard drive.

For example you could define:

1) One 50 GB ext4 partition for Ubuntu /.
2) One 1.5X size of your RAM for swap (25 GB for swap is too much!!!!!).
3) One 1 TB ext4 partition for /home.
4) About 1 TB of unallocated space or allocated for other purposes.

The next step would be to install Ubuntu 10.10 on the new partitions selecting the MBR of the 2TB drive for storing the GRUB loader.

[B]I would like to know the opinion about this proposal of other persons that were collaborating in this thread.
[/B] 
Finally, one comment about your goals: Clonezilla will be not able to create a ready-to-go backup on your 1 TB hard drive. The cloning function of Clonezilla has the limitation that the target disk cannot be smaller than the source disk.

---

### Post by oldfred on 2011-04-18
While I like and plan to use gpt, if the OP want to have two identically configured boots, he will probably be better with MBR on both. If never planning windows he could use gpt, but there is no requirement that makes gpt mandatory. When drives get over 2GiB then gpt will be required. Or booting with UEFI then gpt will be required.

I prefer two clean installs, one on each drive with smaller system partitions. If data is stored in other partitions even /home does not have to be huge. I like the idea of not necessarily allocating all of the space now as in the future different needs may arise. 

If using MBR, you do have to make sure the extended is next to or includes all the unallocated or you get trapped if you have the extended partition between primaries.

I believe srs5694's gdisk does conversions.

Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
Remove old parts of gpt
[http://ubuntuforums.org/showpost.php?p=10022223&postcount=34](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by Glkanter on 2011-04-18
You guys are great, I can't thank you all enough.

I have no desire, and do not anticipate a need for Windows.

I *really* want to use the backup strategy I've described previously.

I'm pretty much lost in the discussion by now.

My legacy data is stored on both the 2 TB and the 1 TB drives.

I agree that it's time to bring this to a close.

You guys are very knowledgeable, and I'm sure you'll come up with a simple solution that satisfies my goals.

We can re-format/partition the 2 TB as needed, as my legacy stuff is on the 1 TB. Then we can copy the legacy stuff to the 2 TB, and do whatever needs to be done on the 1 TB, as per my backup strategy.

And if we don't have to lose both Linux systems, even better!

Thank you!

Garry

---

### Post by K_45 on 2011-04-18
First copy everything you want of the 2TB drive onto the 1TB drive. Then connect the 1TB drive to SATA_0 and the 2TB one to SATA_1, and follow lmarmisa's advice. Then we can work on backup strategies. One other thing, what is your motherboard? If you have a UEFI BIOS, I'd use GPT . . .

---

### Post by Glkanter on 2011-04-18
So, How do I make my 2 TB drive a "UUID" drive?[INDENT]At this point, I just want to make it the best, cleanest drive it can be.
I want it broken up into at least 2 logical drives. The logical drive that Linux is installed to should be no bigger than my 1 TB drive, as I still want to use the 1 TB for backup as I've been describing.
[/INDENT]Then, I'll install Ubuntu 10.10 on it, if necessary. (Are there any configuration settings or anything else I can preserve in any way?)

And I'll copy my old legacy stuff from the 1 TB, if necessary.

Then, I'll want to make the 1 TB a UUID drive.

Everybody agree with this plan? Thanks!

Garry

---

### Post by srs5694 on 2011-04-18
> **lmarmisa said:**
> I have done some tests about GPT and GRUB using a virtual machine and Ubuntu 10.10.
...
So, according to my tests, the only program of Ubuntu that seems adapted to GPT is Gparted.

You're very much mistaken; you just weren't doing things correctly:


[list]
[*]Although fdisk doesn't understand GPT, my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program does; I designed it as an fdisk workalike for GPT disks, although MBR/GPT differences mean that it's got some important differences from fdisk.
[*]GRUB 2 definitely supports GPT; however, it works best with GPT if there's a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) on the disk, and sometimes it doesn't even install on a GPT disk without one. That's probably the issue you encountered in your test.
[*]A critical tool you didn't mention is the kernel. The Linux kernel has GPT support. It's an option, but it is enabled by default in Ubuntu (and in most other distributions).
[/list]


For more information on this, see [this article I wrote](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html) on the topic, or my [GPT fdisk documentation.](http://www.rodsbooks.com/gdisk/)

> Maybe my opinion is not very founded, but I think that GPT is the  future, but Ubuntu 10.10 is not completely ready for that new standard.

I disagree with your opinion -- at least partly. GPT *is* the future, since MBR can't handle disks larger than 2^32 sectors (2 TiB, given 512-byte sectors). Ubuntu is perfectly able to handle GPT today. Although there *are* GPT-specific issues, they're mostly problems related to users bringing MBR assumptions into the GPT world and getting hung up on that. (For instance, there's another thread on this forum where a user insists on trying to set the "boot flag" on a GPT partition, which is completely incorrect.) GPT has several advantages over MBR, even on small disks. The most notable of these is the lack of primary/extended/logical distinction, which causes endless grief in the MBR world.

The one area where you might have a point is that, IIRC, the Ubuntu installer doesn't create a BIOS Boot Partition by default. If you know enough to create one yourself, that's not a problem, but you do have to know to create one.

[quote=oldfred]While I like and plan to use gpt, if the OP want to have two identically  configured boots, he will probably be better with MBR on both. If never  planning windows he could use gpt, but there is no requirement that  makes gpt mandatory.[/quote]

Using the same partitioning system for all hard disks on a computer might slightly reduce the potential for confusion, but it's certainly not required, and I don't really see any advantage to it, aside from that issue of confusion. Certainly there's no advantage to a 2-MBR system over a 2-GPT system, at least if you're booting only Linux. OTOH, the advantages of GPT are pretty small.

I see no evidence that Glkanter's problems are related to the mixed MBR-and-GPT nature of the drives. I've encountered similar problems on all-MBR setups, and it's always been a matter of changing drive assignments or improper boot loader configurations.

[quote=oldfred]When drives get over 2GiB then gpt will be  required. Or booting with UEFI then gpt will be required.[/quote]

I think you mean "2TiB", not "2GiB". ;) Also, UEFI supports booting from either MBR or GPT, although Windows requires GPT on UEFI-based systems, so GPT will probably become the standard on such systems when they become common. That's not relevant for the current discussion, though....

Glkanter, at this point, this thread has bogged down in minutiae and hypotheticals. We just don't know enough about precisely what's going on with your system to be able to offer you more real advice, and there's not much you can do to provide us with that information. (The missing information has to do with issues like how the BIOS assigns drive numbers, how Linux is detecting the drives, etc.) My advice is to just start fiddling with it, as I recommended in [post #24.](http://ubuntuforums.org/showpost.php?p=10687721&postcount=24) Swap the cables around, re-install GRUB, etc., until you get it working. If you can get one installation working, chances are you can get them both working by re-running update-grub or by fiddling with the GRUB configuration (although the latter would require you to come back for more advice).

---

### Post by srs5694 on 2011-04-18
> **Glkanter said:**
> So, How do I make my 2 TB drive a "UUID" drive?

There's no such thing. A Universally Unique ID (UUID) is a 128-bit number that's used (among other things) to uniquely identify a filesystem. Most Linux filesystems include UUIDs so that they can be referred to by UUID vs. by device node (/dev/sda2 or whatever). UUIDs are not assigned to whole hard disks (but see below) and there's no such thing as a "UUID drive."

UUIDs are very similar to Globally Unique IDs (GUIDs), which are used extensively in the GUID Partition Table (GPT) partitioning system. Under GPT, each partition has a unique GUID and another GUID that serves to identify its type (data, BIOS Boot Partition, etc.). Each disk also has a GUID. Some people, particularly in the Apple world, refer to "GUID drives" in the way I'd use the term "GPT drive" -- to refer to a disk that's been partitioned with GPT.

Currently, your 2 TB disk is a GPT disk and your 1 TB disk is not (it's an MBR disk). I don't think this is really the root of your problem, though; your boot loader has become confused because of changes in the way drives are being detected or assigned numbers.

> 
[INDENT]At this point, I just want to make it the best, cleanest drive it can be.
I want it broken up into at least 2 logical drives. The logical drive that Linux is installed to should be no bigger than my 1 TB drive, as I still want to use the 1 TB for backup as I've been describing.
[/INDENT] There's really no way to break up your 2 TB disk into two 1 TB disks. You *can* create partitions on the 2 TB disk that are similar (even identical) in size to the partitions on the 1 TB disk, and you can then copy your Linux installation from the 1 TB disk to the 2 TB disk, leaving 1 TB of space on the 2 TB disk free for other uses. As was noted by somebody in an earlier post, though, this will require some fiddling with configuration files. Note that one of the "U"s in "UUID" stands for "unique." If you've got two filesystems with identical UUIDs on one computer, chances are things will start breaking. Thus, your duplicate setup *must* use different UUIDs from the original. Because critical configuration files use UUIDs, those files must therefore be changed. I don't know of any tools that will do this automatically, offhand.

Overall, I'm not sure that having two identical installations is really worthwhile. If you want it for quick recovery in case of a drive failure, a RAID setup might be better suited, since that keeps both copies up to date and obviates the need to mess with UUID changes. If you want it for backup purposes, an external drive holding a more conventional backup is a better option, since an external drive will be less likely to be damaged by something like a power surge (if you keep it disconnected most of the time), which might take out both internal drives.

---

### Post by Glkanter on 2011-04-18
Yes, I quite agree it's time to bring this to a close.

With the following as my goal, can you tell me what straight forward approach I should use?

In essence, I'm willing to start over with each hard drive. Just tell me the 'best' way to go about it. Does using the UUID eliminate a whole lot of potential confusion? If so, let's use it!

> **Glkanter said:**
> You guys are great, I can't thank you all enough.

I have no desire, and do not anticipate a need for Windows.

I *really* want to use the backup strategy I've described previously.

I'm pretty much lost in the discussion by now.

I posted #50 before I saw #49. 

My legacy data is stored on both the 2 TB and the 1 TB drives.

I agree that it's time to bring this to a close.

You guys are very knowledgeable, and I'm sure you'll come up with a simple solution that satisfies my goals.

We can re-format/partition the 2 TB as needed, as my legacy stuff is on the 1 TB. Then we can copy the legacy stuff to the 2 TB, and do whatever needs to be done on the 1 TB, as per my backup strategy.

And if we don't have to lose both Linux systems, even better!

Thank you!

Garry

Thanks for everything!!

I posted #50 before I saw #49.

---

### Post by oldfred on 2011-04-18
The problem with best ways is that my own best way for me has changed every year. What I suggest to a new user is somewhat drifferent than a more advanced user as it requires more configuration which for new users can be too much change at once.

I would do all partitioning in advance. Gparted will work with gpt (you have to select that under device, advanced. But you also should have the latest gdisk and can use that to create your partitions.

Generally I like small system partitions (root) - for Linux I suggest 10-25GB and I use about 7GB in the system partition. Since you have large drives you can go slightly larger but really do not have to. Even for newer users I suggest separate /home do data is not in system partition. But for advanced users (but I do not think srs5694 agrees) I suggest separate /data partitions and keeping /home with only the users settings in /home. Swap should be the size of RAM(+ a little) if you want to hibernate, otherwise 2GB or something is all that is required. Many users with over 4GB of RAM have no swap.

As you can see just from above there can be a lot of choices. Many of use suggest somewhat different "optimal" partitioning schemes and none are really wrong. Do you plan on lots of data - music, movies etc. Or will you what to install other versions of Linux for testing? 

If it was me I would do this with GPT (assuming you have BIOS). If using gpt all partitions will be primary.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:

Create a first bios_grub partition - size may vary depending on what you use to create it:
Make it 128 kiB as recommended in the following link. Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
It only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues

 20-30 GB Mountpoint / primary or logical beginning ext4(or ext3)
 50GB Mountpoint /home logical beginning ext3(or ext4)
 2 GB Mountpoint swap logical
Remaind of drive in several larger partitions for data or unallocated if not sure what you want to do in the future.

One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

If you want MBR you do not need bios_boot, should make only one or two primary partitions and make the rest of the drive part of the extended partition. You do not have to create logicals in all of the extended but that lets you use all of it without running into the 4 partition limit.

---

### Post by Glkanter on 2011-04-18
I'm not trying to do anything 'unnatural' with the PC, Ubuntu, or the 2 drives.

But I *do* want to make a backup drive that can be swapped into action if the 2 TB drive fails.

Do any changes get made to the PC's BIOS other than when I go in and make changes? Do settings change because of the Ubuntu installation? Do any of the PC's BIOS settings change when I make a different drive the boot drive?

Would the process be less potentially confusing if the 1 TB drive had a case around it, and it became an external USB drive?

Thanks.

---

### Post by oldfred on 2011-04-18
The only BIOS setting change is which drive is the boot drive. 

My working 10.10 install is in sdb, so I currently boot sdb, but was booting sdc for the last couple years which has my previous 10.04 & 9.10 installs. And my test install of Natty in sdc has its boot loader in sda (since that is what installs like to default to) and sda is XP which I do not directly boot and rarely boot at all, now.

My sdb is now gpt, but I have not converted my other drives as of yet from MBR.

If you have UEFI BIOS on a new machine that is a bit more cutting edge and we just recently had a couple of posters with issues.

---


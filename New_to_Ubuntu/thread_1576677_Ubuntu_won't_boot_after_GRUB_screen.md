---
title: "Ubuntu won't boot after GRUB screen"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by DSimm626 on 2010-09-17
Hi.  My first post and my first Linux mistake made-)


I have a HP laptop partitioned with WIN Vista and Ubuntu 9.01 on it.

When I start the pc, GRUB (ver 1.97~beta4) comes up. It use to have a 8 second delay before booting the latest Ubuntu kernel(?) automatically. This is now gone.

After I hit enter on the Ubuntu, linux 2.6.31-22-generic line, the Ubuntu logo screen comes up and then goes to a blank screen with a line curser. After about 3-4 minutes the pc does a FileSystem checks, which seems like 3 or 4 times the goes to a root@my pc name:~# prompt.

How do I get my Ubuntu to work again?

Also, my WinVista will boot but runs very, very slow. I was watching a DVD last night and the DVD drive locked up and froze my pc. It wouldn't do anything so I unplugged and pulled the battery. My fatal mistake-((

Thank you for reading and helping this newbie out.
David

---

### Post by wilee-nilee on 2010-09-17
If you can post the bootscript in my signature, in code tags as described. Code tags are also made by clicking on the # in the reply then put the text in between the two code notations.

---

### Post by chaanakya_chiraag on 2010-09-17
Are there any messages before the prompt?

---

### Post by davidmohammed on 2010-09-17
suggest force a filesystem check and automatic fix when it gets to the # prompt.

I think from memory you have to type

fsck -y

or possibly

sudo fsck -y

---

### Post by DSimm626 on 2010-09-17
@wilie-nilie. Good instructions in your link too. Thanks


#    Boot Info Script 0.55    dated February 15th, 2010                    

============================= ```
Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x89858762

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    61,442,047    61,440,000   7 HPFS/NTFS
/dev/sda2          61,442,048   102,402,047    40,960,000   7 HPFS/NTFS
/dev/sda3         102,414,375   488,392,064   385,977,690   5 Extended
/dev/sda5         102,414,438   219,592,484   117,178,047  83 Linux
/dev/sda6         219,592,548   243,031,319    23,438,772  82 Linux swap / Solaris
/dev/sda7         243,031,383   488,392,064   245,360,682  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DCEA7240EA7216CC                       ntfs                                     
/dev/sda2        D2E25F56E25F3E43                       ntfs       Storage                       
/dev/sda5        cae09705-a3a4-4eac-8e30-39603d0814ab   ext4                                     
/dev/sda6        97afa71f-0ef9-4c06-a2eb-af01e16f1781   swap                                     
/dev/sda7        446fe54c-dc29-4bde-a4cf-811e35a8b5c5   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set cae09705-a3a4-4eac-8e30-39603d0814ab
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cae09705-a3a4-4eac-8e30-39603d0814ab
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=cae09705-a3a4-4eac-8e30-39603d0814ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cae09705-a3a4-4eac-8e30-39603d0814ab
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=cae09705-a3a4-4eac-8e30-39603d0814ab ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cae09705-a3a4-4eac-8e30-39603d0814ab
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=cae09705-a3a4-4eac-8e30-39603d0814ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cae09705-a3a4-4eac-8e30-39603d0814ab
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=cae09705-a3a4-4eac-8e30-39603d0814ab ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cae09705-a3a4-4eac-8e30-39603d0814ab
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=cae09705-a3a4-4eac-8e30-39603d0814ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cae09705-a3a4-4eac-8e30-39603d0814ab
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=cae09705-a3a4-4eac-8e30-39603d0814ab ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set dcea7240ea7216cc
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=cae09705-a3a4-4eac-8e30-39603d0814ab /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=446fe54c-dc29-4bde-a4cf-811e35a8b5c5 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=97afa71f-0ef9-4c06-a2eb-af01e16f1781 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  56.3GB: boot/grub/core.img
  56.6GB: boot/grub/grub.cfg
  57.9GB: boot/initrd.img-2.6.31-20-generic
  57.8GB: boot/initrd.img-2.6.31-21-generic
  58.0GB: boot/initrd.img-2.6.31-22-generic
  56.8GB: boot/vmlinuz-2.6.31-20-generic
  57.5GB: boot/vmlinuz-2.6.31-21-generic
  57.9GB: boot/vmlinuz-2.6.31-22-generic
  58.0GB: initrd.img
  57.8GB: initrd.img.old
  57.9GB: vmlinuz
  57.5GB: vmlinuz.old#
```

---

### Post by DSimm626 on 2010-09-17
> **chaanakya_chiraag said:**
> Are there any messages before the prompt?

100's of lines of text, numbers and symbols. It scrolls by real fast.

---

### Post by wilee-nilee on 2010-09-17
So the script looks like everything is in place, but I will look a little closer, there are others some on-line now some off that are very good at this and the script helps a great deal.

It would be helpful though if you could put the text in code tags, once you know how you will use them regularly.

The easiest way to edit the text is hit the edit button in the script post then advanced highlight the script and click on the # in the panel. This just makes it much easier to read. 

Lets wait for the experts to chime in I say.;)

---

### Post by DSimm626 on 2010-09-17
> **wilee-nilee said:**
> 
It would be helpful though if you could put the text in code tags, once you know how you will use them regularly.

The easiest way to edit the text is hit the edit button in the script post then advanced highlight the script and click on the # in the panel. This just makes it much easier to read. 


Is the text better now? Hopefully that is what you meant. I'm trying to learn:)

---

### Post by wilee-nilee on 2010-09-17
> **DSimm626 said:**
> Is the text better now? Hopefully that is what you meant. I'm trying to learn:)

Excellent, in my Mr Burn's voice.;)

---

### Post by DSimm626 on 2010-09-17
> **davidmohammed said:**
> suggest force a filesystem check and automatic fix when it gets to the # prompt.

I think from memory you have to type

fsck -y

or possibly

sudo fsck -y


This worked!! BUT the pc is running very, very slowly in both OS's now. It takes Ubuntu 4 or so minutes to load when it usually takes less than 1.

I might have a hardware issue now?

EDIT to add, Ubuntu runs fast with the Live cd

---

### Post by DSimm626 on 2010-09-18
> **DSimm626 said:**
> This worked!! BUT the pc is running very, very slowly in both OS's now. It takes Ubuntu 4 or so minutes to load when it usually takes less than 1.

I might have a hardware issue now?

EDIT to add, Ubuntu runs fast with the Live cd


Well that was a one time thing-(. Back to my original problem in my OP.

Windows is running much better this morning so I'm using it for now backing up data because I can still access all my partitions. Linux will run from the Live CD still.

---

### Post by chaanakya_chiraag on 2010-09-18
You have to make the change in /etc/default/grub I believe and run ```
sudo update-grub2
``` afterwards to make it permanent.  Although, I'm surprised it's slower...at least it's actually loading though...

---


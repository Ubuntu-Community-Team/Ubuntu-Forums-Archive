---
title: "Grub bootloader won't appear on boot"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by Vikeyev on 2010-11-02
Hello guys, Ubuntu noob here.

I have just recently (only about 1 hour ago) installed Ubuntu Maverick Meerkat on my windows system. I used the alternate cd (I was getting an errno 5 error with the live cd) and chose to resize my existing partition and install Ubuntu on the freed space. When I boot up my computer the grub boot loader doesn't appear, it just boots straight into Ubuntu and when I check the computer directory their is only one file system in there and that is my Ubuntu system. I wanted to set my boot loader to give me the options of booting into this partition and the windows partition, but I'm not even sure if the windows partition is still on there, which is very worrying to me because I had about 150Gb worth of steam games on that partition (which I can not afford to download again due to my download limit).


I was wondering if anybody could tell me if my windows partition is still installed and if it is how do I get my boot loader to show up at boot time and how can I add my windows 7 partition to it.

Here is the output of the fdisk -l command ```
vikeyev@Vikeyev:~$ sudo fdisk -l
[sudo] password for vikeyev: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b3778

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60254   483984375   83  Linux
/dev/sda2           60254      121602   492776449    5  Extended
/dev/sda5          120837      121602     6142976   82  Linux swap / Solaris
/dev/sda6           60254      120072   480489472   83  Linux
/dev/sda7          120072      120836     6138880   82  Linux swap / Solaris

Partition table entries are not in disk order
```I searched on google and this forum but I couldn't find anything with my exact problem, I did find some things that were similar but not the same. If you need any more information just ask me ; )

Any help you could offer would be greatly appreciated, thank you for your time.
[B]
MOBO[/B]: Asus M4A87TD/USB3
**CPU**: AMD Athlon II x2 245
**GPU**: Radeon HD5770
**RAM**: Corsair VS2GB1333D3 2GB (1333MHz) DDR3 RAM, Non ECC Unbuffered, 9-9-9-24, 1.5V
**PSU**: 600 watt shark
**HDD**: West Gate 1TB 7200RPM SATA2

---

### Post by cinohpa on 2010-11-02
One thing that is puzzling is that there is no info about /dev/sda3 or /dev/sda4.

Can you show us the output of this: 
> 
ls /dev/sd*


Or for more information:

> 
sudo parted /dev/sda
print
quit


The second code block will load your disk into parted and give us all the information we can see about it from the partition table.

From the info from fdisk, your partition table does look a little screwed up but it looks like there is a bunch of space left on the disk. There might be a problem with the number of partitions you can have on a disk. 

For dealing with grub not coming up can you post the content of /boot/grub/menu.lst? Have you seen any errors having to do with grub?

This thread might be helpful if you need to fix your grub configuration:
[http://ubuntuforums.org/showthread.php?t=1611926](http://ubuntuforums.org/showthread.php?t=1611926)

---

### Post by Vikeyev on 2010-11-02
> **cinohpa said:**
> One thing that is puzzling is that there is no info about /dev/sda3 or /dev/sda4.

Can you show us the output of this: 


Or for more information:



The second code block will load your disk into parted and give us all the information we can see about it from the partition table.

From the info from fdisk, your partition table does look a little screwed up but it looks like there is a bunch of space left on the disk. There might be a problem with the number of partitions you can have on a disk. 

For dealing with grub not coming up can you post the content of /boot/grub/menu.lst? Have you seen any errors having to do with grub?

This thread might be helpful if you need to fix your grub configuration:
[http://ubuntuforums.org/showthread.php?t=1611926](http://ubuntuforums.org/showthread.php?t=1611926)

Sorry for taking so long to reply, my ISP is pathetic and I was incapable of getting online.

```
vikeyev@Vikeyev:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sda6  /dev/sda7
vikeyev@Vikeyev:~$ sudo parted /dev/sda
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA WDC WD10EACS-00D (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  496GB   496GB   primary                   boot
 2      496GB   1000GB  505GB   extended
 6      496GB   988GB   492GB   logical   ext4
 7      988GB   994GB   6286MB  logical   linux-swap(v1)
 5      994GB   1000GB  6290MB  logical   linux-swap(v1)

(parted) quit                                                             
vikeyev@Vikeyev:~$ 


```The menu.1st file is completely empty, it has nothing in it.

---

### Post by wilee-nilee on 2010-11-02
It is grub2 there is no menu.list. Post the bootscript in my signature in code tags.

---

### Post by silbak04 on 2010-11-02
according to your output, it doesn't look like your file system for your primary type even shows up as "ntfs" or anything, but says you have 496GB on a files system which seems to not even be there anymore and 492GB on ext4 (Ubuntu)...i'm not a hundred percent sure on this...but i still feel like your windows partition is there, it's just grub i think...maybe this could help:

[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)
[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)

---

### Post by Vikeyev on 2010-11-02
> **wilee-nilee said:**
> It is grub2 there is no menu.list. Post the bootscript in my signature in code tags.

```

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
UUID=479797d8-da94-4451-a2ac-5ff0da540783 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=0fe01545-d786-4844-a2f5-a500e4232ad3 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 542.9GB: boot/grub/core.img
 787.8GB: boot/grub/grub.cfg
 496.4GB: boot/initrd.img-2.6.35-22-generic
 542.9GB: boot/vmlinuz-2.6.35-22-generic
 496.4GB: initrd.img
 542.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  6f 63 6b 20 45 72 72 6f  72 20 31 30 30 35 34 20  |ock Error 10054 |
00000010  22 43 6f 6e 6e 65 63 74  69 6f 6e 20 72 65 73 65  |"Connection rese|
00000020  74 20 62 79 20 70 65 65  72 22 0d 0a 43 73 43 6f  |t by peer"..CsCo|
00000030  6d 6d 20 20 20 20 20 20  20 20 43 6f 6e 6e 65 63  |mm        Connec|
00000040  74 69 6f 6e 20 20 20 20  20 20 20 20 20 20 20 20  |tion            |
00000050  4f 63 74 2d 33 31 2d 32  30 31 30 20 20 32 31 3a  |Oct-31-2010  21:|
00000060  33 32 3a 34 33 2e 30 35  32 20 20 5b 37 37 36 5d  |32:43.052  [776]|
00000070  20 20 7b 43 6e 78 3d 33  2c 34 2c 31 35 30 2e 31  |  {Cnx=3,4,150.1|
00000080  30 31 2e 31 33 35 2e 31  3a 32 37 30 33 30 7d 20  |01.135.1:27030} |
00000090  3a 20 53 65 73 73 69 6f  6e 20 6e 6f 74 20 66 6f  |: Session not fo|
000000a0  75 6e 64 3a 20 35 0d 0a  43 73 43 6f 6d 6d 20 20  |und: 5..CsComm  |
000000b0  20 20 20 20 20 20 43 6f  6e 6e 65 63 74 69 6f 6e  |      Connection|
000000c0  50 6f 6f 6c 20 20 20 20  20 20 20 20 4f 63 74 2d  |Pool        Oct-|
000000d0  33 31 2d 32 30 31 30 20  20 32 31 3a 33 32 3a 34  |31-2010  21:32:4|
000000e0  33 2e 30 35 32 20 20 5b  37 37 36 5d 20 20 44 69  |3.052  [776]  Di|
000000f0  73 63 6f 6e 6e 65 63 74  28 33 29 0d 0a 43 73 43  |sconnect(3)..CsC|
00000100  6f 6d 6d 20 20 20 20 20  20 20 20 43 6f 6e 6e 65  |omm        Conne|
00000110  63 74 69 6f 6e 20 20 20  20 20 20 20 20 20 20 20  |ction           |
00000120  20 4f 63 74 2d 33 31 2d  32 30 31 30 20 20 32 31  | Oct-31-2010  21|
00000130  3a 33 32 3a 34 33 2e 30  35 33 20 20 5b 33 30 39  |:32:43.053  [309|
00000140  36 5d 20 20 7b 43 6e 78  3d 33 2c 34 2c 31 35 30  |6]  {Cnx=3,4,150|
00000150  2e 31 30 31 2e 31 33 35  2e 31 3a 32 37 30 33 30  |.101.135.1:27030|
00000160  7d 20 3a 20 53 65 73 73  69 6f 6e 20 6e 6f 74 20  |} : Session not |
00000170  66 6f 75 6e 64 3a 20 36  0d 0a 43 73 43 6f 6d 6d  |found: 6..CsComm|
00000180  20 20 20 20 20 20 20 20  43 6f 6e 6e 65 63 74 69  |        Connecti|
00000190  6f 6e 50 6f 6f 6c 20 20  20 20 20 20 20 20 4f 63  |onPool        Oc|
000001a0  74 2d 33 31 2d 32 30 31  30 20 20 32 31 3a 33 32  |t-31-2010  21:32|
000001b0  3a 34 33 2e 30 35 33 20  20 5b 33 30 39 36 5d 20  |:43.053  [3096] |
000001c0  20 44 69 73 63 6f 6e 6e  65 63 74 28 33 29 0d 0a  | Disconnect(3)..|
000001d0  43 73 43 6f 6d 6d 20 20  20 20 20 20 20 20 43 6f  |CsComm        Co|
000001e0  6e 6e 65 63 74 69 6f 6e  20 20 20 20 20 20 20 20  |nnection        |
000001f0  20 20 20 20 4f 63 74 2d  33 31 2d 32 30 31 30 20  |    Oct-31-2010 |
00000200


```

---

### Post by wilee-nilee on 2010-11-02
What you have posted is missing many things, did you post the whole file generated by the script.

Whether or not you will be able to recover anything is hard to say that is not my area of knowledge. But generally it is advised to not run the HD anymore until you try a recovery, use a live cd

---

### Post by Vikeyev on 2010-11-02
> **wilee-nilee said:**
> What you have posted is missing many things, did you post the whole file generated by the script.

Whether or not you will be able to recover anything is hard to say that is not my area of knowledge. But generally it is advised to not run the HD anymore until you try a recovery, use a live cd.

Here is a boot script from my setup you will see the difference, I have W7, Lucid and Maverick on one HD.




```
                    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

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

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   967,970,797   967,968,750  83 Linux
/dev/sda2         967,970,814 1,953,523,711   985,552,898   5 Extended
/dev/sda5       1,941,237,760 1,953,523,711    12,285,952  82 Linux swap / Solaris
/dev/sda6         967,970,816 1,928,949,759   960,978,944  83 Linux
/dev/sda7       1,928,951,808 1,941,229,567    12,277,760  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2: PTTYPE="dos" 
/dev/sda5        bb03c006-048d-4468-94fb-207999bd3e49   swap                                     
/dev/sda6        479797d8-da94-4451-a2ac-5ff0da540783   ext4                                     
/dev/sda7        0fe01545-d786-4844-a2f5-a500e4232ad3   swap                                     
/dev/sda: PTTYPE="dos" 

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
search --no-floppy --fs-uuid --set 479797d8-da94-4451-a2ac-5ff0da540783
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 479797d8-da94-4451-a2ac-5ff0da540783
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
    search --no-floppy --fs-uuid --set 479797d8-da94-4451-a2ac-5ff0da540783
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=479797d8-da94-4451-a2ac-5ff0da540783 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 479797d8-da94-4451-a2ac-5ff0da540783
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=479797d8-da94-4451-a2ac-5ff0da540783 ro single 
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
    search --no-floppy --fs-uuid --set 479797d8-da94-4451-a2ac-5ff0da540783
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 479797d8-da94-4451-a2ac-5ff0da540783
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

title    Windows 7
root     (hd0,2)
makeactive
chainloader +1

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
UUID=479797d8-da94-4451-a2ac-5ff0da540783 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=0fe01545-d786-4844-a2f5-a500e4232ad3 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 542.9GB: boot/grub/core.img
 787.8GB: boot/grub/grub.cfg
 496.4GB: boot/initrd.img-2.6.35-22-generic
 542.9GB: boot/vmlinuz-2.6.35-22-generic
 496.4GB: initrd.img
 542.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  6f 63 6b 20 45 72 72 6f  72 20 31 30 30 35 34 20  |ock Error 10054 |
00000010  22 43 6f 6e 6e 65 63 74  69 6f 6e 20 72 65 73 65  |"Connection rese|
00000020  74 20 62 79 20 70 65 65  72 22 0d 0a 43 73 43 6f  |t by peer"..CsCo|
00000030  6d 6d 20 20 20 20 20 20  20 20 43 6f 6e 6e 65 63  |mm        Connec|
00000040  74 69 6f 6e 20 20 20 20  20 20 20 20 20 20 20 20  |tion            |
00000050  4f 63 74 2d 33 31 2d 32  30 31 30 20 20 32 31 3a  |Oct-31-2010  21:|
00000060  33 32 3a 34 33 2e 30 35  32 20 20 5b 37 37 36 5d  |32:43.052  [776]|
00000070  20 20 7b 43 6e 78 3d 33  2c 34 2c 31 35 30 2e 31  |  {Cnx=3,4,150.1|
00000080  30 31 2e 31 33 35 2e 31  3a 32 37 30 33 30 7d 20  |01.135.1:27030} |
00000090  3a 20 53 65 73 73 69 6f  6e 20 6e 6f 74 20 66 6f  |: Session not fo|
000000a0  75 6e 64 3a 20 35 0d 0a  43 73 43 6f 6d 6d 20 20  |und: 5..CsComm  |
000000b0  20 20 20 20 20 20 43 6f  6e 6e 65 63 74 69 6f 6e  |      Connection|
000000c0  50 6f 6f 6c 20 20 20 20  20 20 20 20 4f 63 74 2d  |Pool        Oct-|
000000d0  33 31 2d 32 30 31 30 20  20 32 31 3a 33 32 3a 34  |31-2010  21:32:4|
000000e0  33 2e 30 35 32 20 20 5b  37 37 36 5d 20 20 44 69  |3.052  [776]  Di|
000000f0  73 63 6f 6e 6e 65 63 74  28 33 29 0d 0a 43 73 43  |sconnect(3)..CsC|
00000100  6f 6d 6d 20 20 20 20 20  20 20 20 43 6f 6e 6e 65  |omm        Conne|
00000110  63 74 69 6f 6e 20 20 20  20 20 20 20 20 20 20 20  |ction           |
00000120  20 4f 63 74 2d 33 31 2d  32 30 31 30 20 20 32 31  | Oct-31-2010  21|
00000130  3a 33 32 3a 34 33 2e 30  35 33 20 20 5b 33 30 39  |:32:43.053  [309|
00000140  36 5d 20 20 7b 43 6e 78  3d 33 2c 34 2c 31 35 30  |6]  {Cnx=3,4,150|
00000150  2e 31 30 31 2e 31 33 35  2e 31 3a 32 37 30 33 30  |.101.135.1:27030|
00000160  7d 20 3a 20 53 65 73 73  69 6f 6e 20 6e 6f 74 20  |} : Session not |
00000170  66 6f 75 6e 64 3a 20 36  0d 0a 43 73 43 6f 6d 6d  |found: 6..CsComm|
00000180  20 20 20 20 20 20 20 20  43 6f 6e 6e 65 63 74 69  |        Connecti|
00000190  6f 6e 50 6f 6f 6c 20 20  20 20 20 20 20 20 4f 63  |onPool        Oc|
000001a0  74 2d 33 31 2d 32 30 31  30 20 20 32 31 3a 33 32  |t-31-2010  21:32|
000001b0  3a 34 33 2e 30 35 33 20  20 5b 33 30 39 36 5d 20  |:43.053  [3096] |
000001c0  20 44 69 73 63 6f 6e 6e  65 63 74 28 33 29 0d 0a  | Disconnect(3)..|
000001d0  43 73 43 6f 6d 6d 20 20  20 20 20 20 20 20 43 6f  |CsComm        Co|
000001e0  6e 6e 65 63 74 69 6f 6e  20 20 20 20 20 20 20 20  |nnection        |
000001f0  20 20 20 20 4f 63 74 2d  33 31 2d 32 30 31 30 20  |    Oct-31-2010 |
00000200

       
```For some reason not all of it copied over last time.

---

### Post by oldfred on 2010-11-03
It looks like you tried to paste in a grub legacy style boot stanza. If it is there grub's osprober will find it.

I would try looking at your old partitions and/or repair sda1 with testdisk. It can often find lost or damaged partitions.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by Vikeyev on 2010-11-03
> **oldfred said:**
> It looks like you tried to paste in a grub legacy style boot stanza. If it is there grub's osprober will find it.

I would try looking at your old partitions and/or repair sda1 with testdisk. It can often find lost or damaged partitions.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

I'm running Maverick Meerkat, there is no software sources option in administration. I already have the universe repo activated, I always do.

---

### Post by oldfred on 2010-11-03
You need to run test disk from a liveCD not your install as that may make things worse.

They moved software sources. Or you can get to it from System, Administration, Update Manager and click on the setting button in the lower left.

If universe is enabled you should just be able to download it from synaptic. testdisk is also installed on most linux based repair/recovery CDs.

---

### Post by Vikeyev on 2010-11-03
> **Vikeyev said:**
> I'm running Maverick Meerkat, there is no software sources option in administration. I already have the universe repo activated, I always do.
I can't use the live cd to install from I said that in my first post, I keep getting errno 5 errors, even on mint and kubuntu, I get a similar error on fedora, debian and arch. The only live cd's that have EVER worked for me are OpenSuSE and Mandriva live cd's. I installed from the alernate cd.

---

### Post by Vikeyev on 2010-11-03
**WTF **DID UBUNTU DO TO MY WINDOWS PARTITION????????????????

I installed GParted and had a look in that and I also chucked in my windows 7 installer disk.

**NONE **of my partitions are the ntfs file system, I have 2 large partitions a swap partition and I can't remember what the other one is. The 2 large ones are between 450-500GB each (can't remember exactly) One contains Ubuntu (what I'm typing this from now) the other is......**EMPTY**. 

Why in hell is it empty, I had 150GB worth of friggin steam games, I told the installer to resize the partition and put Ubuntu on the empty space NOT REFORMAT THE BLOODY THING THEN RESIZE IT.

How the hell could this have happened, what a crock!!!!!!

Anyone got any clues as to why this has happened, during the installation process I chose the option to resize existing partitions and install Ubuntu on the empty space, why did it reformat it?

Lastly why do people keep saying you can't alter the grub.cfg file, the ONLY way I have been able to get my grub menu to appear on boot is to alter that file.

---


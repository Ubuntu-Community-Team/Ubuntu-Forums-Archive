---
title: "fstab"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by BobJam on 2011-05-03
I'm getting a message at bootup:  "One or more of the mounts in /etc/fstab cannot yet be mounted: /home . . ." and then it says it's "waiting" for my home UUID and then "Press ESC to enter a recovery shell"

I've googled around for this issue and the consensus seemed to be to replace the UUID with my dev label for home, which is /dev/sda6.  But that didn't work.

The bootup screen GOES NO FURTHER and I'm not real proficient with a CLI, so I used a LiveCD for the editing in a GUI and to access my / and /home directories (and am using it as we speak to post in this forum).

I messed around some more with my etc/fstab file, and I think I may have screwed it up even more.  Here is the current iteration:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1
UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda6
UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d /home           ext3    relatime        0       2
/dev/sda5
UUID=f07345d7-f056-47e4-8bdc-6adce994574f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```Interestingly. the UUID for my /home directory is the same as it always has been, hasn't changed, and is the EXACT one shown by that message.

I tried the mount command in the recovery shell, but that didn't work either.

And here's my partitions:

[IMG]http://i55.tinypic.com/2dv8or4.jpg[/IMG]

I'm not real checked out on running commands from the LiveCD terminal that will act on my local machine, so if anyone has any commands to suggest, could you please give them with that in mind? Or could I just run the command from the recovery shell?

Clearly I'm lost and I guess I could always do a LiveCD reinstall, but I'd rather recover my bootup into the existing GUI.

I hate to end this like so many of the pleas here . . . but . . . HELP!!!!!!  How do I get my boot up back?

---

### Post by Hedgehog1 on 2011-05-03
We need to get a look at the current state of your system so we can help you fix your fstab file..

From the LiveCD/LiveUSB:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by andrewthomas on 2011-05-03
> **BobJam said:**
>   Here is the current iteration:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1
UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda6
UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d /home           ext3    relatime        0       2
/dev/sda5
UUID=f07345d7-f056-47e4-8bdc-6adce994574f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
You just need to comment out the UUID lines, but copy the rest of the information on the lines.  Such as,
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1  /   ext3    relatime,errors=remount-ro 0       1
#UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 /  ext3 relatime,errors=remount-ro 0       1
/dev/sda6  /home           ext3    relatime        0       2
#UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d /home ext3 relatime        0       2
/dev/sda5  none            swap    sw              0       0
#UUID=f07345d7-f056-47e4-8bdc-6adce994574f none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```You probably don't need to have your cdrom drive in fstab.

---

### Post by Hedgehog1 on 2011-05-03
**andrewthomas** - you are giving very poor advice.

If you replace the UUIDs with /dev/sdxy typ references, any time you change disks or partitions Ubuntu will crash.

Correcting the UUIDs in the fstab will create a safer fstab file.

**BobJam** - I would encourage you to post the script output, please.  The idea is to put the correct UUIDs in the fstab file,


The Hedge

:KS

---

### Post by andrewthomas on 2011-05-03
> **Hedgehog1 said:**
> **andrewthomas** - you are giving very poor advice.
 
If you replace the UUIDs with /dev/sdxy typ references, any time you change disks or partitions Ubuntu will crash.
 
 
The Hedge
 
:KSHe just wants to get it to boot.  
I am not suggesting this as a long-term solution. 
I am just stating what he did wrong when editing his fstab file.

---

### Post by oldfred on 2011-05-03
I think andrewthomas is close. It looks like the OP uncommented the lines that normally says this with a # making it a comment

# Entry for /dev/sdc6 :

When it only says this, it is trying to mount it and it is not a valid line

[COLOR=Red]/dev/sda1[/COLOR]
UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 /               ext3    relatime,errors=remount-ro 0       1

On every line add the # for comment back in. Only the line with UUID is the valid entry.
[COLOR=Red]#[/COLOR]/dev/sda1
UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 /               ext3    relatime,errors=remount-ro 0       1

---

### Post by BobJam on 2011-05-04
Hang on everybody.

This business with the LiveCD and redoing the boot order each time I want to see if a mod works is tedious and time consuming . . . plus this darn forum logs me out if I take too long.

So far, though, no joy . . . will report results in detail soon.

For now, Hedgehog 1, here is that script output you asked for:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Acer 3 is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06cd1510

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    48,162,869    48,162,807  83 Linux
/dev/sda2          48,162,870   488,392,064   440,229,195   5 Extended
/dev/sda5         468,519,723   488,392,064    19,872,342  82 Linux swap / Solaris
/dev/sda6          48,162,996   323,083,214   274,920,219  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4051 MB, 4051697152 bytes
255 heads, 63 sectors/track, 492 cylinders, total 7913471 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  38     7,839,719     7,839,682   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4110 MB, 4110227968 bytes
181 heads, 14 sectors/track, 3168 cylinders, total 8027789 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1dad1dad

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63     8,027,788     8,027,726   6 FAT16


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 4085 MB, 4085062144 bytes
255 heads, 63 sectors/track, 496 cylinders, total 7978637 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        41116a1e-1ea3-4ca3-bd34-ff5014d079b0   ext3                                     
/dev/sda5        f07345d7-f056-47e4-8bdc-6adce994574f   swap                                     
/dev/sda6        0cf7ace8-d9ae-43f6-a410-6ebafb3a072d   ext3                                     
/dev/sdb1        B804-AE1B                              vfat       Cruzer                        
/dev/sdd1        49F0-4ABE                              vfat                                     
/dev/sde1        4095-368A                              vfat       7805-OEA8                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /media/7805-OEA8         vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdd1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdb1        /media/Cruzer            vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda6        /media/disk-1            ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sda1        /media/disk-2            ext3       (rw,nosuid,nodev,uhelper=hal)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
# timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=41116a1e-1ea3-4ca3-bd34-ff5014d079b0

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-23-generic
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.31-23-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-23-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-23-generic (recovery mode)
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.31-23-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro  single
initrd        /boot/initrd.img-2.6.31-23-generic

title        Ubuntu 9.10, kernel 2.6.31-22-generic
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, kernel 2.6.28-19-generic
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-19-generic (recovery mode)
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 9.10, kernel 2.6.27-17-generic
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-17-generic (recovery mode)
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro  single
initrd        /boot/initrd.img-2.6.27-17-generic

title        Ubuntu 9.10, memtest86+
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1
#UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda6
#UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d /home           ext3    relatime        0       2
/dev/sda5
UUID=f07345d7-f056-47e4-8bdc-6adce994574f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   3.3GB: boot/grub/menu.lst
   4.8GB: boot/grub/stage2
  16.9GB: boot/initrd.img-2.6.27-17-generic
  16.9GB: boot/initrd.img-2.6.28-19-generic
   3.1GB: boot/initrd.img-2.6.31-22-generic
   3.4GB: boot/initrd.img-2.6.31-23-generic
   4.8GB: boot/vmlinuz-2.6.27-17-generic
   4.8GB: boot/vmlinuz-2.6.28-19-generic
   3.5GB: boot/vmlinuz-2.6.31-22-generic
  16.9GB: boot/vmlinuz-2.6.31-23-generic
   3.4GB: initrd.img
   3.1GB: initrd.img.old
  16.9GB: vmlinuz
   3.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  5f 62 69 74 5f 61 72 72  61 79 5f 69 6e 76 65 72  |_bit_array_inver|
00000010  74 5f 73 65 6c 65 63 74  69 6f 6e 00 65 5f 62 69  |t_selection.e_bi|
00000020  74 5f 61 72 72 61 79 5f  73 65 6c 65 63 74 5f 61  |t_array_select_a|
00000030  6c 6c 00 65 5f 62 69 74  5f 61 72 72 61 79 5f 73  |ll.e_bit_array_s|
00000040  65 6c 65 63 74 5f 73 69  6e 67 6c 65 5f 72 6f 77  |elect_single_row|
00000050  00 65 5f 62 69 74 5f 61  72 72 61 79 5f 63 6c 65  |.e_bit_array_cle|
00000060  61 72 00 65 5f 62 69 74  5f 61 72 72 61 79 5f 64  |ar.e_bit_array_d|
00000070  65 6c 65 74 65 5f 73 69  6e 67 6c 65 5f 6d 6f 64  |elete_single_mod|
00000080  65 00 65 5f 62 69 74 5f  61 72 72 61 79 5f 64 65  |e.e_bit_array_de|
00000090  6c 65 74 65 00 65 5f 62  69 74 5f 61 72 72 61 79  |lete.e_bit_array|
000000a0  5f 6d 6f 76 65 5f 72 6f  77 00 65 5f 62 69 74 5f  |_move_row.e_bit_|
000000b0  61 72 72 61 79 5f 69 6e  73 65 72 74 00 65 5f 62  |array_insert.e_b|
000000c0  69 74 5f 61 72 72 61 79  5f 67 65 74 5f 74 79 70  |it_array_get_typ|
000000d0  65 00 67 5f 6f 6e 63 65  5f 69 6e 69 74 5f 65 6e  |e.g_once_init_en|
000000e0  74 65 72 5f 69 6d 70 6c  00 67 5f 69 6e 74 65 72  |ter_impl.g_inter|
000000f0  6e 5f 73 74 61 74 69 63  5f 73 74 72 69 6e 67 00  |n_static_string.|
00000100  67 5f 74 79 70 65 5f 72  65 67 69 73 74 65 72 5f  |g_type_register_|
00000110  73 74 61 74 69 63 5f 73  69 6d 70 6c 65 00 67 5f  |static_simple.g_|
00000120  6f 6e 63 65 5f 69 6e 69  74 5f 6c 65 61 76 65 00  |once_init_leave.|
00000130  65 5f 62 69 74 5f 61 72  72 61 79 5f 6e 65 77 00  |e_bit_array_new.|
00000140  65 5f 73 6f 72 74 65 72  5f 6e 65 65 64 73 5f 73  |e_sorter_needs_s|
00000150  6f 72 74 69 6e 67 00 65  5f 73 6f 72 74 65 72 5f  |orting.e_sorter_|
00000160  67 65 74 5f 73 6f 72 74  65 64 5f 74 6f 5f 6d 6f  |get_sorted_to_mo|
00000170  64 65 6c 5f 61 72 72 61  79 00 65 5f 73 6f 72 74  |del_array.e_sort|
00000180  65 72 5f 67 65 74 5f 6d  6f 64 65 6c 5f 74 6f 5f  |er_get_model_to_|
00000190  73 6f 72 74 65 64 5f 61  72 72 61 79 00 65 5f 73  |sorted_array.e_s|
000001a0  6f 72 74 65 72 5f 73 6f  72 74 65 64 5f 74 6f 5f  |orter_sorted_to_|
000001b0  6d 6f 64 65 6c 00 65 5f  73 6f 72 74 65 72 00 fe  |model.e_sorter..|
000001c0  ff ff 82 fe ff ff f5 22  0e 19 56 3a 2f 01 00 fe  |......."..V:/...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 98 f3 62 10 00 00  |............b...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdd1

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 80 01 00  |.<.MSWIN4.1.....|
00000010  02 00 02 00 00 f8 f5 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  4e 7e 7a 00 80 00 29 be  4a f0 49 20 20 20 20 20  |N~z...).J.I     |
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 fa f4  |      FAT16   ..|
00000040  31 c0 8e d8 bd 00 7c b8  e0 1f 8e c0 89 ee 89 ef  |1.....|.........|
00000050  b9 00 01 f3 a5 ea 5e 7c  e0 1f 00 00 60 00 8e d8  |......^|....`...|
00000060  8e d0 8d 66 a0 fb 80 7e  24 ff 75 03 88 56 24 c7  |...f...~$.u..V$.|
00000070  46 c0 10 00 c7 46 c2 01  00 8b 76 1c 8b 7e 1e 03  |F....F....v..~..|
00000080  76 0e 83 d7 00 89 76 d2  89 7e d4 8a 46 10 98 f7  |v.....v..~..F...|
00000090  66 16 01 c6 11 d7 89 76  d6 89 7e d8 8b 5e 0b b1  |f......v..~..^..|
000000a0  05 d3 eb 8b 46 11 31 d2  f7 f3 89 46 d0 01 c6 83  |....F.1....F....|
000000b0  d7 00 89 76 da 89 7e dc  8b 46 d6 8b 56 d8 8b 7e  |...v..~..F..V..~|
000000c0  d0 c4 5e 5a e8 98 00 72  2f c4 7e 5a b9 0b 00 be  |..^Z...r/.~Z....|
000000d0  f1 7d 57 f3 a6 5f 26 8b  45 1a 74 0b 83 c7 20 26  |.}W.._&.E.t... &|
000000e0  80 3d 00 75 e7 72 56 50  c4 5e 5a 8b 7e 16 8b 46  |.=.u.rVP.^Z.~..F|
000000f0  d2 8b 56 d4 e8 68 00 58  72 43 1e 07 8e 5e 5c bf  |..V..h.XrC...^\.|
00000100  00 20 ab 89 c6 8b 56 5c  01 f6 73 03 80 c6 10 8e  |. ....V\..s.....|
00000110  da ad 3d f8 ff 72 eb 31  c0 ab 0e 1f c4 5e 5a be  |..=..r.1.....^Z.|
00000120  00 20 ad 09 c0 74 24 48  48 8b 7e 0d 81 e7 ff 00  |. ...t$HH.~.....|
00000130  f7 e7 03 46 da 13 56 dc  e8 24 00 73 e5 e8 17 00  |...F..V..$.s....|
00000140  20 65 72 72 00 30 e4 cd  16 cd 19 8a 5e 24 ff 6e  | err.0......^$.n|
00000150  5a 31 db b4 0e cd 10 5e  ac 56 3c 00 75 f3 c3 56  |Z1.....^.V<.u..V|
00000160  89 46 c8 89 56 ca 8c 46  c6 89 5e c4 b4 41 bb aa  |.F..V..F..^..A..|
00000170  55 8a 56 24 84 d2 74 19  cd 13 72 15 d1 e9 81 db  |U.V$..t...r.....|
00000180  54 aa 75 0d 8d 76 c0 89  5e cc 89 5e ce b4 42 eb  |T.u..v..^..^..B.|
00000190  2c 8b 4e c8 8b 56 ca 8a  46 18 f6 66 1a 91 f7 f1  |,.N..V..F..f....|
000001a0  92 f6 76 18 89 d1 88 c6  86 e9 d0 c9 d0 c9 8a 46  |..v............F|
000001b0  18 28 e0 fe c4 08 e1 c4  5e c4 b8 01 02 8a 56 24  |.(......^.....V$|
000001c0  cd 13 73 06 30 e4 cd 13  eb a2 8b 46 0b f6 76 c0  |..s.0......F..v.|
000001d0  01 46 c6 83 46 c8 01 83  56 ca 00 4f 75 ea 8e 46  |.F..F...V..Ou..F|
000001e0  c6 5e c3 00 00 00 00 00  00 00 00 00 00 00 00 00  |.^..............|
000001f0  00 46 42 57 54 4c 4f 41  44 42 49 4e 00 00 55 aa  |.FBWTLOADBIN..U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc
```Hope there's some clues here.

BTW, thanks all . . . am really in a panic right now even though I can always do a reinstall with the LiveCD . . . as I said before, just don't want to wipe out my existing configs (and there's other considerations that bother me too with this situation).

---

### Post by BobJam on 2011-05-04
BTW, you guys are my only lifeline right now.

Lemme' 'splain what the other thing is that I'm worried about right now and why I'm really hoping I can restore this boot.

I have all my passwords stored in an encrypted file in a Windows program in a VM I was running.

I did store them in a Oo spreadsheet password protected file on one of my USB sticks, but unfortunately the last time I did that was a couple of months ago, and I've since changed all my email passwords.

They are the "generated" type of passwords and consist of upper and lower case, numbers, and symbols.

Bottom line, I can't get to my password program unless I restore the boot.

In the alternative if I am forced to do a clean install, could I save my VBox config in my home directory (which I can access with this LiveCD) to a USB stick and then paste it into my clean install . . . would that give me the same VM back?

Anyway, I really don't want to go through that if I don't have to.

Fortunately, the log in password for this forum was one of the few that I could remember.

In any case, no email right now.

Again, you folks are the only chance I have right now of recovering my existing boot.  So please hang in.

TIA

---

### Post by ~Plue on 2011-05-04
> **BobJam said:**
> 
```

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1
#UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda6
#UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d /home           ext3    relatime        0       2
/dev/sda5
UUID=f07345d7-f056-47e4-8bdc-6adce994574f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
You've commented out the root file system and the /home partition and uncommented only the /dev/device label without indicating where to mount it etc..
Modify the file as in the post by oldfred and the computer should boot fine on the next reboot

---

### Post by BobJam on 2011-05-04
BTW, here are two things that I've done recently that may offer some clues.

1.  I installed XAMPP and Joomla on my local machine and am trying to get my website on my local machine so that I test edits first and then FTP them to the live site if they work.

Right now I'm editing the live site, which is not a very good idea.

Before this calamity, I was about to transfer the db from the live site to mine.

2.  I installed BUM because I thought I might be able to use it to disable a service that was running MySQL and PHP in the background and conflicting with my XAMPP/LAMPP config.  I believe I did disable some kind of "Avahi" service, which probably didn't have anything to do with the two instances of those things running, but the problem did go away.

Plus, I was able to start up just fine for a few days after I disabled that service.  While it probably didn't have anything to do with my SQL and PHP issue, it doesn't seem like it would be related to this either.

I'm just grabbing at straws looking for a proximate cause . . . but really don't see one.

---

### Post by BobJam on 2011-05-04
@ ~Plue,

Wait a  minute . . . wait a minute.

You mean like this?:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sda1
UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 /               ext3    relatime,errors=remount-ro 0       1
#/dev/sda6
UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d /home           ext3    relatime        0       2
#/dev/sda5
UUID=f07345d7-f056-47e4-8bdc-6adce994574f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by ~Plue on 2011-05-04
> **BobJam said:**
> @ ~Plue,

Wait a  minute . . . wait a minute.

You mean like this?:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sda1
UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 /               ext3    relatime,errors=remount-ro 0       1
#/dev/sda6
UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d /home           ext3    relatime        0       2
#/dev/sda5
UUID=f07345d7-f056-47e4-8bdc-6adce994574f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
Exactly.

---

### Post by BobJam on 2011-05-04
@ Plue,

OK . . . that IS my existing fstab file, and now I get the message the same as was in my OP.

And here's the latest iteration of that script:

               ```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Acer 3 is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06cd1510

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    48,162,869    48,162,807  83 Linux
/dev/sda2          48,162,870   488,392,064   440,229,195   5 Extended
/dev/sda5         468,519,723   488,392,064    19,872,342  82 Linux swap / Solaris
/dev/sda6          48,162,996   323,083,214   274,920,219  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4051 MB, 4051697152 bytes
255 heads, 63 sectors/track, 492 cylinders, total 7913471 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  38     7,839,719     7,839,682   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4110 MB, 4110227968 bytes
181 heads, 14 sectors/track, 3168 cylinders, total 8027789 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1dad1dad

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63     8,027,788     8,027,726   6 FAT16


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 4085 MB, 4085062144 bytes
255 heads, 63 sectors/track, 496 cylinders, total 7978637 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        41116a1e-1ea3-4ca3-bd34-ff5014d079b0   ext3                                     
/dev/sda5        f07345d7-f056-47e4-8bdc-6adce994574f   swap                                     
/dev/sda6        0cf7ace8-d9ae-43f6-a410-6ebafb3a072d   ext3                                     
/dev/sdb1        B804-AE1B                              vfat       Cruzer                        
/dev/sdd1        49F0-4ABE                              vfat                                     
/dev/sde1        4095-368A                              vfat       7805-OEA8                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /media/7805-OEA8         vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdb1        /media/Cruzer            vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdd1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda6        /media/disk-1            ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sda1        /media/disk-2            ext3       (rw,nosuid,nodev,uhelper=hal)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
# timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=41116a1e-1ea3-4ca3-bd34-ff5014d079b0

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-23-generic
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.31-23-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-23-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-23-generic (recovery mode)
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.31-23-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro  single
initrd        /boot/initrd.img-2.6.31-23-generic

title        Ubuntu 9.10, kernel 2.6.31-22-generic
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, kernel 2.6.28-19-generic
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-19-generic (recovery mode)
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 9.10, kernel 2.6.27-17-generic
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-17-generic (recovery mode)
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 ro  single
initrd        /boot/initrd.img-2.6.27-17-generic

title        Ubuntu 9.10, memtest86+
uuid        41116a1e-1ea3-4ca3-bd34-ff5014d079b0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sda1
UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 /               ext3    relatime,errors=remount-ro 0       1
#/dev/sda6
UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d /home           ext3    relatime        0       2
#/dev/sda5
UUID=f07345d7-f056-47e4-8bdc-6adce994574f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   3.3GB: boot/grub/menu.lst
   4.8GB: boot/grub/stage2
  16.9GB: boot/initrd.img-2.6.27-17-generic
  16.9GB: boot/initrd.img-2.6.28-19-generic
   3.1GB: boot/initrd.img-2.6.31-22-generic
   3.4GB: boot/initrd.img-2.6.31-23-generic
   4.8GB: boot/vmlinuz-2.6.27-17-generic
   4.8GB: boot/vmlinuz-2.6.28-19-generic
   3.5GB: boot/vmlinuz-2.6.31-22-generic
  16.9GB: boot/vmlinuz-2.6.31-23-generic
   3.4GB: initrd.img
   3.1GB: initrd.img.old
  16.9GB: vmlinuz
   3.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  5f 62 69 74 5f 61 72 72  61 79 5f 69 6e 76 65 72  |_bit_array_inver|
00000010  74 5f 73 65 6c 65 63 74  69 6f 6e 00 65 5f 62 69  |t_selection.e_bi|
00000020  74 5f 61 72 72 61 79 5f  73 65 6c 65 63 74 5f 61  |t_array_select_a|
00000030  6c 6c 00 65 5f 62 69 74  5f 61 72 72 61 79 5f 73  |ll.e_bit_array_s|
00000040  65 6c 65 63 74 5f 73 69  6e 67 6c 65 5f 72 6f 77  |elect_single_row|
00000050  00 65 5f 62 69 74 5f 61  72 72 61 79 5f 63 6c 65  |.e_bit_array_cle|
00000060  61 72 00 65 5f 62 69 74  5f 61 72 72 61 79 5f 64  |ar.e_bit_array_d|
00000070  65 6c 65 74 65 5f 73 69  6e 67 6c 65 5f 6d 6f 64  |elete_single_mod|
00000080  65 00 65 5f 62 69 74 5f  61 72 72 61 79 5f 64 65  |e.e_bit_array_de|
00000090  6c 65 74 65 00 65 5f 62  69 74 5f 61 72 72 61 79  |lete.e_bit_array|
000000a0  5f 6d 6f 76 65 5f 72 6f  77 00 65 5f 62 69 74 5f  |_move_row.e_bit_|
000000b0  61 72 72 61 79 5f 69 6e  73 65 72 74 00 65 5f 62  |array_insert.e_b|
000000c0  69 74 5f 61 72 72 61 79  5f 67 65 74 5f 74 79 70  |it_array_get_typ|
000000d0  65 00 67 5f 6f 6e 63 65  5f 69 6e 69 74 5f 65 6e  |e.g_once_init_en|
000000e0  74 65 72 5f 69 6d 70 6c  00 67 5f 69 6e 74 65 72  |ter_impl.g_inter|
000000f0  6e 5f 73 74 61 74 69 63  5f 73 74 72 69 6e 67 00  |n_static_string.|
00000100  67 5f 74 79 70 65 5f 72  65 67 69 73 74 65 72 5f  |g_type_register_|
00000110  73 74 61 74 69 63 5f 73  69 6d 70 6c 65 00 67 5f  |static_simple.g_|
00000120  6f 6e 63 65 5f 69 6e 69  74 5f 6c 65 61 76 65 00  |once_init_leave.|
00000130  65 5f 62 69 74 5f 61 72  72 61 79 5f 6e 65 77 00  |e_bit_array_new.|
00000140  65 5f 73 6f 72 74 65 72  5f 6e 65 65 64 73 5f 73  |e_sorter_needs_s|
00000150  6f 72 74 69 6e 67 00 65  5f 73 6f 72 74 65 72 5f  |orting.e_sorter_|
00000160  67 65 74 5f 73 6f 72 74  65 64 5f 74 6f 5f 6d 6f  |get_sorted_to_mo|
00000170  64 65 6c 5f 61 72 72 61  79 00 65 5f 73 6f 72 74  |del_array.e_sort|
00000180  65 72 5f 67 65 74 5f 6d  6f 64 65 6c 5f 74 6f 5f  |er_get_model_to_|
00000190  73 6f 72 74 65 64 5f 61  72 72 61 79 00 65 5f 73  |sorted_array.e_s|
000001a0  6f 72 74 65 72 5f 73 6f  72 74 65 64 5f 74 6f 5f  |orter_sorted_to_|
000001b0  6d 6f 64 65 6c 00 65 5f  73 6f 72 74 65 72 00 fe  |model.e_sorter..|
000001c0  ff ff 82 fe ff ff f5 22  0e 19 56 3a 2f 01 00 fe  |......."..V:/...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 98 f3 62 10 00 00  |............b...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdd1

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 80 01 00  |.<.MSWIN4.1.....|
00000010  02 00 02 00 00 f8 f5 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  4e 7e 7a 00 80 00 29 be  4a f0 49 20 20 20 20 20  |N~z...).J.I     |
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 fa f4  |      FAT16   ..|
00000040  31 c0 8e d8 bd 00 7c b8  e0 1f 8e c0 89 ee 89 ef  |1.....|.........|
00000050  b9 00 01 f3 a5 ea 5e 7c  e0 1f 00 00 60 00 8e d8  |......^|....`...|
00000060  8e d0 8d 66 a0 fb 80 7e  24 ff 75 03 88 56 24 c7  |...f...~$.u..V$.|
00000070  46 c0 10 00 c7 46 c2 01  00 8b 76 1c 8b 7e 1e 03  |F....F....v..~..|
00000080  76 0e 83 d7 00 89 76 d2  89 7e d4 8a 46 10 98 f7  |v.....v..~..F...|
00000090  66 16 01 c6 11 d7 89 76  d6 89 7e d8 8b 5e 0b b1  |f......v..~..^..|
000000a0  05 d3 eb 8b 46 11 31 d2  f7 f3 89 46 d0 01 c6 83  |....F.1....F....|
000000b0  d7 00 89 76 da 89 7e dc  8b 46 d6 8b 56 d8 8b 7e  |...v..~..F..V..~|
000000c0  d0 c4 5e 5a e8 98 00 72  2f c4 7e 5a b9 0b 00 be  |..^Z...r/.~Z....|
000000d0  f1 7d 57 f3 a6 5f 26 8b  45 1a 74 0b 83 c7 20 26  |.}W.._&.E.t... &|
000000e0  80 3d 00 75 e7 72 56 50  c4 5e 5a 8b 7e 16 8b 46  |.=.u.rVP.^Z.~..F|
000000f0  d2 8b 56 d4 e8 68 00 58  72 43 1e 07 8e 5e 5c bf  |..V..h.XrC...^\.|
00000100  00 20 ab 89 c6 8b 56 5c  01 f6 73 03 80 c6 10 8e  |. ....V\..s.....|
00000110  da ad 3d f8 ff 72 eb 31  c0 ab 0e 1f c4 5e 5a be  |..=..r.1.....^Z.|
00000120  00 20 ad 09 c0 74 24 48  48 8b 7e 0d 81 e7 ff 00  |. ...t$HH.~.....|
00000130  f7 e7 03 46 da 13 56 dc  e8 24 00 73 e5 e8 17 00  |...F..V..$.s....|
00000140  20 65 72 72 00 30 e4 cd  16 cd 19 8a 5e 24 ff 6e  | err.0......^$.n|
00000150  5a 31 db b4 0e cd 10 5e  ac 56 3c 00 75 f3 c3 56  |Z1.....^.V<.u..V|
00000160  89 46 c8 89 56 ca 8c 46  c6 89 5e c4 b4 41 bb aa  |.F..V..F..^..A..|
00000170  55 8a 56 24 84 d2 74 19  cd 13 72 15 d1 e9 81 db  |U.V$..t...r.....|
00000180  54 aa 75 0d 8d 76 c0 89  5e cc 89 5e ce b4 42 eb  |T.u..v..^..^..B.|
00000190  2c 8b 4e c8 8b 56 ca 8a  46 18 f6 66 1a 91 f7 f1  |,.N..V..F..f....|
000001a0  92 f6 76 18 89 d1 88 c6  86 e9 d0 c9 d0 c9 8a 46  |..v............F|
000001b0  18 28 e0 fe c4 08 e1 c4  5e c4 b8 01 02 8a 56 24  |.(......^.....V$|
000001c0  cd 13 73 06 30 e4 cd 13  eb a2 8b 46 0b f6 76 c0  |..s.0......F..v.|
000001d0  01 46 c6 83 46 c8 01 83  56 ca 00 4f 75 ea 8e 46  |.F..F...V..Ou..F|
000001e0  c6 5e c3 00 00 00 00 00  00 00 00 00 00 00 00 00  |.^..............|
000001f0  00 46 42 57 54 4c 4f 41  44 42 49 4e 00 00 55 aa  |.FBWTLOADBIN..U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc
```And here also is the blkid output:

```
/dev/sda1: UUID="41116a1e-1ea3-4ca3-bd34-ff5014d079b0" TYPE="ext3" 
/dev/sda5: UUID="f07345d7-f056-47e4-8bdc-6adce994574f" TYPE="swap" 
/dev/sda6: UUID="0cf7ace8-d9ae-43f6-a410-6ebafb3a072d" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: LABEL="Cruzer" UUID="B804-AE1B" TYPE="vfat" 
/dev/sdd1: SEC_TYPE="msdos" UUID="49F0-4ABE" TYPE="vfat" 
/dev/sde1: LABEL="7805-OEA8" UUID="4095-368A" TYPE="vfat" 
ubuntu@ubuntu:~$
```Incidentally, and I said this in my OP, the UUID shown in blkid here, and that is also in my fstab file and in the script above, is EXACTLY the same UUID shown for "/home" in that bothersome boot up message that announces that the UUID is NOT mounted.and doesn't allow me to boot.

Anyway, the latest iteration of fstab as you and oldfred recommended DOES NOT remedy the problem.

So . . . more ideas?

And, BTW, thanks VERY much for trying to help me out.  Ready and willing (and hopeful) to do more so I can avoid a clean install.

---

### Post by BobJam on 2011-05-04
@ andrewthomas,

I remmed out the lines you suggested in the fstab file, EXCEPT for the CDROM UUID:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1
#UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda6
#UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d /home           ext3    relatime        0       2
/dev/sda5
#UUID=f07345d7-f056-47e4-8bdc-6adce994574f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```Still didn't boot, but now I get:

"/tmp: waiting for (null)
:waiting for /dev/sda5
Press ESC to enter recovery shell"

Incidentally, to all, this isn't my current fstab.  Just tried the andrewthomas one about an hour ago and am trying to catch up.

My current fstab is as I replied to ~Plue above:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sda1
UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 /               ext3    relatime,errors=remount-ro 0       1
#/dev/sda6
UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d /home           ext3    relatime        0       2
#/dev/sda5
UUID=f07345d7-f056-47e4-8bdc-6adce994574f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```But none of the iterations seem to work.  My head is starting to hurt with all these iterations of fstab.

Back to the BIOS and change the boot order, test, back to the BIOS and change the boot order, test . . . sheeeesh, I've reallly gotten myself into a mess . . .so far though it seems to be a mystery buried in the ether.

More suggestions?

---

### Post by ~Plue on 2011-05-04
> **BobJam said:**
> Incidentally, and I said this in my OP, the UUID  shown in blkid here, and that is also in my fstab file and in the script  above, is EXACTLY the same UUID shown for "/home" in that bothersome  boot up message that announces that the UUID is NOT mounted.and doesn't  allow me to boot.


That is a bit odd..Try checking the filesystem for errors
```

sudo umount /dev/sda1 && sudo umount /dev/sda6
sudo fsck.ext3 -f /dev/sda1
sudo fsck.ext3 -f /dev/sda6
```edit:// Missed you last post there,
If you want to use the /dev/disk-label, you sould also copy the options used in the line by uuid.
i.e, instead of using only /dev/sda1, you should also define the filesystem, the mountpoint and other options 
```
/dev/sda1  /  ext3  relatime,errors=remount-ro   0  1  
```In any case, try the fsck before making any other changes

---

### Post by Lateralis on 2011-05-04
This is a general comment to you about fstab BobJam.  When mounting a disc you can either specify /dev/sdXY or the UUID.  This identification is the first thing in each uncommented line in an fstab file.  But you need other stuff after it, for instance a mount point, mount options, filesystem type etc...  Otherwise the system will not know what to do with these partitions and crap out.  So simply having 

```

/dev/sda6

```

as a line in fstab will lead to errors.  As it says in fstab, you need the following in order to mount the filesystem:

```

<file system> <mount point>   <type>  <options>       <dump>  <pass>

```

If you did want to try the /dev/sdXY method of mounting, then try the following:

```

/dev/sda1  /               ext3    relatime,errors=remount-ro 0       1
#UUID=41116a1e-1ea3-4ca3-bd34-ff5014d079b0 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda6 /home           ext3    relatime        0       2
#UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d /home           ext3    relatime        0       2
/dev/sda5 none            swap    sw              0       0
#UUID=f07345d7-f056-47e4-8bdc-6adce994574f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I've left the UUID lines intact but commented out, so they are there for quick retrieval.  

Note however, I don't think this will actually fix your problem.  From the what you said in your OP, your partitions are being found OK but there is a problem mounting them.  This is quite separate from the partitions not being found at all.  

One thing you could try is to change the /dev/sda6 line to

```

/dev/sda6 /home           ext3    relatime,**errors=remount-ro**        0       2

```

If you are able to boot then /home will be read only.  However, iIt may give you the opportunity of saving everything that you need.  If your system doesn't boot then something more fundamental is going on.

---

### Post by BobJam on 2011-05-04
@ ~Plue,

A little shaky on this because of the warning:

```
ubuntu@ubuntu:~$ sudo fsck.ext3 -f /dev/sda1
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
ubuntu@ubuntu:~$ sudo fsck.ext3 -f /dev/sda6
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda6 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted
```So, should I go ahead with it?  Can I "unmount" them and run the file check and then mount them again?  What would the commands be?

Something curious here,  but I don't know if I'm reading this right . . . it says that the file systems are MOUNTED yet the message that I'm getting on boot says /home UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d ISN'T.

---

### Post by ~Plue on 2011-05-04
> **BobJam said:**
> @ ~Plue,

A little shaky on this because of the warning:
So, should I go ahead with it?  Can I "unmount" them and run the file check and then mount them again?  What would the commands be?

Something curious here,  but I don't know if I'm reading this right . . . it says that the file systems are MOUNTED yet the message that I'm getting on boot says /home UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d ISN'T.
Thats because the partitions are mounted in the live session, I've edited my previous post to include the commands for unmounting the partitions

---

### Post by BobJam on 2011-05-04
> **~Plue said:**
> Thats because the partitions are mounted in the live session, I've edited my previous post to include the commands for unmounting the partitionsThen after the file checks don't I need to remoount them if I want to be able see them with the LiveCD?  And the command for that would be . . .?  (I'm wondering if Lateralis's comments come in here and it's not just a simple "mount /dev/sda6 /home" command).

I don't want to lose the ability to see and manipulate these things with the LiveCD.

I'm also afraid of losing the ability of loading the CD, which is why I didn't REM out the cdrom line as andrewthomas suggested.

Maybe unnecessary fears, but I'm hanging by a thread here. . . it would be like losing connectivity right now and not being able to get to this thread.

---

### Post by Lateralis on 2011-05-04
The fstab in /dev/sda6 is only there for the installed version of Ubuntu.  Anything you change there will have no effect on the LiveCD session.  So if you comment out the CD line in the fstab in /dev/sda1 then you will have no working CD in that *installed* version.  But as you can't boot to it, it doesn't matter! 

If you do unmount the drives then you can remount them again.  Open up Nautilus (in Natty, there's the /home file launcher) and click the drives in the left-hand pane.  In classic Gnome, click Places and then the drives to mount them.

---

### Post by BobJam on 2011-05-04
@ ~Plue,

OK . . . here are the file checks:

```
ubuntu@ubuntu:~$ sudo umount /dev/sda1 && sudo umount /dev/sda6
ubuntu@ubuntu:~$ sudo fsck.ext3 -f /dev/sda1
e2fsck 1.41.3 (12-Oct-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 222897/1507328 files (1.2% non-contiguous), 1270274/6020350 blocks
ubuntu@ubuntu:~$ sudo fsck.ext3 -f /dev/sda6
e2fsck 1.41.3 (12-Oct-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda6: 68737/8593408 files (2.1% non-contiguous), 20398618/34365027 blocks
ubuntu@ubuntu:~$
```I really don't know what I'm looking at, but assuming these are OK, then I would guess not only is everything in order there, but as we have seen already, the fstab file seems to be in order too.

Consequently my guess (I'm wayyy out on a limb here because most of this stuff is wayyy over my head) would be that whatever my problem is, and as I think maybe Lateralis intimated, it goes a lot further than just the fstab file.

Is there a services file script, or a daemon file script, or a log file that I can copy and paste here that you guys can look at and maybe get a clue?

And, BTW Lateralis, thanks for the reassurance on the mounting issue.  Yes, they showed up very nicely on nautilus and all I had to do was click them to remount them.

My next step will be to copy that fstab file Lateralis made on the /dev/sda method to see if at least I can boot, even if it's just "read only", and maybe make copies of that password file I was talking about.

Not the ultimate solution I'm looking for, which Lateralis pointed out, but it may be the only option I have left.

Not ready to throw in the towel yet, but that point seems to be coming closer and closer.

---

### Post by Lateralis on 2011-05-04
> **BobJam said:**
> @ ~Plue,

Is there a services file script, or a daemon file script, or a log file that I can copy and paste here that you guys can look at and maybe get a clue?

And, BTW Lateralis, thanks for the reassurance on the mounting issue.  Yes, they showed up very nicely on nautilus and all I had to do was click them to remount them.

My next step will be to copy that fstab file Lateralis made on the /dev/sda method to see if at least I can boot, even if it's just "read only", and maybe make copies of that password file I was talking about.

Not the ultimate solution I'm looking for, which Lateralis pointed out, but it may be the only option I have left.

Not ready to throw in the towel yet, but that point seems to be coming closer and closer.

On the logs, yes, there is.  In the Live session, mount your '/' partition (/dev/sda1 I think), open a terminal and navigate to the /var/log directory on sda1.  Then type 

```

cat dmesg | grep sd

```

I don't know if that will tell us anything, but dmesg is where messages from the kernel get stored.  If the system is trying to mount the /dev/sda6 but is struggling for some reason there will be a message.  

As for my /dev/sda "method", stating /dev/sda1 etc. in fstab will not mount it as read only, but the option "errors=remount-ro" will tell the system to mount the specified filesystem as read-only in the event of an error.  As I say, I'm not sure that will work, but if you are able to get into your Ubuntu with a read only /home you may be able to save whatever documents you need.  But that's also still only a may.

---

### Post by BobJam on 2011-05-04
@ Lateralis,

Whoa Dude.  Wow!!!!

Thanks VERY VERY much Lateralis . . . and thanks to everyone else too . . . you saved my butt big time.

I copied and pasted your /dev/sda method, and just for the heck of it I bounced back into my local machine AND IT WORKED.  I'm sure it was those columns you put in there so that the /dev/sda lines had all the info for mounting.  And I'm pretty sure the thing is writing to the /home directory, so it's certainly not read only.

My next step was going to be to try your suggestion to add the "errors=remount-ro" into the /dev/sda6 line, which as I understand it would have made it read-only.

But, thankfully, it doesn't look like I have to go that far.

I think the key here was making a complete line including all the columns, as you emphasized, rather than just a simple /dev/sda<whatever>.  That may have been included in some of the other stuff I looked at when I first started having this problem, but if it was I overlooked it.  Your emphasis on that tip was just the right medicine.

I checked in Google, and this thread has already been indexed, so anybody searching on "One or more of the mounts in . . . ", the message that I quoted in my OP, will get a hit on this thread.  Your tip and emphasis will definitely help others.

I would mark this "SOLVED" but I want to leave it "Open" for the moment to see if anybody has any comments on why the UUID line wasn't working.  **In fact, I guess Hedgehog 1's caution in post #4 applies here. ** I would like to get back to UUID's in my fstab file, but for now I'm happy.  **I guess I need to make sure at the moment that I don't mess with changing disks or partitions.**

And, even though it seems like it's "solved" for now, here's that log you wanted to look at:

```
********:~$ cd /
********:/$ cd /var/log
********:/var/log$ cat dmesg | grep sd
[    1.492265] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.492304] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.492347] sd 0:0:0:0: [sda] Write Protect is off
[    1.492350] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.492372] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.492487]  sda:
[    1.542653]  sda1 sda2 < sda5 sda6 >
[    1.559610] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.211280] sd 7:0:0:0: Attached scsi generic sg2 type 0
[    8.211976] sd 7:0:0:0: [sdb] 7913471 512-byte logical blocks: (4.05 GB/3.77 GiB)
[    8.212348] sd 7:0:0:0: [sdb] Write Protect is off
[    8.212350] sd 7:0:0:0: [sdb] Mode Sense: 45 00 00 08
[    8.212353] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[    8.212910] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    8.213976] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[    8.213979]  sdb:
[    8.214405] sd 9:0:0:0: Attached scsi generic sg4 type 0
[    8.214797] sd 8:0:0:0: Attached scsi generic sg5 type 0
[    8.215479]  sdb1
[    8.216727] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[    8.216730] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[    8.216915] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    8.219041] sd 9:0:0:0: [sdd] 7978637 512-byte logical blocks: (4.08 GB/3.80 GiB)
[    8.220043] sd 8:0:0:0: [sde] 8027789 512-byte logical blocks: (4.11 GB/3.82 GiB)
[    8.222040] sd 9:0:0:0: [sdd] Write Protect is off
[    8.222043] sd 9:0:0:0: [sdd] Mode Sense: 03 00 00 00
[    8.222045] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[    8.223042] sd 8:0:0:0: [sde] Write Protect is off
[    8.223045] sd 8:0:0:0: [sde] Mode Sense: 03 00 00 00
[    8.223047] sd 8:0:0:0: [sde] Assuming drive cache: write through
[    8.237037] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[    8.237040]  sdd:
[    8.244015] sd 8:0:0:0: [sde] Assuming drive cache: write through
[    8.244018]  sde: sdd1
[    8.251058]  sde1
[    8.252040] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[    8.252043] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[    8.259036] sd 8:0:0:0: [sde] Assuming drive cache: write through
[    8.259039] sd 8:0:0:0: [sde] Attached SCSI removable disk
[   18.670672] Adding 9936160k swap on /dev/sda5.  Priority:-1 extents:1 across:9936160k 
[   18.811757] EXT3 FS on sda1, internal journal
[   20.185604] EXT3 FS on sda6, internal journal
********:/var/log$
```I ran this from my LOCAL MACHINE after it booted up, NOT the LiveCD, so I don't know if this has the information you suspected.

No more LiveCD, for  now anyway.

Thanks again.

(So I guess it may have been the fstab file after all . . . but I'm still a little concerned about the failure to use UUID's)

(And, andrewthomas, I see you had those lines in there also but I don't think I copied and pasted your suggestion in . . . I just had the simple /dev/sda line . . . though I've done so many iterations of this fstab file that I MAY have just not tested it.  In any case, I don't mean to shortchange you . . . thanks also).

---

### Post by Lateralis on 2011-05-04
Hehe.  Glad its all solved, but I didn't really do much. =P  andrewthomas was also the first to suggest using /dev/sdXY, not me.  I just helped to clarify the point a bit.  Also, the fschk may have helped.  I don't know as, to be honest, I've never seen this problem before now!  

My advice now is rather obvious but I think essential: back everything up!  As you know, any loss of data can be really frustrating, especially when that data is hugely important.  If possible make use of Ubuntu One, so that any really important stuff is backed up to the cloud.  I personally use a combination of Ubuntu One and two external hard drives, as well as the internal drive, to ensure all my data is backed up in more than two locations at once.  I've not needed to restore any backups yet, but when the day comes and I lose a drive I'll be sure glad I've got everything backed up *everywhere*!  

As for the UUIDs and so on, I have personally found using /dev/sdXY to be a perfectly valid way of doing things.  I know the Hedge isn't a fan, and for a very good reason, but problems with using the /dev/sdXY really only occur if you are changing hard drives or have a an OS on an external drive which is not always connected, or connected with multiple drives.  Then UUIDs are essential.  But if you're not going to fiddle with partitions, drives or drive orders, then /dev/sdXY should suffice.  Still, using UUIDs is more robust and is preferred.  But no matter what you chose to do I'd strongly suggest making backups your first priority!  :P

---


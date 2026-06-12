---
title: "grub loading..then a black screen appears with nothing"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by nuwave on 2010-02-03
I installed UNR 9.10 with no problems and everything was working smoothly. This morning in my first class I was taking notes with no problems. Later that morning I turn on my Dell Mini 10v and prompts me what I believe was a "safe mode" screen so I can boot. I try to run normally but all I get is a black screen with nothing. I ran it in recovery mode and it gave me the following message.

Gave up waiting for root device. common problems
-Boot args(cat/proc/cmdline)
  -check rootdelay=(did the system wait long enough?)
  -check root=(did the system wait for the right device?)
-Missing modules(cat/proc/modules; IS/dev)
Alert!/dev/disk/by-uuid/d3bb8e26-9798-49 ce-bc57
 -afb6ca6za7ba does not exist. Drop to a shell!

I don't know a lot but I know that this is telling me that it is not recognizing the device where the OS is installed. Why is did this happen and how can fix it!! PLEASE HELP, I don't want to lose all my notes

---

### Post by thulefoth on 2010-02-03
[http://sourceforge.net/apps/mediawik...lems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

---

### Post by nuwave on 2010-02-03
thanks for the quick reply :D but does this process work even if I completely wiped out the Windows OS. All I got on my machine is UNR 9.10, I am able to boot the Live USB but I'm not quite sure how to fix the GRUB issue within the the Live USB.

---

### Post by audiomick on 2010-02-03
Hi.
No need to panic, at least not yet. 
Firstly, I don't think the link from thulefoth will help much. It is referring to a wubi install, which is not what you have.

Just for your information: my (desktop) machine shows exactly that message occasionally. In my case, it most likely has to do with the cheap Samsung drives not getting spun up in time for the boot loader.

I assume you had your computer shut down, and were re-booting, not waking out of suspend or something. I imagine so, I can't see you getting the message otherwise.

Did a later attempt at booting behave any differently?
Just to be sure: the computer didn't get dropped or anything, did it?

As far as your notes go, if you can boot into a live USB, then you should be able to back up your files onto an external drive. In fact, you should be doing this anyway if the computer is going to school with you every day. What if it does get dropped, or stolen?

In order to see what is what with the boot process, go here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
follow the instructions (it works from the live CD/ live USB as well) and post the results file here.

---

### Post by nuwave on 2010-02-03
im checking it out right now, thanks

---

### Post by nuwave on 2010-02-03
ok audiomick did what the other post said but still not sure what im looking for. here is what came out of the "boot info script"

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa42d04a3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   228,476,429   228,476,367  83 Linux
/dev/sda2         228,476,430   234,436,544     5,960,115   5 Extended
/dev/sda5         228,476,493   234,436,544     5,960,052  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4037 MB, 4037017600 bytes
100 heads, 36 sectors/track, 2190 cylinders, total 7884800 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          8,064     7,884,799     7,876,736   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       11f61157-2f8a-4db2-bbe6-92ef67c79bc3   ext2                                     
/dev/sda5        e13fbfa9-4436-4d33-8ecf-15534d6a8736   swap                                     
/dev/sdc1        9CAA-28B2                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /mnt/root                ext4       (rw)
/dev             /mnt/root/dev            none       (rw,bind)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set d3bb8e26-9798-49ce-bc57-afb6ca62a7ba
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d3bb8e26-9798-49ce-bc57-afb6ca62a7ba
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=d3bb8e26-9798-49ce-bc57-afb6ca62a7ba ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d3bb8e26-9798-49ce-bc57-afb6ca62a7ba
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=d3bb8e26-9798-49ce-bc57-afb6ca62a7ba ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d3bb8e26-9798-49ce-bc57-afb6ca62a7ba
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=d3bb8e26-9798-49ce-bc57-afb6ca62a7ba ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d3bb8e26-9798-49ce-bc57-afb6ca62a7ba
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=d3bb8e26-9798-49ce-bc57-afb6ca62a7ba ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d3bb8e26-9798-49ce-bc57-afb6ca62a7ba
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d3bb8e26-9798-49ce-bc57-afb6ca62a7ba ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d3bb8e26-9798-49ce-bc57-afb6ca62a7ba
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d3bb8e26-9798-49ce-bc57-afb6ca62a7ba ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d3bb8e26-9798-49ce-bc57-afb6ca62a7ba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e13fbfa9-4436-4d33-8ecf-15534d6a8736 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 



thanks for the help

---

### Post by audiomick on 2010-02-03
This looks wrong to me:
Grub is looking for this UUID to boot
> menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d3bb8e26-9798-49ce-bc57-afb6ca62a7ba
	linux	/boot/vmlinuz-2.6.31-17-generic root=[COLOR=Red]UUID=d3bb8e26-9798-49ce-bc57-afb6ca62a7ba ro single [/COLOR]
	initrd	/boot/initrd.img-2.6.31-17-generic

Which I can't see in the UUID table
> Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       11f61157-2f8a-4db2-bbe6-92ef67c79bc3   ext2                                     
/dev/sda5        e13fbfa9-4436-4d33-8ecf-15534d6a8736   swap                                     
/dev/sdc1        9CAA-28B2                              vfat                                     

That's all I can say for now. I am sure this can be fixed, but I am not sure how off hand.
I have some things to do right now. Maybe someone else will look in who can help. I will look back later.

---

### Post by oldfred on 2010-02-03
could you also list 

 sudo blkid


Which should be the same as what the boot script listed, but just to confirm the sda is missing.

You also posted your results to the thread with the instructions. there was no need. I suggest you go back and just delete that.

---

### Post by nuwave on 2010-02-03
the result of sudo blkid were

/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="11f61157-2f8a-4db2-bbe6-92ef67c79bc3" TYPE="ext2" 
/dev/sda5: UUID="e13fbfa9-4436-4d33-8ecf-15534d6a8736" TYPE="swap" 
/dev/sdc1: UUID="9CAA-28B2" TYPE="vfat"

the journey continues but im enjoying every bit except for my computer bricking:)

---

### Post by oldfred on 2010-02-03
Your sda1 is missing in action.

I do not know testdisk, but that would be my next try. Others may be able to give more advice but to get started download and review these sites:

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by nuwave on 2010-02-03
wow!! how in the world did that happen?  thanks for the info I will dig some more...

---

### Post by Sky Aisling on 2010-02-03
Hi Nuwave,
When you are at the black screen, have you tried ***alt, control, delete***?

---

### Post by nuwave on 2010-02-03
yup and it just restarts

---

### Post by nuwave on 2010-02-03
> **Sky Aisling said:**
> Hi Nuwave,
When you are at the black screen, have you tried ***alt, control, delete***?

yup it restarts and begins the whole process again and i get the same error message

---

### Post by nuwave on 2010-02-03
> **oldfred said:**
> Your sda1 is missing in action.

I do not know testdisk, but that would be my next try. Others may be able to give more advice but to get started download and review these sites:

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

i tried following what ubuntu.com website said and i got nowhere i think its my own fault of being a newbie but i'll keep trying im working on getting testdisk and running it

---

### Post by nuwave on 2010-02-03
I've hit a brick wall...I'm trying my best to get testdisk installed but I having no luck. The same is for gddrescue, i download but I dont know how to install. I ran terminal which told me to sudo apt-get install (testdisk or gddrescue) but this did nothing it gave an error (couldn't find package testdisk). Any ideas?

---

### Post by meierfra. on 2010-02-04
I don't think there is anything wrong with your partition table. The boot info script was even able to boot /dev/sda1, so also your  file system does not seem  have any serious damage.   

But lets try a file system check:

```
sudo umount /dev/sda1 
```
(thats just in case /dev/sda1 is mounted) and then

```
sudo e2fsck -fyv  /dev/sda1
```

---

### Post by nuwave on 2010-02-04
> **meierfra. said:**
> I don't think there is anything wrong with your partition table. The boot info script was even able to boot /dev/sda1, so also your  file system does not seem  have any serious damage.   

But lets try a file system check:

```
sudo umount /dev/sda1 
```
(thats just in case /dev/sda1 is mounted) and then

```
sudo e2fsck -fyv  /dev/sda1
```

ok here is the output

ubuntu@ubuntu:~$ sudo umount /dev/sda1
[sudo] password for ubuntu: 
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo e2fsck -fyv  /dev/sda1
e2fsck 1.41.9 (22-Aug-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  187288 inodes used (2.62%)
     249 non-contiguous files (0.1%)
     110 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 163820/50
 1560272 blocks used (5.46%)
       0 bad blocks
       1 large file

  134385 regular files
   23201 directories
      68 character device files
      26 block device files
       0 fifos
     390 links
   29592 symbolic links (23307 fast symbolic links)
       7 sockets
--------
  187669 files
ubuntu@ubuntu:~$ 


thanks for the input meierfra i hope this gets us closer to solving:D

---

### Post by meierfra. on 2010-02-04
e2fsck did not find any problems.

Could you post the outputs of

```
sudo blkid -p /dev/sda1
```

and 

```
sudo tune2fs -l /dev/sda1
```
(-l is a lowercase -L)

---

### Post by nuwave on 2010-02-04
> **meierfra. said:**
> e2fsck did not find any problems.

Could you post the outputs of

```
sudo blkid -p /dev/sda1
```

and 

```
sudo tune2fs -l /dev/sda1
```
(-l is a lowercase -L)

Here's the output

ubuntu@ubuntu:~$ sudo blkid -p /dev/sda1
[sudo] password for ubuntu: 
/dev/sda1: ambivalent result (probably more filesystems on the device)
ubuntu@ubuntu:~$ sudo tune2fs -l /dev/sda1
tune2fs 1.41.9 (22-Aug-2009)
Filesystem volume name:   <none>
Last mounted on:          /mnt/root
Filesystem UUID:          d3bb8e26-9798-49ce-bc57-afb6ca62a7ba
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              7143424
Block count:              28559545
Reserved block count:     1427977
Free blocks:              26999273
Free inodes:              6956136
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1017
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Tue Jan 19 15:38:04 2010
Last mount time:          Wed Feb  3 11:29:55 2010
Last write time:          Thu Feb  4 09:13:00 2010
Mount count:              0
Maximum mount count:      25
Last checked:             Thu Feb  4 09:13:00 2010
Check interval:           15552000 (6 months)
Next check after:         Tue Aug  3 10:13:00 2010
Lifetime writes:          14 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      5b973676-afd8-4e73-9401-5ed788f0ceca
Journal backup:           inode blocks
ubuntu@ubuntu:~$

---

### Post by meierfra. on 2010-02-04
> ubuntu@ubuntu:~$ sudo blkid -p /dev/sda1
[sudo] password for ubuntu:
/dev/sda1: ambivalent result (probably more filesystems on the device)

Seems there are some traces of an old file system on /dev/sda1.

Try this
```
sudo dd if=/dev/zero of=/dev/sda1 count=2
```
Be very careful with the dd command.  If it runs for more than just  a couple of seconds, kill the process with "ctrl+c"

---

### Post by nuwave on 2010-02-04
> **meierfra. said:**
> Seems there are some traces of an old file system on /dev/sda1.

Try this
```
sudo dd if=/dev/zero of=/dev/sda1 count=2
```
Be very careful with the dd command.  If it runs for more than just  a couple of seconds, kill the process with "ctrl+c"

I like to give a big thanks to everyone who has helped. so what exactly is this command doing? i just want to make sure I know what I'm doing, this is all a big learning process for me.

---

### Post by nuwave on 2010-02-05
alright here is the output

ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda1 count=2
sudo: /etc/sudoers is mode 0644, should be 0440
Segmentation fault
ubuntu@ubuntu:~$

---

### Post by nuwave on 2010-02-05
ok i found two other post that look promising any thoughts?
 
[http://ubuntuforums.org/showthread.php?t=1353509](http://ubuntuforums.org/showthread.php?t=1353509)
 
[http://ubuntuforums.org/showthread.php?t=1355385](http://ubuntuforums.org/showthread.php?t=1355385)

---

### Post by meierfra. on 2010-02-05
> so what exactly is this command doing? i
The "dd" command  will write zeros to the first two sectors of the partition. An ext4 files system does not use the first two sectors, but other file systems do.  So if you are lucky the "dd" command will remove the data "blkid" is complaining about.

> sudo: /etc/sudoers is mode 0644, should be 0440
That is very weird.  This happens if the permissions of the sudoers file have been changed.  I never have seen this on the LiveCD.  

I suggest to check the LiveCD for defects (Choose the "Check CD for defects" option at the first menu when booting from the CD)

Then try the "dd" command again.


> ok i found two other post that look promising any thoughts?
They have the same symptoms, but the cause seems different.

---

### Post by nuwave on 2010-02-05
> **meierfra. said:**
> The "dd" command  will write zeros to the first two sectors of the partition. An ext4 files system does not use the first two sectors, but other file systems do.  So if you are lucky the "dd" command will remove the data "blkid" is complaining about.


That is very weird.  This happens if the permissions of the sudoers file have been changed.  I never have seen this on the LiveCD.  

I suggest to check the LiveCD for defects (Choose the "Check CD for defects" option at the first menu when booting from the CD)

Then try the "dd" command again.



They have the same symptoms, but the cause seems different.

great thanks I will check the liveCD for defects

---

### Post by nuwave on 2010-02-05
I checked the LiveUSB for defects and there was none. I ran the the command again and it was the same message again...

---

### Post by meierfra. on 2010-02-06
Is your LiveUSB a persistent install? That is, changes are not lost after rebooting?

Is there anything you have done, which might have changed the permissions on the sudoer file?

It might be possible to plug your USB drive into a different computer which has Ubuntu (or some other Linux)  installed, mount the file system of your LiveUSB and then  change the permission on your sudoers file via

```
sudo chmod 440 [mountpoint]/etc/sudoers
```

I never  have done anything like that, but I will look into it.

Or you could reinstall the LiveUSB. A 4GB  flash drive is even big enough for a regular install.

---

### Post by nuwave on 2010-02-06
> I never have done anything like that, but I will look into it.

Or you could reinstall the LiveUSB. A 4GB flash drive is even big enough for a regular install 


When I created the LiveUSB I followed closely the instructions on the Ubuntu site, and it wasn't a persistent install. So I'm not sure how this may have happened I'm going to reinstall the LiveUSB maybe that help

---

### Post by nuwave on 2010-02-06
I reinstalled the LiveUSB and I ran sudo dd if=/dev/zero of=/dev/sda1 count=2 again and I got this

ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda1 count=2
2+0 records in
2+0 records out
1024 bytes (1.0 kB) copied, 0.0586349 s, 17.5 kB/s

I think it did what you were talking about meierfra> The "dd" command will write zeros to the first two sectors of the partition. An ext4 files system does not use the first two sectors, but other file systems do. So if you are lucky the "dd" command will remove the data "blkid" is complaining about. 

I restarted and I got the same thing its still not booting..

---

### Post by meierfra. on 2010-02-06
There is a program called [wipefs ]("http://karelzak.blogspot.com/2009/11/wipefs8.html") which is able to detect the signatures  of most file systems and is also able to erase all the unwanted signatures.  Unfortunately its is very new  and  you will have to compile it from source. If you would like to give that a try, here are the instructions:

Download   [util-linux-ng-2.17.tar.gz]("ftp://ftp.kernel.org/pub/linux/utils/util-linux-ng/v2.17/util-linux-ng-2.17.tar.gz") to your Desktop.

Right click the file and choose "Extract Here"

Open a terminal.

```
cd ~/Desktop
mkdir Util
cd util-linux-ng-2.17
sudo ./configure --prefix=$HOME/Desktop/Util --without-ncurses 
sudo make
sudo make install
```

This installed the Util-Linux package to the folder Util on your desktop.
I tried this and  got  a few error messages from "make" and "make install. But "wipefs" still was working fine for me.

Next  run wipefs via

```
cd  ~/Desktop/Util/sbin
sudo ./wipefs /dev/sda1

```

 "wipefs /dev/sda1"  displays some basic information on all the file systems found on /dev/sda1,    but does  not change anything.   Post that  information.

---

### Post by nuwave on 2010-02-06
> **meierfra. said:**
> There is a program called [wipefs ]("http://karelzak.blogspot.com/2009/11/wipefs8.html") which is able to detect the signatures  of most file systems and is also able to erase all the unwanted signatures.  Unfortunately its is very new  and  you will have to compile it from source. If you would like to give that a try, here are the instructions:

Download   [util-linux-ng-2.17.tar.gz]("ftp://ftp.kernel.org/pub/linux/utils/util-linux-ng/v2.17/util-linux-ng-2.17.tar.gz") to your Desktop.

Right click the file and choose "Extract Here"

Open a terminal.

```
cd ~/Desktop
mkdir Util
cd util-linux-ng-2.17
sudo ./configure --prefix=$HOME/Desktop/Util --without-ncurses 
sudo make
sudo make install
```This installed the Util-Linux package to the folder Util on your desktop.
I tried this and  got  a few error messages from "make" and "make install. But "wipefs" still was working fine for me.

Next  run wipefs via

```
cd  ~/Desktop/Util/sbin
sudo ./wipefs /dev/sda1

``` "wipefs /dev/sda1"  displays some basic information on all the file systems found on /dev/sda1,    but does  not change anything.   Post that  information.


ok here is the output, I believe I did everything right 

```
ubuntu@ubuntu:~/Desktop/util-linux-ng-2.17$ cd  ~/Desktop/Util/sbin
ubuntu@ubuntu:~/Desktop/Util/sbin$ sudo ./wipefs /dev/sda1
offset               type
----------------------------------------------------------------
0x410                minix   [filesystem]

0x438                ext4   [filesystem]
                     UUID:  d3bb8e26-9798-49ce-bc57-afb6ca62a7ba

ubuntu@ubuntu:~/Desktop/Util/sbin$ 
 
```

---

### Post by meierfra. on 2010-02-06
> 0x410                minix   [filesystem]

This is very weird.  You have the minix "signature"     written in the Superblock of your ext4 partition.  That location is supposed to contain the number of free inodes of your   Ubuntu file system. But "tune2fs" had no problem reading the number of free inodes. 

So I'm guessing that by some strange coincidence the number of free inodes of the Ubuntu files system  matches the signature of the mininx file system.

If my theory is correct, you just would have to create one file in your Ubuntu partition to solve your problem.

So try this

```
sudo mount /dev/sda1 /mnt
sudo touch /mnt/empty_file
sudo blkid -p /dev/sda1
```

---

### Post by nuwave on 2010-02-06
ok here is the output

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo touch /mnt/empty_file
ubuntu@ubuntu:~$ sudo blkid -p /dev/sda1
/dev/sda1:ambivalent result (probably more filesystem on the device)

i restarted my machine and it still gave the same problem

---

### Post by meierfra. on 2010-02-07
> ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: you must specify the filesystem type

Sorry, mount is not able to determine the file system type.  I should have thought about that. Try

```
sudo mount -t ext4 /dev/sda1 /mnt
sudo touch /mnt/empty_file
sudo blkid -p /dev/sda1
```

---

### Post by nuwave on 2010-02-07
ok i ran once and it gave me some weird message but I ran it the second time and it gave me this

/dev/sda1: UUID="d3bb8e26-9798-49ce-bc57-afb6ca62a7ba" VERSION="1.0" TYPE="ext4" USAGE="filesystem"

I am so happy to report that my system is FIXED!!:D It started up properly and all my files are safe. I really have to thank you so much meierfra, and everyone else who helped. The journey was wonderful and now I can happily post this as solved

Thanks everyone

---

### Post by meierfra. on 2010-02-07
> I am so happy to report that my system is FIXED!!

Great.  

This is the strangest bug I have ever come across. It can hid anybody with an ext2/3/4 filesystem  at any time, although with a very low probability.

Minix uses the "magic number" 6824 at  the location 0x410  to mark a Minix file system.

0x410 is also the location any ext filesystem uses to record the number of free inodes.
(The number of free inodes is essentially the number of files you are still able to create on the file system)

9320 in little endian  decoding is "6824"  

If the number of free inodes happens to  be  9320 plus a multiple of 65536,  then  the  ext filesystem will write  6824  to the 0x410 location. 

So many programs will gets confused and don't know whether the files system is Minix or Ext.

---

### Post by DenisD on 2010-02-07
Hi,

> **meierfra. said:**
> 
This is the strangest bug I have ever come across. It can hid anybody with an ext2/3/4  at any time, although with a very low probability.

The same bug happened on my laptop 2h ago. Luckily I found this thread. :) Thanks for the correct solution! A lot of people suggested to replace the UUID in Grub with the device-path for the  partition.

1:65535 is not so low compared to thousands of users using Linux every day ;).
I think this should be fixed.

---

### Post by meierfra. on 2010-02-07
> 1:65535 is not so low compared to thousands of users using Linux every day
You are right. It probably happens quite often, but never gets diagnosed right.   I'll bet quite a few people end up reinstalling because  of this.

I'll file a bug report at launchpad.

---

### Post by meierfra. on 2010-02-07
Here is the bug report I filed:

[http://bugs.launchpad.net/ubuntu/+bug/518582](http://bugs.launchpad.net/ubuntu/+bug/518582)

nuwave and DenisD: Could you go to that link and click on

 "This bug affects x people" Does this bug affect you"  ( or "This bug affects you)

to let launchpad now that you have been affected by the bug. Thanks.

---

### Post by truejabber on 2010-02-07
Thanks very much [meierfra.]("http://ubuntuforums.org/member.php?u=552151")! This was frustrating the hell out of me until I found your solution! You rock.

---

### Post by meierfra. on 2010-02-07
> This was frustrating the hell out of me until I found your solution!
Seems this is affecting lots of people.

Just to make it easier for anybody else who has this problem. 
You just need to do this:

```
sudo blkid -p  /dev/[COLOR="Red"]sda1[/COLOR] 
```
(But replace "/dev/sda1"  by the device name of your Ubuntu partition)

It should  return

/dev/sda1: ambivalent result (probably more filesystems on the device)

If it returns something else,   you have a different problem and the following solution will not help you.


```
sudo mount -t [COLOR="Navy"]ext4[/COLOR]  /dev/[COLOR="Red"]sda1[/COLOR] /mnt
```
(if your Ubuntu files system is ext3, use ext3 instead of ext4)

```
 
sudo touch /mnt/empty_file
```
Wait  a couple of seconds for the filesystem  to update its self. Then

```
sudo blkid -p /dev/[COLOR="Red"]sda1[/COLOR] 
```

Hopefully  this will now return something like

/dev/sda1: UUID="d3bb8e26-9798-49ce-bc57-afb6ca62a7ba" VERSION="1.0" TYPE="ext4" USAGE="filesystem"

and you should be all set.


Also could anybody who is affected by this problem please  go to 

[http://bugs.launchpad.net/ubuntu/+bug/518582](http://bugs.launchpad.net/ubuntu/+bug/518582)

 click on

"This bug affects x people" Does this bug affect you" ( or "This bug affects you")

and let launchpad know that this is affecting you,

---

### Post by nuwave on 2010-02-07
> Also could anybody who is affected by this problem please go to 

[http://bugs.launchpad.net/ubuntu/+bug/518582](http://bugs.launchpad.net/ubuntu/+bug/518582)

click on

"This bug affects x people" Does this bug affect you" ( or "This bug affects you")

and let launchpad know that this is affecting you

I reported the bug and it looks like a lot of people are following your fix meierfra! This is very exciting : )

---

### Post by munkydust on 2010-02-16
Thank you very much for figuring this out. I turned my computer on after work and this helped me solve the problem pretty quickly. Cheers guys. Should this be made a Sticky?

---

### Post by meierfra. on 2010-02-16
> Should this be made a Sticky?
I don't know whether four cases in 9 days is enough to make it a sticky. But you can click on the "report abuse" button in left panel (its not only for abuse) and request it.

Also launchpad has been ignoring my  bug report so far. So please let them know that your are affected (see [post 40]("http://ubuntuforums.org/showpost.php?p=8790624&postcount=40"))

---

### Post by eric_1982 on 2010-06-09
I  wasted two days trying to get this fixed on ubuntu 10.04 64-bit server. Finally I found a solution that worked! Thanks you!

---

### Post by Matt__ on 2010-06-09
lol..i wish i had found this days ago...
Im assuming this is the same problem I had.
my mini 10v did the same but also wouldnt let me reinstall 10.04 or any ext4 version of ubuntu as all i got after install was black screen. I eventually tried an old 8.04 disk which used ext2 and installed! which then allowing me to overwrite it with a fresh install of 10.04
(I assume it somehow wrote over the offending 0x410?)

---

### Post by nuwave on 2010-08-12
I think hibernation and running a liveUSB image is what caused this problem for me. Because the other day I put my computer to hibernate, I got curious about another distro and decided to run it as a LiveUSB. Once I was done running the liveUSB I shutdown my machine and tried rebooting Ubuntu but it failed booting and was giving a similar problem. As I was kicking myself on the *** for breaking my system again, I thought about this post and decided to run the same exact commands. To my surprise and relief this fixed my system. So I suggest to everyone if they are trying out a LiveCD or LiveUSB to check if they properly shut-down their system.

---


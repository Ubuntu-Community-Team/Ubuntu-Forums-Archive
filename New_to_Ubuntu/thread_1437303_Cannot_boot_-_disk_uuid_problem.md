---
title: "Cannot boot - disk uuid problem"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by sdj on 2010-03-23
I have an installation of ubuntu on my laptop on which I installed xubuntu-desktop and have been using it fine for some time.

However when I turned it on this evening it will not boot properly, it starts fine but ends up in a blank screen.  When I boot to recovery mode I get a message like** ALERT! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xx$ does not exist** and it puts me into an unfamiliar shell.  I have tried some advice from other similar posts but have not been able to make any progress.  Some of the things I've tried are:

- ran fsck /dev/sda1 and it came up clean.
- mounted sda1 and checked the contents of /mnt/sda1/etc/fstab and /mnt/sda1/boot/grub/menu.lst, they look like the uuid's match.
- when I run 'sudo blkid' there are only entries for /dev/loop0 and /dev/sda5, there's nothing for /dev/sda1

I've been using ubuntu for a few years but am still not that knowledegable about technical stuff as it has generally 'just worked' fine for me.  Is there anything I can try to get my system to boot normally again?  Thanks for any help you can give me.

---

### Post by audiomick on 2010-03-23
Hallo.
I am not likely to be able to help you tonight, I will be off to bed soon. However, I would suggest going here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
and following the instructions to run meierfra's boot info script.

The script reports  just about everything relevant to your boot setup. It should show what has gone wrong. The script can be downloaded and run whilst booted into the live CD.

Post the output here (use code Tags, it is a lot of text. That is the # button at the top of the posting window).

Hopefully someone will be able to decipher it for you soon. I will look back in sometime tomorrow.

I am fairly sure that your problem can be fixed without too much bother.

---

### Post by srs5694 on 2010-03-23
If /dev/sda1 is your root partition and if it appears OK, as is suggested by your original post, then I'd suggest first specifying its name to blkid, as in "sudo blkid /dev/sda1". If you still get nothing, then you may be able to reset the UUID using the -U option to tune2fs, as in:

```

sudo tune2fs -U 1445adc8-3145-4fcb-86df-701f0f711943 /dev/sda1

```

Change the UUID to whatever your root partition is supposed to be using, of course.

If even that doesn't work, then it's trickier, since there's something very strange going on that might indicate serious hard disk problems. Still, if fsck doesn't turn up any problems and you can access the filesystem OK from an emergency disk, as you say you can, I'd suggest just replacing the UUID specifications in /etc/fstab and /boot/grub/menu.lst with /dev/sda1 pointers, at least as a stop-gap. For instance, in /etc/fstab, change:

```

UUID=1445adc8-3145-4fcb-86df-701f0f711943   /        ext3        noauto,noatime    1 2

```

(of course, your UUID will be different) ...to:

```

/dev/sda1            /        ext3        noauto,noatime    1 2

```

If your /boot/grub/menu.lst file uses UUIDs, particularly on the kernel line, change them, too.

Ubuntu's automated tools might not be able be able to properly edit these changes, which could cause problems down the line, but you should at least be able to boot. Before making these changes, back up the original files so you can restore them in the future, should you need to.

---

### Post by sdj on 2010-03-24
Thanks for the suggestions.  I've downloaded and run the boot info script and this is what I get:

```

ubuntu@ubuntu:~/Downloads$ sudo bash /home/ubuntu/Downloads/boot_info_script055.sh 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Downloads
ubuntu@ubuntu:~/Downloads$ cat RESULTS.txt 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed1f86f7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   224,829,674   224,829,612  83 Linux
/dev/sda2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sda5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: ambivalent result (probably more filesystems on the device)
/dev/sda5        ba6c3216-2e85-4004-aa24-d4f8713ce4b0   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

ubuntu@ubuntu:~/Downloads$ 


```When I run 'sudo blkid /dev/sda1' I get no output.

I have not tried the tune2fs command or changing UUIDs yet.  Before I do try it, is there anything in the above output to indicate where the problem might be?

Thanks

---

### Post by sdj on 2010-03-24
Okay I have run the boot info script again this time with sda1 mounted, perhaps this output is more useful.
Thanks

```


ubuntu@ubuntu:~/Downloads$ cat RESULTS.txt 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed1f86f7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   224,829,674   224,829,612  83 Linux
/dev/sda2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sda5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: ambivalent result (probably more filesystems on the device)
/dev/sda5        ba6c3216-2e85-4004-aa24-d4f8713ce4b0   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /mnt/sda1                ext3       (rw)


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
timeout        3

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=54398c51-84bf-47d2-9725-0730031ebd63

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.27-14-generic
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-14-generic (recovery mode)
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=54398c51-84bf-47d2-9725-0730031ebd63 ro  single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 9.10, memtest86+
uuid        54398c51-84bf-47d2-9725-0730031ebd63
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=54398c51-84bf-47d2-9725-0730031ebd63 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ba6c3216-2e85-4004-aa24-d4f8713ce4b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  74.1GB: boot/grub/menu.lst
  71.6GB: boot/grub/stage2
  74.0GB: boot/initrd.img-2.6.27-14-generic
  74.0GB: boot/initrd.img-2.6.28-16-generic
  71.6GB: boot/initrd.img-2.6.31-14-generic
  71.6GB: boot/initrd.img-2.6.31-15-generic
  74.0GB: boot/initrd.img-2.6.31-16-generic
  74.1GB: boot/initrd.img-2.6.31-17-generic
  74.1GB: boot/initrd.img-2.6.31-19-generic
  74.1GB: boot/initrd.img-2.6.31-20-generic
  68.4GB: boot/vmlinuz-2.6.27-14-generic
  74.0GB: boot/vmlinuz-2.6.28-16-generic
  74.0GB: boot/vmlinuz-2.6.31-14-generic
  71.5GB: boot/vmlinuz-2.6.31-15-generic
  74.0GB: boot/vmlinuz-2.6.31-16-generic
  74.0GB: boot/vmlinuz-2.6.31-17-generic
  71.6GB: boot/vmlinuz-2.6.31-19-generic
  74.1GB: boot/vmlinuz-2.6.31-20-generic
  74.1GB: initrd.img
  74.1GB: initrd.img.old
  74.1GB: vmlinuz
  71.6GB: vmlinuz.old
ubuntu@ubuntu:~/Downloads$ 


```

---

### Post by srs5694 on 2010-03-24
Something is preventing auto-detection of the filesystem type and UUID on /dev/sda1, but we knew that from your very first post. I don't know what the problem might be. This is troubling, but OTOH, you say that fsck reports no errors and the filesystem does mount correctly. This seems to suggest that the filesystem is basically sound, although it could be that fsck is just not catching some serious problem. In addition to my previous suggestions, I have two more:


[list]
[*]Do a raw backup of the device, as in "dd if=/dev/sda1 of=/dev/sdb1". This will require a spare drive/partition (/dev/sdb1 in this example) that's at least as large as the original. If you use dd, be *very careful,* particularly with the if= and of= options; if you reverse them, you could wipe out your partition! If you've got some free space somewhere but not enough for a full "raw" backup like this, you could use a pipeline with compression, tar, or some other file-oriented backup utility; however, if the filesystem is hiding some serious corruption, file-oriented backups might not actually back up everything. Post if you need more explicit instructions, and include information on how much space you've got on potential backup media and how much space is used on your root filesystem.
[*]Use the -f option to e2fsck, as in "e2fsck -f /dev/sda1". This will force a more thorough check of the filesystem than your initial fsck probably did. This may uncover (and hopefully correct) some problems. It's also possible, but unlikely, that it will end up making the partition unmountable.
[/list]

---

### Post by sdj on 2010-03-24
I don't have sufficient external storage to do a dd raw backup.  However I've just used the live CD to back up all my data to a usb drive before trying the other suggestions from your earlier post.  These were the results:

- The tune2fs command didn't seem to do anything.  I tried it with sda1 both mounted and unmounted but blkid still didn't show up sda1 and my system still wouldn't boot normally.

- I then replaced the UUID in /etc/fstab with /dev/sda1, and in /boot/grub/menu.lst changed the 'kopt=' line and all 'kernel' lines to use /dev/sda1 as well.  It now boots normally but I'm concerned about the problems down the line that you mentioned.  I will go back into the live CD and try "e2fsck -f /dev/sda1".

Thanks for your help so far.

---

### Post by sdj on 2010-03-24
I've run the file system check and it doesn't seem to have found anything bad:

```


ubuntu@ubuntu:~$ sudo e2fsck -f /dev/sda1
e2fsck 1.41.9 (22-Aug-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 334715/7028736 files (2.2% non-contiguous), 16038295/28103701 blocks
ubuntu@ubuntu:~$


```Does this mean my hard drive is fine?
Not sure if it's relevant but I remember skipping one of the automated fsck on boot recently.

---

### Post by srs5694 on 2010-03-24
At least your system is booting now!

Try posting the result of this command:

```

sudo dumpe2fs -h /dev/sda1

```

This will display various pieces of low-level information on the filesystem. Something there might provide a clue about what's going on.

---

### Post by sdj on 2010-03-25
Here is the output of 'sudo dumpe2fs -h /dev/sda1'

```


dumpe2fs 1.41.9 (22-Aug-2009)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          54398c51-84bf-47d2-9725-0730031ebd63
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              7028736
Block count:              28103701
Reserved block count:     1405185
Free blocks:              12056025
Free inodes:              6693964
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1017
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Filesystem created:       Fri Nov 14 22:01:42 2008
Last mount time:          Thu Mar 25 12:21:17 2010
Last write time:          Wed Mar 24 21:23:59 2010
Mount count:              3
Maximum mount count:      30
Last checked:             Wed Mar 24 21:01:50 2010
Check interval:           15552000 (6 months)
Next check after:         Mon Sep 20 22:01:50 2010
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       4809432
Default directory hash:   half_md4
Directory Hash Seed:      9f97705b-f5ec-4aff-a59c-739643b87f25
Journal backup:           inode blocks
Journal size:             128M


```

---

### Post by srs5694 on 2010-03-25
That all looks perfectly normal to me, although I might be overlooking something. Does the UUID on the fourth line match the one that you'd been using in /etc/fstab and your GRUB configuration?

My best guess at this point is that something has corrupted the first sector or two of your /dev/sda1 partition. These sectors aren't used by ext2fs itself, but they may be interfering with the ability of various tools to properly identify the filesystem. If so, clearing them out may fix the problem, but before you do that, I recommend you examine them and back up whatever's there. Do so like this:

```

sudo dd if=/dev/sda1 of=sda1-two-sectors.img bs=512 count=2

```

Be *very careful* with that command, and particularly with the if= and of= parameters; if you get them wrong you could do serious damage to your filesystem! If you can attach that file to your next reply (click the paperclip icon in the advanced editor; or post it to your personal Web site with a link) I could examine it; or you can install the hexedit package and look at it yourself. On the couple of ext2/3 filesystems I've got handy and booted at the moment, these sectors are entirely 0 values. It's not necessarily an error if they're not, though; GRUB can store part of itself in this space, for instance. (I don't think that should be the case for you, since information you posted earlier indicates that GRUB is installed in your MBR.) You might be able to find a string that would help identify what's in this space, though. That might give a clue about what happened, and if it's something inappropriate (a random raw ASCII file, say), you can be more confident about proceeding with overwriting that space.

Another clue might be obtained with the file command:

```

$ sudo file -s /dev/sda1
/dev/sda1: Linux rev 1.0 ext2 filesystem data

```

That's what I get on one of my systems. If some sort of random file (a JPEG image, say) got dumped there by accident, file might be able to identify it.

If you choose to overwrite those first two sectors, I have two suggestions:


[list]
[*]Install GRUB to that partition by typing "sudo grub-install /dev/sda1". GRUB should remain installed in your MBR, so this shouldn't affect the way your system boots. You'd just be using this to overwrite whatever's in the first couple sectors of /dev/sda1 with something that the various utilities can deal with (namely, GRUB).
[*]You could use dd to blank it out by copying 1024 bytes from /dev/zero, as in "sudo dd if=/dev/zero of=/dev/sda1 bs=512 count=2". Be *very very* careful with this command; a slipup in device specifications, the bs (block size) parameter, or the count parameter could trash your filesystem! When you type it, *pause* before hitting Enter. Review each parameter to be sure it's correct.
[/list]


I advise holding off on doing either of these things unless you see something in the first couple sectors that you can positively identify as inappropriate, though. Overall, I recommend installing GRUB rather than blanking with dd, since you're less likely to make a mistake that will damage the filesystem. If GRUB refuses to install because it doesn't like what it sees, though, dd may be the only choice for repair. (You could leave it as-is or do a backup/erase/restore operation, though.)

---

### Post by Paddy Landau on 2010-03-25
> **sdj said:**
> ... I then replaced the UUID in /etc/fstab with /dev/sda1...
It seems to me that your UUID had changed.

Did you change the partitions in any way at all, perhaps through GParted?

In any event, it seems to be all OK now. Phew!

---

### Post by sdj on 2010-03-25
I don't think the UUID has changed.  Now that I can boot into the system the outputs of 'sudo blkid /dev/sda1' and 'sudo dumpe2fs -h /dev/sda1' match the contents of /etc/fstab and /boot/grub/menu.lst.  The problem seems to be that my system can't identify the UUID of sda1 until it has actually booted off it.

srs5694, thanks for all the suggestions.  I'll have a look at trying this at the weekend.  I was considering re-installing from scratch when 10.04 is released, so as my physical disk seems to be fine if need be I can always persevere with the current setup until then.  If I do go this route are there any particular updates I should watch out for (where the fstab and menu.lst changes I made could cause a problem)?  Would a kernel update cause an issue for instance?

---

### Post by srs5694 on 2010-03-25
A kernel update is likely to automatically rewrite your GRUB configuration, so you may need to go in and change the UUID entries to specify the device filename (/dev/sda1) instead. A kernel update wouldn't ordinarily trigger an /etc/fstab update AFAIK.

If you upgrade to 10.04, only a complete re-install, including creating a new filesystem on the disk, is likely to eliminate the problem. Thus, if you haven't created a separate /home partition, you should back up your home directory's contents and be prepared to restore them after the update. (This is the sort of situation where having a separate /home partition can pay off -- with a separate /home, there's no need to jump through extra hoops to preserve it when you re-install!)

---

### Post by MaxEnt on 2010-03-29
I'm a software developer and I've just experienced the same problem described here.  In my case it was /dev/sda6 which refused to mount during the boot process, which is my /home partition.    This is stable system I've been pounding on daily for a long time, with nothing but the usual updates.  Everything else is working normally.  

After getting over my shock at not rebooting, I was able to do a successful fsck -f on this partition. Nevertheless, mount continued to complain about not finding the UUID for /home.  

I soon figured out to run blkid -p /dev/sda6.  It printed a message with the text "ambivalent result" as you can see from an strace I did later.  

```
write(2, "/dev/sda6: ambivalent result (pr"..., 71) = 71
```I tried to replace the UUID manually, using the value from /etc/fstab: 

```
tune2fs -U "6908d716-5bdf-4dfd-aa78-116d9f5606cd" /dev/sda6
```No joy.  I used tune2fs -l to look at the superblock.  The correct UUID was showing up here, but blkid -p still refused to spit it out.  

I tried booting under the previous kernel.  No difference.  

At this point I changed the mount command to use /dev/sda6 and skip the UUID.  The system then booted fine.  

First I did a backup of /home to a remote system.  Then I ran the 2 minute test using smartctl tools.   No problem detected.  

Finally, I repeated the blkid -p command, and was surprised to discover that it was now successfully reporting the UUID it couldn't find earlier.  Strange.  

I now ran the successful blkid command under strace as well to see what was different.   It was kind of hard to read.  I transformed it with the following process:  

```
wdiff -n failure.txt working.txt | colordiff | ansi2html | Firefox PDF printer
```It looks OK, but something ate the first line.  

My strace command used the -x option and -e read=3 to capture all IO from the affected partition.  I've attached the resulting 80 page document.  Differences are in red/blue.  Process ID differences are not important, of course, but there are also differences in the values read from the key disk areas.  

The search strings [- or {+ will find the reported changes.  

I'm certain I've done nothing unusual to contribute to this problem.  It's possible that the drive is erratic, but unlikely, since I should be seeing bad sector errors, and I'm not.   This is Seagate drive, less than a year old.  

If there's something quirky about blkid in some strange edge case, my strace diff might help to point it out, if anyone wants to go hardcore.  

For now though, I'm just going to keep an eye on this and make more frequent backups, unless someone knows more about this.

---


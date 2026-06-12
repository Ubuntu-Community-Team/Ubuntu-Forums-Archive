---
title: "I'm multi-booting Windows 7, Vista and Ubuntu, but GRUB won't show up"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by jtravisrolko on 2009-07-28
I had Vista and Windows 7 installed, I freed the space for Ubuntu 9.04 - about 35GB - and then booted from the Ubuntu disc. There were no errors on the disc. I selected "use largest amount of contiguous free space", but it only selected 2.5GB instead of the 35GB that were available, so I dragged the little icon back to around 30GB. While installing there was an error - apt configuration failure or something along those lines, but then it said "searching for mirror" and everything was fine afterwards. I restarted and GRUB didn't show up, as it never has (this being the third time I've tried Ubuntu). It went straight to the 'Windows 7 or Windows Vista' screen. 

Here are some things I was previously told would help:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x323d21cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42849408

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20301   163065856    7  HPFS/NTFS
/dev/sdb2           20301       32214    95684952    7  HPFS/NTFS
/dev/sdb3           32215       38913    53809717+   5  Extended
/dev/sdb5           32215       38633    51560586   83  Linux
/dev/sdb6           38634       38913     2249068+  82  Linux swap / Solaris

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8fd4960a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77826   625129472    7  HPFS/NTFS

Disk /dev/sdd: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d9a2e0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       77826   625129472    7  HPFS/NTFS

Disk /dev/sde: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ae1bc51

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       77826   625129472    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

``````
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ cat/boot/grub/menu.lst
bash: cat/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

```EDIT: Here is some more info that may help:

```

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Computing Partition Table of /dev/sdc...
Computing Partition Table of /dev/sdd...
Computing Partition Table of /dev/sde...
Searching sda1 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb3 for information... 
Searching sdb5 for information... 
Searching sdb6 for information... 
Searching sdc1 for information... 
Searching sdd1 for information... 
Searching sde1 for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop
ubuntu@ubuntu:~$ 
```

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x323d21cd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x42849408

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   326,133,759   326,131,712   7 HPFS/NTFS
/dev/sdb2         326,133,760   517,503,663   191,369,904   7 HPFS/NTFS
/dev/sdb3         517,517,910   625,137,344   107,619,435   5 Extended
/dev/sdb5         517,517,973   620,639,144   103,121,172  83 Linux
/dev/sdb6         620,639,208   625,137,344     4,498,137  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8fd4960a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 1,250,260,991 1,250,258,944   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7d9a2e0e

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048 1,250,260,991 1,250,258,944   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ae1bc51

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          2,048 1,250,260,991 1,250,258,944   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9EA69535A6950F41" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb1: UUID="3C5CED555CED0A8A" TYPE="ntfs" 
/dev/sdb2: UUID="34F023B9F023806A" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb5: UUID="4f510f82-5703-4490-b365-5ac6ae27ad40" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="e86d46a0-d765-4fcb-9b4b-afe1100e4178" TYPE="swap" 
/dev/sdc1: UUID="DA7601E37601C0ED" LABEL="New Volume" TYPE="ntfs" 
/dev/sdd1: UUID="B8CC8285CC823D9E" LABEL="New Volume" TYPE="ntfs" 
/dev/sde1: UUID="8604A80D04A801F3" LABEL="New Volume" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sdb5/boot/grub/menu.lst: ===========================

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
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=4f510f82-5703-4490-b365-5ac6ae27ad40 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4f510f82-5703-4490-b365-5ac6ae27ad40

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        4f510f82-5703-4490-b365-5ac6ae27ad40
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4f510f82-5703-4490-b365-5ac6ae27ad40 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        4f510f82-5703-4490-b365-5ac6ae27ad40
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4f510f82-5703-4490-b365-5ac6ae27ad40 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        4f510f82-5703-4490-b365-5ac6ae27ad40
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=4f510f82-5703-4490-b365-5ac6ae27ad40 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=e86d46a0-d765-4fcb-9b4b-afe1100e4178 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/scd1       /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 268.5GB: boot/grub/menu.lst
 268.5GB: boot/grub/stage2
 268.5GB: boot/initrd.img-2.6.28-11-generic
 268.5GB: boot/vmlinuz-2.6.28-11-generic
 268.5GB: initrd.img
 268.5GB: vmlinuz
```

---

### Post by Taylor13 on 2009-07-28
Ok let's see if I got this right. It sounds like you've got windows vista and 7 setup as a dual boot off of one hard drive and when you try to add Ubuntu grub doesn't work. 

However, from the other things you posted I would guess that you have Vista on one hard drive, 7 on a different hard drive and a third hard drive for data (formatted NTFS, windows).  And, at the time you ran those commands, you also had Linux installed to that second (320gig) hard drive. 

I would guess that your system boots from the first (100gig) hard drive by default. I'd also expect that the setup program installed the bootloader to the second drive (320gig) by default (same as install drive). 

This is actually close to how my system is setup. Try using your BIOS setup to boot off of the 320gig drive instead. Otherwise you may need to tell the setup to install the bootloader to the first drive instead. 

Good luck!

---

### Post by jtravisrolko on 2009-07-28
I have them all on one 320gb drive.

---

### Post by Taylor13 on 2009-07-28
Ok, I'm still betting that the boatloader was installed to the other drive in that case. In other words, try booting off of the other hard drive.

---

### Post by jtravisrolko on 2009-07-28
Other drive? I have a few other drives, but they're all nearly full. I don't see why a bootloader would have been installed on one of them. I have a 320gb, three 640gb, and a 1tb. The 320gb is the only one I've used for OS's. The others are for media.

---

### Post by jtravisrolko on 2009-07-28
bump

---

### Post by Taylor13 on 2009-07-28
From what you originally posted it looks like both the 320g and 1t drives are marked bootable. It's quite possible to boot one operating system from a bootloader on a completely different drive depending on which order the drives were recognized in when you did the various installlations.  For example, if you install windows to your "second" drive (which is what your original post indicates) then it's very possible that the windows bootloader could reside on the first drive, since it's normal to boot off of the first drive in the system.  

Something quick to try would be to boot the other drive. If your BIOS currently has the 320g drive listed first for boot then put the 1t one above it or vice versa.

---

### Post by jtravisrolko on 2009-07-28
Thanks very much. That worked, but it took a couple minutes at the "starting up" screen. I'm afraid to change anything else, but could I get a shorter load time if the bootloader was on the same disk as the OS? The 1TB disk is external. Why was the bootloader even put on that disk?

---

### Post by Taylor13 on 2009-07-28
I guess it was put there because it was detected as being the first device (sda) and your other drives were after it (sdb, etc).  Why it detected an external before an internal drive is beyond me.

When you say 'starting up' screen, do you mean the text mode before grub loads or the graphical ubuntu boot screen?

If it's slow before it actually starts booting linux then I would say yes you could possibly speed it up.  If it's slow while it's booting linux then that would be more difficult and could be related to many things.

I'm glad you were able to get it working though.

---

### Post by jtravisrolko on 2009-07-28
It's a text screen after I select Ubuntu in GRUB - a flashing underscore with "starting up" along with some other text I don't remember. The graphical screen doesn't take long at all, but this takes at least a couple minutes. It's at least as bad as Vista.

Wow, this new Linux experience is frustrating. It seemed like 20 minutes before I figured out how to install Firefox 3.5, let alone codecs and other apps like VLC. I'm so used to just clicking an "install" button.

---

### Post by Taylor13 on 2009-07-28
Hmmm...I'm not familiar enough with GRUB to know where exactly that's loading but it shouldn't be that bad. 

As I understand it the boot loader is actually very tiny and has just enough information to load GRUB into memory which is actually stored on a normal partition (usually your Linux partition, in /boot).  I would think that would be the slower part, not loading Linux or the initial ram disk image after GRUB decides what to boot. My own computer only takes a second or two there.

All I can say about the newness is try not to get too frustrated :) .  It can be very different but not usually difficult.  One thing to remember is that in a lot of cases many people will have done exactly what you are trying to do or close, so Google and forums like this one will be your best friend.

---

### Post by ranch hand on 2009-07-29
Boot from your live CD.

Pull up the terminal.
```

sudo grub   (this will bring up a grub promt)

grub> find /boot/grub/stage1   (this will bring up a list in your case it should be a single entry like  (hd0,4))
grub> root (hd0,4)

grub> setup (hd0)

grub> quit

```
Reboot

Assuming that it boots right I would edit the /boot/grub/menu.lst to have a longer time out.  I like enough time to read the thing.  Hitting enter will boot whatever is highlighted right now so I set mine way up ato 100 (I have a bunch of OS').  10 second may be enough for you but I think I would set it at 15 or 20.

---


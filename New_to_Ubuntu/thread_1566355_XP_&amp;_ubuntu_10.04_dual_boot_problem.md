---
title: "XP &amp; ubuntu 10.04 dual boot problem"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by botak8200 on 2010-09-02
hi all,i'm very very new to linux and need help....
currently i'm running on XP dual boot with ubuntu 10.04 on my compaq v3000 series. the problem is i couldn't boot into ubuntu anymore. it all happened when i'm update via update manager. during installation process suddenly my power supply cut off. then i reboot my laptop & it couldn't boot 10.04 anymore (XP just fine). 
after a couple search, i've found [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) & here's the result:


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,811   312,580,095   271,614,285   f W95 Ext d (LBA)
/dev/sda5          40,965,813   102,398,309    61,432,497   e W95 FAT16 (LBA)
/dev/sda6         102,400,000   303,947,775   201,547,776  83 Linux
/dev/sda7         303,949,824   312,580,095     8,630,272  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2: PTTYPE="dos" 
/dev/sda6        680a0bd5-4162-4dd6-a68b-1a5a36221b01   ext4                                     
/dev/sda7        27c20c25-e12c-4414-8835-08786258094a   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

so i really need somebody to guide me (as i'm noob here) to solve my problem as i've got a lot of my stuffs here....

thanks in advance...:p

---

### Post by Nytram on 2010-09-02
You could try running **fsck** from an Ubuntu Live disk, that may repair the problem.

Boot up the Live disk and run the command:

**sudo fsck /dev/sda6**

(Ensure the partition isn't mounted)

---

### Post by botak8200 on 2010-09-02
> **Nytram said:**
> You could try running **fsck** from an Ubuntu Live disk, that may repair the problem.

Boot up the Live disk and run the command:

**sudo fsck /dev/sda6**

(Ensure the partition isn't mounted)

i've tried but here's the result :

ubuntu@ubuntu:~$ sudo fsck /dev/sda6
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda6

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

thanks again....

---

### Post by Nytram on 2010-09-02
You could try this (again from a Live disk):

**sudo fsck -b 32768 /dev/sda6**

If that doesn't work it may be necessary to reinstall Ubuntu, that's what I'd probably do. Unless someone else can suggest a fix.

If you have important data on that partition there are programs available which can attempt to recover it.

---

### Post by botak8200 on 2010-09-02
i'll try later & will update the result.

thanks again...

---

### Post by Rubi1200 on 2010-09-03
For data recovery see here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

As Nytram pointed out, you may have little choice but to reinstall.

---

### Post by botak8200 on 2010-09-03
> **Rubi1200 said:**
> For data recovery see here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

As Nytram pointed out, you may have little choice but to reinstall.


thanks....
looks like i've got no choice but have to reinstall & recover all my data in ubuntu partition...

thanks guys...

---

### Post by soramia on 2010-09-03
hi! maybe it is not the righy forum, but please help me!
i am new linux user, after 20 window's years and it's very difficult for me:

[LIST=1]
[*] i've tried to install skype and it appears the error
[LIST=1]
[*]error: dependency is not satisfiable libasound2
[/LIST]
 
[*]i received the upgrading from 8.04 version to 10.03.1 version. i created the cd and, after restarting the pc....error
[LIST=1]
[*]E: Unable to locate any  package files, perhaps this is not a Debian Disc
[/LIST]
 
[*]i have an external hard disk. i plugged it in the usb port and.... error:
[/LIST]
[INDENT]It's not possible to mount the drive

[/INDENT]I am crazy....i would format everything and reinstall windows...but i want to win!
can you help me?
thank you
rosa:popcorn:):P


P.s. sorry for my english....i am italian!

---


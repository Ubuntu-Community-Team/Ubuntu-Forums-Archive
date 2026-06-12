---
title: "GRUB issue"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by jrb368 on 2009-11-21
I just completed installation of Ubuntu v9.10, partitioning my HD between Windows XP and Ubuntu.  At the conclusion of installation and after restart, I got the following message:

GRUB loading
error: no such disk
grub rescue>

I tried reading through the other threads, but I'm still lost.  I do know Ubuntu is installed on partition sdb5, per a boot info script someone recommended.  Any thoughts?  Thanks!

---

### Post by frenchn00b on 2009-11-21
you have to go to command line into the grub menu at boot

then 

help

root (hd0,  **[COLOR="Red"] press tab[/COLOR]**

to find your disk

here an example of commands:

> root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-25-k7 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-k7
savedefault
boot


beware there is a grub2, the grub team, they changes all their commands, just to f * c k all newbies and make it harder or impossible.
Grub is nice, far nicer than lilo was. I like grub.

---

### Post by kansasnoob on 2009-11-21
> **jrb368 said:**
> I just completed installation of Ubuntu v9.10, partitioning my HD between Windows XP and Ubuntu.  At the conclusion of installation and after restart, I got the following message:

GRUB loading
error: no such disk
grub rescue>

I tried reading through the other threads, but I'm still lost.  I do know Ubuntu is installed on partition sdb5, per a boot info script someone recommended.  Any thoughts?  Thanks!

It would be helpful if you could post the results of the Boot Info Script here.

No guarantees I can help, but maybe.

---

### Post by jrb368 on 2009-11-21
Thanks for the replies/help so far!  I'll try those first few things in the meantime.

Boot script text as follows:

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=63f4160e-cd49-49fa-9670-251f95689489)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.0 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders, total 80043264 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd17cd17c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,108,029    78,107,967   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00059a08

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   557,600,084   557,600,022   7 HPFS/NTFS
/dev/sdb2         557,600,085   976,768,064   419,167,980   5 Extended
/dev/sdb5         557,600,148   970,759,754   413,159,607  83 Linux
/dev/sdb6         970,759,818   976,768,064     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9E74B2B174B28B91" TYPE="ntfs" 
/dev/sdb1: UUID="6CE48678E48643F4" LABEL="FreeAgent Drive" TYPE="ntfs" 
/dev/sdb5: UUID="63f4160e-cd49-49fa-9670-251f95689489" TYPE="ext4" 
/dev/sdb6: UUID="e997b518-c5f0-4063-ae1a-36333a630925" TYPE="swap" 

=============================== "mount" output: ===============================
```

---


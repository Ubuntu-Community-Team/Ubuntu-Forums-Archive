---
title: "Can not recognize sda4 - ??"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by cat2005 on 2009-10-20
Hi,

For some strange reason, my system will not recognize / mount sda4.  sda4 is a partition I created from a prior install.  It worked fine then.  Could you help me?

**1) Here is my:  ls /dev/disk/by-uuid -lah (area of interest in bold)**

lrwxrwxrwx 1 root root  10 2009-10-19 23:23 14e6c3ab-a70a-461e-a35d-92795fabe5a8 -> ../../sda3
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 53cb4452-f63f-4f62-8fbf-aaeeabeb5d19 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 72773812-8d7c-4dc1-8fd0-a54966e49dd9 -> ../../sda2
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 7b1c0cb0-03e3-481d-8248-67c88cbd936e -> ../../sdb3
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 86c77820-6029-4f2a-8a94-09d572e603c6 -> ../../sdb2
**lrwxrwxrwx 1 root root  10 2009-10-19 23:23 90272743-8704-454a-986c-e7cd45dfa8f0 -> ../../sda4**
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 c51e0d86-07ad-4ac7-8f2c-bdf8f1b89e06 -> ../../sdb4
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 d6e3085e-47d6-4226-b317-514d2479873a -> ../../sdb1

**2) Here is my:  sudo mount /media/sda4 (area of interest in bold)**

mythprime@mythcpu:/$ sudo mount /media/sda4
[sudo] password for mythprime: 
**mount: special device /dev/disk/by-uuid/90272743-8704-454a-986c-e7cd45dfa8f does not exist**
[B]
3) Here is my: FSTAB (area of interest in bold)[/B]

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=53cb4452-f63f-4f62-8fbf-aaeeabeb5d19 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=14e6c3ab-a70a-461e-a35d-92795fabe5a8 /home           ext3    relatime        0       2
# swap was on /dev/sda2 during installation
UUID=cf64d36c-05c4-4e69-a01f-5c1818a366d4 none            swap    sw              0       0
**UUID=90272743-8704-454a-986c-e7cd45dfa8f /media/sda4 ext3 sync,noauto,rw,user 0 2**
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

_Did you catch that?_  

My ls (#1) states the device exists.  My sudo (#2) states it does not exist.  My FSTAB states it does exist (sda4 is a manually added FSTAB entry).

Yes, I already created the proper mount point inside /media (/media/sda4).

Totally lost.....

I welcome your input.  Thanks!

/ Mythbuntu 9.04
// Thunar file manager

---

### Post by cat2005 on 2009-10-20
I forgot to add something.  Upon boot / reboot, I get a message like this:

[B]Unable to resolve UUID=90272743-8704-454a-986c-e7cd45dfa8f 
fsck died with exit status 8
Please repair the file system manually[/B]

Could someone explain those messages, or point me to a resource?  I do not understand them.

Thank you again.

---

### Post by mikechant on 2009-10-20
What output do you get from the
```
sudo blkid
```
command?

---

### Post by mcduck on 2009-10-20
> **cat2005 said:**
> Hi,

For some strange reason, my system will not recognize / mount sda4.  sda4 is a partition I created from a prior install.  It worked fine then.  Could you help me?

**1) Here is my:  ls /dev/disk/by-uuid -lah (area of interest in bold)**

lrwxrwxrwx 1 root root  10 2009-10-19 23:23 14e6c3ab-a70a-461e-a35d-92795fabe5a8 -> ../../sda3
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 53cb4452-f63f-4f62-8fbf-aaeeabeb5d19 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 72773812-8d7c-4dc1-8fd0-a54966e49dd9 -> ../../sda2
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 7b1c0cb0-03e3-481d-8248-67c88cbd936e -> ../../sdb3
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 86c77820-6029-4f2a-8a94-09d572e603c6 -> ../../sdb2
**lrwxrwxrwx 1 root root  10 2009-10-19 23:23 90272743-8704-454a-986c-e7cd45dfa8f0 -> ../../sda4**
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 c51e0d86-07ad-4ac7-8f2c-bdf8f1b89e06 -> ../../sdb4
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 d6e3085e-47d6-4226-b317-514d2479873a -> ../../sdb1

**2) Here is my:  sudo mount /media/sda4 (area of interest in bold)**

mythprime@mythcpu:/$ sudo mount /media/sda4
[sudo] password for mythprime: 
**mount: special device /dev/disk/by-uuid/90272743-8704-454a-986c-e7cd45dfa8f does not exist**
[B]
3) Here is my: FSTAB (area of interest in bold)[/B]

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=53cb4452-f63f-4f62-8fbf-aaeeabeb5d19 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=14e6c3ab-a70a-461e-a35d-92795fabe5a8 /home           ext3    relatime        0       2
# swap was on /dev/sda2 during installation
UUID=cf64d36c-05c4-4e69-a01f-5c1818a366d4 none            swap    sw              0       0
**UUID=90272743-8704-454a-986c-e7cd45dfa8f /media/sda4 ext3 sync,noauto,rw,user 0 2**
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

_Did you catch that?_  

My ls (#1) states the device exists.  My sudo (#2) states it does not exist.  My FSTAB states it does exist (sda4 is a manually added FSTAB entry).

Yes, I already created the proper mount point inside /media (/media/sda4).

Totally lost.....

I welcome your input.  Thanks!

/ Mythbuntu 9.04
// Thunar file manager

your fstab entry is missing the last "0" from the UUID. :)

"ls /dev/disk/by-uuid -lah" said the UUID is this:
90272743-8704-454a-986c-e7cd45dfa8f0

..while your fstab has this:
90272743-8704-454a-986c-e7cd45dfa8f

---

### Post by cat2005 on 2009-10-20
> **mcduck said:**
> your fstab entry is missing the last "0" from the UUID. :)
 
"ls /dev/disk/by-uuid -lah" said the UUID is this:
90272743-8704-454a-986c-e7cd45dfa8f0
 
..while your fstab has this:
90272743-8704-454a-986c-e7cd45dfa8f
 
 
D'oh!  I was afraid it would be something so stupid simple as such.
 
Thank you!

---


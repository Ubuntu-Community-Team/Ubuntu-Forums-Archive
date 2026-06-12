---
title: "Mounting an exsisting NTFS raid set"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by aireq on 2009-01-12
Today I got a bad virus on my XP machine so I was forced to wipe the hard drive. Since I've been meaning to try out Ubuntu I figured now was a good time since I have to redo my computer anyway.

I have a 80gb system drive that I installed Ubuntu on. I also have a pair of 150gb SATA drives hooked into a Silicon Image controller. They were setup on XP as a RAID 1 array using NTFS.

I have dmraid installed but I can't for the life of me figure out how to mount the raid drive. Keep in mind I'm totaly brand new to linux/ubuntu.

If I go to places/computer I see two drives for the raid array instead of one. Here's the output from various DMRAID commands

[I]aireq@aireq-desktop:/$ sudo dmraid -ay
RAID set "sil_agbgahcfaicf" already active
RAID set "sil_agbgahcfaicf1" already active

aireq@aireq-desktop:/$ sudo dmraid -s
*** Active Set
name   : sil_agbgahcfaicf
size   : 312579760
stride : 0
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0

aireq@aireq-desktop:/$ sudo dmraid -r
/dev/sdb: sil, "sil_agbgahcfaicf", mirror, ok, 312579760 sectors, data@ 0
/dev/sda: sil, "sil_agbgahcfaicf", mirror, ok, 312579760 sectors, data@ 0

aireq@aireq-desktop:/$ sudo dmraid -b
/dev/sdf:    976773168 total, "WD-WCAPW2588615"
/dev/sdc:    160086528 total, "Y3J9LNBE"
/dev/sdb:    312581808 total, "5LS2AQ17"
/dev/sda:    312581808 total, "5LS0NPKM"

[/I]

So how do I mount this mirrored array? I've seen the "how-to fake raid" tutorial, but a lot of that seems preoccupied with installing Ubuntu on the raid partion. I just want to make to an existing set.


Eric

---

### Post by aireq on 2009-01-12
If I go to /dev/mapper/ I see the following

[I]aireq@aireq-desktop:/$ cd /dev/mapper/
aireq@aireq-desktop:/dev/mapper$ dir
control  sil_agbgahcfaicf  sil_agbgahcfaicf1
[/I]

also here's how I've tried to map it, and the error that I got

[I]aireq@aireq-desktop:/dev/mapper$ sudo mount -t ntfs-3g /dev/mapper/sil_agbgahcfaicf /dev/raid/
NTFS signature is missing.
Failed to mount '/dev/mapper/sil_agbgahcfaicf': Invalid argument
The device '/dev/mapper/sil_agbgahcfaicf' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
[/I]

---

### Post by ronparent on 2009-01-16
I've been dealing with a like problem. Try 'auto' in place of 'ntfs'

---


---
title: "[SOLVED] Oh darn! Now my Windows hard drives won't mount."
date: 2009-01-06
forum: New to Ubuntu
---

### Post by newbpanda on 2009-01-06
I was reading somewhere on a different thread where it was suggested to the poster to download a program to make NTFS hard drives readable because he was having trouble installing WoW in WINE. 

The thing is they were readable in UBUNTU already. One was "DRV2_VOL1" & the other was "67.9GB." How do I tell Ubuntu to ignore the fact they are NTFS & read them again? Everytime I reboot in Ubuntu they are unreadable. :(

---

### Post by Tim Sharitt on 2009-01-06
What exactly did you change that caused the drives to be unreadable? It may also be helpful if you post the contents of /etc/fstab.

---

### Post by newbpanda on 2009-01-06
Oops! I just re-read two possible threads about installing Windows games onto ubuntu...


If I remember correctly the guy was saying he was a guild master so he absolutely needed to use WOW when he was on Ubuntu or else he'd never be able to use the OS. He said something about being "sadface" if he didn't get to do this.

EDIT: Found it! I instructed the terminal to do: sudo apt-get install ntfs-3g. 


I think that's what's wrong. (I'll get on Ubuntu in the morning. I was downloading an NVIDIA driver for a friend's computer & it took twenty mins!) Right now I need to get to bed. :D

---

### Post by newbpanda on 2009-01-07
Here's my /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=7741ff86-687c-4226-96c1-aee409874a87 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=979404d7-db66-455d-ad46-e2b7fb2c9aed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda2       /media/disk     ntfs-3g                 force 0 0
/dev/sdb1       /media/DRV2_VOL1 ntfs-3g                force 0 0

```

Even after editing this and etc/mtab they aren't readable.

When I try clicking the drive from the pull-down menu I'm not allowed to use it.

EDIT: Solved somehow... don't know how, but I fiddled with a bunch of stuff I read & it worked.

---


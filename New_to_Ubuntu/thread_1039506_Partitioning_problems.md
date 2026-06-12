---
title: "Partitioning problems"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by OllieGab on 2009-01-14
I've got openSuse installed on /dev/sda1 and Ubuntu on /dev/sda1. I'm trying to increase the /dev/sda1 slightly as I have some unallocated space on my harddrive.
However, using Gnome partitioning editor, several of the partitions have a padlock symbol next to them - they are obviously locked off for editing.
Question is, how to I get them un-locked, ie how do I get full control over my partitions?
Just to the right of (I'm now obviously talking how it is showing up graphically in the editor!) of /dev/sda1 I have an allocated space and all I would like to do is to increase up to the point where /dev/sda2 starts.

Cheers Ollie

---

### Post by macintosh on 2009-01-14
use could use gparted.

---

### Post by Montblanc_Kupo on 2009-01-14
Could be because you're booted onto the partition? Try using a LiveCD...

---

### Post by Captain_tux on 2009-01-14
If the partitions are currently mounted, you won't be able to do anything with them, no matter what partitioning tool you're using...

---

### Post by alienexplorers on 2009-01-14
boot into the live cd and when it is loaded run:
> sudo gparted
You should then be able to alter your partitions.
Forgive me for my ignorance but how can both be in /dev/sda1:
> I've got openSuse installed on /dev/sda1 and Ubuntu on /dev/sda1

---

### Post by OllieGab on 2009-01-14
> **alienexplorers said:**
> boot into the live cd and when it is loaded run:

You should then be able to alter your partitions.
Forgive me for my ignorance but how can both be in /dev/sda1:

Sorry about that, it's obviously an typo: 1 and 2, respectively!

Yes, using the live CB made a difference. I managed to increase the partition I wanted larger. Thanks for that!
A couple of follow on questions...I've got two swap partitions within /dev/sda2. I assume I don't really need two, or should I, as I've got two distros installed? Or are either distro able to use one swap partition, wherever it is?
(I never run both distros simultaneously). Or do I need two, one in /dev/sda1 and the other in /dev/sda2?

Ollie

---


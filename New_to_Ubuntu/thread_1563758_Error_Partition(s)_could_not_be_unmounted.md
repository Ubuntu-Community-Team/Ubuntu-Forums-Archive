---
title: "Error Partition(s) could not be unmounted"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by Clockwerks on 2010-08-29
Hi, I am another newbie who just got Ubuntu.
When I loaded the live CD onto my laptop, the system worked up until I tried to do a full installation.
During the download process, the error message popped up
partition could not be unmounted for /isodevice
Can somebody give me some advice?
Running a standard Dell Latitude D or C610
Thanks in advance!

---

### Post by TeoBigusGeekus on 2010-08-29
After some googling
> ...ctrl-alt-f1 to go to console and type:
umount -l /isodevice
and then alt-f7 to return to install process...

---

### Post by Mark Phelps on 2010-08-29
> **Clockwerks said:**
> Running a standard Dell Latitude D or C610


Dells are infamous for already having the maximum of 4 partitions assigned.

To ensure that yours is NOT one of those, boot into the LiveCD, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one).

---


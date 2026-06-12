---
title: "Partition in External HD will not automount"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by george.brindeiro on 2010-05-25
Hi everyone!

I have an external hard-drive to which I am backing my regular hard-drive.
First of all, I created partitions in the former of the same size as the partitions in the latter.

Then, I attempted to use dd to copy the contents from one of such partitions to its correspondent partition in the external drive. I was successful in doing so, but the cloned partition maintained the original partition's mounting point ('/') and now it won't automount because the original partition is already mounted.

I do not wish it to mount to '/', rather I would like it to automount to /media/ROOT (ROOT is the label of the cloned partition), just like the other partitions I have (/media/GEORGE and /media/HOME).

How can I change that? I do not want to use fstab.

George

---

### Post by -humanaut- on 2010-05-25
Can you open a terminal and type: cat /etc/fstab

I wanna see where or if you're drive is mounted and then I'll show you how to edit it to auto-mount the drive.

---


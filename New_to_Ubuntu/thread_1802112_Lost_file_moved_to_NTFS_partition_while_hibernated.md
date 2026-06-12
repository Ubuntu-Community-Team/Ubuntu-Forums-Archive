---
title: "Lost file moved to NTFS partition while hibernated"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by bomberb17 on 2011-07-11
Hi, I have 2 partitions, an NTFS with win7 and another with Ubuntu 11. While Windows was hibernated, I booted into Ubuntu and I moved a pdf file from a network drive to a folder in the NTFS partition. (I now have learned that this was a big mistake!) After booting back to Windows, the file is gone! So is there a way to recover that file?
P.S. Undelete software won't work

---

### Post by AlphaLexman on 2011-07-11
> **bomberb17 said:**
> While Windows was hibernated, I booted into Ubuntu
I didn't know that was possible... Wouldn't power-up restore the hibernation ??

Anyway, hibernation should keep a snapshot of your system at suspend time, if you altered the partition, and then un-hibernated, the restoration will revert to the suspend state.

In an extreme situation, you could alter the hibernation file, but just mounting and adding a pdf won't do that.
> **bomberb17 said:**
> After booting back to Windows, the file is gone! So is there a way to recover that file?
P.S. Undelete software won't work
Probably not from the NTFS partition... since you moved the file instead of copying the file, you best bet may be some recovery tools (depending on the partition format) from the original network drive the file was moved from.

---

### Post by bomberb17 on 2011-07-11
Rebooting into windows restored hibernation normally. The problem is that I lost the file. Recovery tools won't work in the NTFS partition (won't find the file). Recovery tools in the network drive mark the file as damaged and unrecoverable.

---

### Post by wildmanne39 on 2011-07-11
Hi, what format is the file saved in? also I copy files I never just move a file from ubuntu to windows it is a risky task.

---

### Post by bomberb17 on 2011-07-12
It was a pdf

---

### Post by wildmanne39 on 2011-07-12
Hi, then the format sure is not the problem.
Since it is on a windows system I am at a loss, you could boot ubuntu then copy the file back into it and see if it is readable that way if it will let you do it with a corrupt file.

---

### Post by bomberb17 on 2011-07-12
I'm sorry I don't understand what you mean.

---

### Post by AlphaLexman on 2011-07-12
> **bomberb17 said:**
> Recovery tools in the network drive mark the file as damaged and unrecoverable.
Regrettably, I'm afraid your .pdf file is gone forever. Make backups, copy instead of move, and learn from your mistake(s).

---


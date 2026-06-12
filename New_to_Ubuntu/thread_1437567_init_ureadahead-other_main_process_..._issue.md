---
title: "init ureadahead-other main process ... issue"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by K.krstnsn on 2010-03-24
Hi 

I JUST installed 9.10. Installed some apps i normally use. I rebooted and now on reboot i get.

fsck from util-linux-ng 2.16
/dev/sda1: clean, 160607/488640 files, 827197/1953897 blocks
fsck from util-linux-ng 2.16
/dev/sda6: recovering journal
/dev/sda6: clean, 1866/9035776 files, 838426/36142225 blocks
init: unreadahead-other main process (455) terminated with status 4

can anyone help please? I'd rather not install as i just set this up as an HTPC. so all the files on USB are indexed which took FOREVER.

---

### Post by Elfy on 2010-03-24
on each boot? 

It looks ok to me - though if you are talking about init: unreadahead-other main process (455) terminated with status 4 that is ok it seems 

> Status 4 (usually ureadahead-other exits with this) means that you had a mountpoint in your fstab that didn't have any files on it needed during boot.

[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

---

### Post by K.krstnsn on 2010-03-24
I figured out what it was. I had a shared folder on a USB drive that was connected.

I disconnected, booted removed the share and now its good.

---

### Post by mastapat11 on 2011-05-12
> **K.krstnsn said:**
> I figured out what it was. I had a shared folder on a USB drive that was connected.

I disconnected, booted removed the share and now its good.

I ran into a similar nonsense too.  but mine was a uuid of a partition that was diff then what fstab had.
booted into a live cd then changed the uuid and this error still shows, but the system boots.

PS.  (rant) Why is it that lucid can't just frickin' skip partitions it can't find during boot that in fstab after a 30-60s timeout??  that so hard?

---


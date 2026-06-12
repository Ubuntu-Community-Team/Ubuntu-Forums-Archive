---
title: "fstab question"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by mesmith on 2009-10-26
I have two hd's.  The first is where my system is located, plus the swap area, mount point /.  In fstab these partitons are shown with with UUID's.  My second hd is a single partition device used for data storage.  It's entry in fstab has no UUID associated with it.  Its mount point is under /media.

Why the difference?  Why isn't a UUID required for the partition on the second drive?

---

### Post by alphaniner on 2009-10-26
A UUID is an alternative to using /dev/sd**.  UUIDs are more robust because /dev/sd** designations can change as devices are added/removed.

As to why they are different, that I don't know.  Ubuntu uses UUIDs by default.  How did the entry for the second HDD get in fstab?

---

### Post by ctc26 on 2009-10-26
At a guess I would say that the UUID is dependent on the filesystem in use on the media. Your first HD is comprised of Ext3/Ext4 partitions. Whilst I'm guessing that your second HD is fat32 or ntfs as it has the /media mount point attached to it.

Also I think the UUID is used to identify partitions at boot time, so it may not be necessary for a partition with the mount point /media to have one.

Hope this helps,

ctc26.

---

### Post by mesmith on 2009-10-26
Well, "it got there" at my hand.  Following instructions on the web for how to install a second drive in linux.  It works fine.  Maybe because the advice was not ubuntu specific it just suggested using the partition name.

Just curious as to why the difference.  I imagine that if I created another partion on my main drive that I could describe it either way, assuming I took care to not tangle the sda1's sda2's, etc.  I can see where UUID's are safer.

---

### Post by mesmith on 2009-10-26
Also, the second drive is formatted as ext3.

---

### Post by alphaniner on 2009-10-27
```
Well, "it got there" at my hand.
```

Well, that's why it's different.  The installer made the entries for the sda partitions, you made the other one.  In a manner of speaking, the installer had better information than you.

Why the difference?  Well, UUID is *relatively* new.  I'm pretty sure it's available to any up-to-date distro, but that doesn't mean every distro is using it.  The tutorial you followed may have been old or out of date.  At first glance, UUID is more complicated than /dev/****.  But it's not all that difficult once you understand it.

/dev/sd** designations were used for a loooong time.  It's not the wrong way to fstab, but it's also not the best way.  Yes, you could use the /dev designation if you created a new partition on sda, but as you said using UUID would be safer.

Hope this helps.

---

### Post by QLee on 2009-10-27
[QUOTE=mesmith]Well, "it got there" at my hand.  Following instructions on the web for how to install a second drive in linux.  It works fine.  Maybe because the advice was not ubuntu specific it just suggested using the partition name.

Just curious as to why the difference.  I imagine that if I created another partion on my main drive that I could describe it either way, assuming I took care to not tangle the sda1's sda2's, etc.  I can see where UUID's are safer.[/QUOTE]

Yes, you can choose UUID or device node or even LABEL for mounting in GRUB or fstab or even on the command line. Personally, I give my partitions a label and mount that way because I can more easily remember a label I gave than a long assigned UUID. All ways work if we use them correctly, we have the choice. You may have read an old document, mounting by device node was previously the standard.

---

### Post by mesmith on 2009-10-27
Many thanks to all who responded.  I now understand.

---


---
title: "Why clean install?"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by HungryOcopus on 2009-10-29
Maybe it's a simple question, but in a lot of the threads where people mention 9.10 it seems like the majority of people suggest clean installing over upgrading through the manager. To me it seems much more logical to upgrade (don't necessarily need to back up data, my default settings and my appearance preferences will stay - i think...).
And it seems like ubuntu does a decent job of clearing out old packages and such, so I can't imagine it's that much of an improvement performance wise.

Can anyone tell me the benefits of clean installing over upgrading? Thanks.

---

### Post by OffAxis on 2009-10-29
The two things that come to mind that a clean install is supposed to provide are the best performance for ext4, and it'll install grub2. 
If you upgrade you're left with ext3 and grub legacy.

---

### Post by philinux on 2009-10-29
> **HungryOcopus said:**
> Maybe it's a simple question, but in a lot of the threads where people mention 9.10 it seems like the majority of people suggest clean installing over upgrading through the manager. To me it seems much more logical to upgrade (don't necessarily need to back up data, my default settings and my appearance preferences will stay - i think...).
And it seems like ubuntu does a decent job of clearing out old packages and such, so I can't imagine it's that much of an improvement performance wise.

Can anyone tell me the benefits of clean installing over upgrading? Thanks.

In this instance there are two. Ext4 and grub2.

Make sure you read the full release notes.
[http://www.ubuntu.com/getubuntu/releasenotes/910overview#ext4%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/910overview#ext4%20by%20default)

---

### Post by bigspottycat on 2009-10-29
I always prefer to clean install now, having had problems with difficult upgrades in the past.

If you keep all your data in a separate 'home' partition (which also happens to include setting for appearance etc) on the hard drive, you can just install the new release over the previous one (in a separate partition), without having to worry about losing any data (although data backup is still a good idea!).

This also means that you can try different distros, each in it's own partition, without having to worry about your data, which is safely stored in it's own partition.

---

### Post by Hospadar on 2009-10-29
+1 for separate home partition.
It makes it super easy to do a clean install every new version where all my personal data remains, and all I need to do is add a few programs from apt-get (or synaptic if you prefer) which takes no time at all.

Here's a pretty good writeup on different partitioning schemes if you aren't familiar:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by servicetech on 2009-10-29
I too am interested in doing the separate home partition, makes it super easy to upgrade every 6 months.

Is there an easy way to do this that doesn't involve a lot of terminal commands?

---

### Post by KIAaze on 2009-10-29
> **servicetech said:**
> I too am interested in doing the separate home partition, makes it super easy to upgrade every 6 months.

Is there an easy way to do this that doesn't involve a lot of terminal commands?

Use GParted. (Or QtParted if you prefer Qt/KDE)
GParted should be available on the Live-CD.

---


---
title: "External HDD Help"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by MattyG on 2009-01-04
Ok, Now what I did is I have an external Hard Drive that is formatted to Linux.But I would like to format it back to Windows so I can partion it for both. But when I try and Run the Windows Vista disk it says I don't have the proper boot files. And when I'm running windows I can't see or access the External drive at all. So what I need help with is finding the windows boot record to put onto the drive and also need to know the best way to do that. Thanks in advance for any help.

---

### Post by taurus on 2009-01-04
Use gparted (install it if you don't have it in System -> Administration) and reformat it to ntfs.

---

### Post by sadaruwan12 on 2009-01-04
> **taurus said:**
> Use gparted (install it if you don't have it in System -> Administration) and reformat it to ntfs.
Yes, go back to Linux use gParted and remove all the linux partiotions you've and then try it with your Vista.I think this should work.

---

### Post by -kg- on 2009-01-04
> **MattyG said:**
> Ok, Now what I did is I have an external Hard Drive that is formatted to Linux.But I would like to format it back to Windows so I can partion it for both. But when I try and Run the Windows Vista disk it says I don't have the proper boot files. And when I'm running windows I can't see or access the External drive at all. So what I need help with is finding the windows boot record to put onto the drive and also need to know the best way to do that. Thanks in advance for any help.

> Use gparted (install it if you don't have it in System -> Administration) and reformat it to ntfs. 

Or as long as you're about it (and if you have both Vista and Ubuntu installed on another hard drive), while you have GPartEd running (either from your installation or from the Live CD) instead of reformatting the external drive to ntfs, just shrink that partition to whatever you desire, then create a new partition and format *that* to ntfs.

That way, you accomplish everything you want to do in one GPartEd session.

See ["How To Partition"]("https://help.ubuntu.com/community/HowtoPartition") for further information on doing this.

---

### Post by MattyG on 2009-01-15
Ok, I went on my ubuntu and I can see the drive now but I cant even edit it from there. But now when I try and boot that drive it dosent work at all.

---


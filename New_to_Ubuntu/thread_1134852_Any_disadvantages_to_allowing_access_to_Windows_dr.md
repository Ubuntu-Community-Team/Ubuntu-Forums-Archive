---
title: "Any disadvantages to allowing access to Windows drive?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by verdigris on 2009-04-24
I hope this is the right place for this post, otherwise, my excuses to the mods :-?

I'm dualbooting, and don't really need read/write access to my Windows C: drive because my main storage/working area is in a different partition (also NTFS). 

However, I would like to share Firefox profiles, which would require read/write access to the C: drive. Are there any disadvantages to this (especially security)?

Thanks!

---

### Post by kanikilu on 2009-04-24
I don't really see how it could be a security problem. The only thing that I would be slightly concerned about is somehow corrupting data by writing to an NTFS partition - but that was several years ago when write support to NTFS was experimental, these days I think it's probably pretty stable.

I occasionally write to NTFS, and don't have any problems, but mainly I just need to read, not write.

These days I'm working more and more with native linux filesystems and HFS+ for Mac OS X (still waiting on write support to journaled HFS+ partitions! ;) )

---

### Post by jowilkin on 2009-04-24
Foxmarks (now called xmarks) should give you most of the functionality of a shared profile.  I use it to sync several computers: [http://www.foxmarks.com/](http://www.foxmarks.com/)

But allowing access to a windows drive does not really have disadvantages.  Only issue I've ever run across is if the drive needs to be checked (like when computer is shutdown improperly) only Windows knows how to do the check to get the drive working again.  So you need to boot into Windows whenever this happens to get things working again in Linux.  A minor annoyance really...

---

### Post by verdigris on 2009-04-24
Hi kanikilu, jowilkin,
Thanks for the replies! I was most worried that while trojans/worms I may get while browsing on the Linux platform would find its way to the C: drive, but that sounds like it won't happen. I think sharing profiles would be more useful to me than xmarks because I'd also like to keep some extensions/add-ons in sync.
Cheers!

---

### Post by SentientFluid on 2009-04-24
Firefox also allows you to tell it where to look for the profiles.  When I dual-booted I moved it to a shared partition and told Firefox in both XP and Ubuntu to use the same profile.  No need to worry about syncing and you won't need to access your Windows system partition.

I can explain how to do it when I get home from work if you need.

---

### Post by verdigris on 2009-04-24
Thanks SentientFluid, I'll try it out first and if I need any help, I'll post here! =D

---

### Post by tommynz1975 on 2009-04-24
yes please SentientFluid I would like your tip to share a profile / bookmarks

---

### Post by SentientFluid on 2009-04-26
For basic instructions see here:

[http://ubuntuforums.org/showthread.php?p=7152267](http://ubuntuforums.org/showthread.php?p=7152267)

Comment in there with any questions on how to share profiles between operating systems.

---


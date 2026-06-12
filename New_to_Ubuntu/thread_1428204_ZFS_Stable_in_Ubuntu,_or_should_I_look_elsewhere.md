---
title: "ZFS: Stable in Ubuntu, or should I look elsewhere?"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by busydoingnothing on 2010-03-12
After finding out that my hardware RAID card doesn't like my drives, it looks like I'll be going software RAID. From what I've read, ZFS with a RAID-Z is the way to go. Is the ZFS-FUSE solution for Ubuntu solid/stable enough, or should I just go with an OS where it is natively supported?

---

### Post by srs5694 on 2010-03-12
Why do you need ZFS, and on what filesystems would you use it? I certainly wouldn't recommend using ZFS as the filesystem for Linux as a whole, although it might be OK if you needed it for certain specific and limited things. As a general rule, FUSE-based filesystems are likely to be slower and less reliable than native Linux filesystems. I don't know how reliable or speedy ZFS on FUSE in particular is, though.

If you're mainly interested in RAID features, then using Linux's software RAID in conjunction with a Linux kernel-based filesystem, such as ext4fs or XFS, may do all you need.

If you need ZFS features such as copy-on-write or snapshots, you might want to look into Btrfs, which is Linux's native filesystem that supports ZFS-like features. Btrfs is still considered experimental, though, so you should restrict its use to just those directories/partitions on which you really need it.

---

### Post by busydoingnothing on 2010-03-12
I have 2x 500GB drives that I want to use in a RAID-1 (for important data, which I will backup weekly to an external drive), and I have 3x 1TB drives that I want to use in a RAID-5 for other data (video, audio, other storage). RAID-Z seems to be touted as a better solution to RAID-5, so that's why I was looking into it.

---

### Post by srs5694 on 2010-03-12
Define "better." What's better for one use or application may not be better for another one. For instance, RAID-1 is better for reliability than using no RAID, but software-based RAID-1 also usually entails a performance hit. Is RAID-1 "better" than not using RAID? That depends on your specific needs, and also on the RAID-1 implementation.

That said, my knowledge of RAID-Z is limited, so I may not be able to offer more guidance on it specifically. I can be certain that you won't get useful advice unless you lay out your specific needs, though. How will you be using this computer? (Server, HTPC, desktop, etc.?) How important is access speed to you? How important is reliability to you? Do you need specific ZFS features? (If so, which ones and for what?) How will data on the RAID partitions/drives be accessed? (By local programs demanding rapid access, by remote systems accessing small files, etc.?) Any advice you get before providing these details, and perhaps others, is suspect at best, since the answers to these questions dictate the answer to the overall question of what type of storage solution best fits you needs.

---

### Post by denver on 2010-03-12
As a "native" alternative, i would recommend btrfs. It is already included in the default kernel, and as of 10.04, most critical features are implemented.

However, its still under heavy development at the moment.

I have been testing it with great results on a few VPS's. It can even be used as a multi disk silesystem, similar to RAID. At the moment it suports RAID0, RAID1 and RAID10.

Have a look at it.

---

### Post by busydoingnothing on 2010-03-12
Here's my original thread about what this home server is supposed to accomplish: [http://ubuntuforums.org/showthread.php?t=1389148](http://ubuntuforums.org/showthread.php?t=1389148)

Essentially I want to use the 2x 500GB to backup all data from machines on the network (namely, my desktop and my girlfriend's laptop). 

The 3x 1TB drives are used for storage. I want to host all of our media to share among all the machines (above-mentioned plus an XBOX 360 and HTPC). I also record music and shoot films, so I'll be storing all of that data there unless I'm actively working on it, in which case it would be stored on my desktop. I'd like to use the server to encode video when needed, which will mostly be an overnight process.

All in all, performance isn't necessarily my greatest concern. Just about all of my needs are low-performance except the video encoding. Reliability is more of a concern. 

Re: RAID-5 versus RAID-Z, the explanation on Wikipedia seems to convey the benefit of Z over 5: [http://en.wikipedia.org/wiki/Non-standard_RAID_levels#RAID-Z](http://en.wikipedia.org/wiki/Non-standard_RAID_levels#RAID-Z)

As far as hardware goes, I'm going to purchase a new mobo/cpu/ram/video combo most likely next week. I wanted to recycle old hardware for this project, but it seems that onboard SATA is going to be better than a PCI SATA controller, and a newer CPU will definitely be better for encoding video.

---

### Post by srs5694 on 2010-03-12
Nothing you mentioned requires ZFS or Btrfs features, as far as I can tell. I'd say that in Linux, you're best off using XFS, or possibly JFS, since they work well with the sorts of large files that video editing software produces. (Ext4fs also does well with this, but online reports suggest it's a little bit less robust.) The Wikipedia description of RAID-Z makes it sound like it's got some technically nifty additions, but I doubt if they'd have really significant performance implications for you. (As I said, though, I'm not a RAID-Z expert, so I could well be wrong about that.)

Overall, I'd suggest going with RAID-1, RAID-5, or a combination of those, using XFS on the big backup and video-editing partitions and ext3fs or ReiserFS on the main Linux system partitions.

---

### Post by barret1 on 2010-04-08
> **srs5694 said:**
> Nothing you mentioned requires ZFS or Btrfs features, as far as I can tell...

I'm in the same boat as the OP, looking to raid-z as a good software raid solution. RAID-Z offers a lot of advantages when it comes to data integrity, using checksums to detect "soft errors", in addition to many other features. Even though I don't NEED a lot of the features of zfs, the fact that the file system is designed from the beginning to ensure data integrity makes it enticing, as compared to traditional file systems.

Anyway, I was going to go with OpenSolaris for my file server...but the recent acquisition of Sun by Oracle has put the future of that OS in doubt. So I am considering going with a BSD variant, or ubuntu. I'd prefer ubuntu since I am a linux person.

So I am wondering if anyone knows the answer to the original question: Is ZFS-FUSE stable enough for "production use" on raw disks (not partitions)?

---

### Post by ratcheer on 2010-04-08
To the OP, ZFS is major overkill for what you are trying to do. ZFS is mainly used for enterprise systems consisting of hundreds of disk drives, or, at any rate, a lot more than 5 drives. RAID-5 is not really suitable for a 3-disk array, either.

I would recommend either a 3-disk RAID-0 array (and a good backup strategy), or adding a fourth disk and making it RAID 1+0 (aka RAID-10).

Tim

---


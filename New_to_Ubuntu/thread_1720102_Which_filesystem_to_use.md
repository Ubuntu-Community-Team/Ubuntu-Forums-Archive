---
title: "Which filesystem to use"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by MarkTrent on 2011-04-02
I've spent the last week trying things out and I'm at my wit's end (Since it takes 4 hours to perform the transfer each time), it seems I'll be installing Windows again tomorrow.

I've got a 2TB hard drive, I want to get the most storage from it as possible under Linux but with a good transfer speed. So far my results have been: (when formatting the drive, and then copying 1.3TB of 700mb files to it)


Filesystem:::::GB left

NTFS:::::583
ext2:::::554
ext4 (with journal removed and reserved space set to 0%):::::549
xfs:::::579
jfs (with log size set to 1mb) :::::578

so results are:

ext2: **29gb** available less than NTFS
ext4 (without journal or system reserved blocks): **34gb** available less than NTFS
xfs: **6gb** available less than NTFS
jfs: **5gb** available less than NTFS

...from 1.3tb of data copied to the drive, so more will be lost once I've filled the entire disk of 1.82TB.


I would use NTFS for my drive, but it only gives 15mb/s transfer speed compared to 80-115 for the other filesystems.

What filesystem am I supposed to use on Linux which gives me the same storage capacity of NTFS but a better transfer speed under Linux??? There must be one surely!


Note - Please don't tell me to run these commands:

tune2fs -O ^has_journal /dev/****
tune2fs -m 0 /dev/****

Read my post, I've already run these.

---

### Post by mads65 on 2011-04-02
OK, I asked this question to myself:

If I had a 200 GB drive, would I go for speed and convenience if I had to loose 3.4 GB disk space?

The answer was YES, so I recommend EXT4 file system.

---

### Post by MarkTrent on 2011-04-02
> **mads65 said:**
> OK, I asked this question to myself:

If I had a 200 GB drive, would I go for speed and convenience if I had to loose 3.4 GB disk space?

The answer was YES, so I recommend EXT4 file system.

Multiply it by the 5x 2TB hard drives I have and that's 170GB... It's a lot of space to lose when NTFS manages not to somehow.


I asked this question to myself:

If I can get fast write speeds and the best storage efficiency using Windows, why should I use Linux?

The answer was, I have no idea.

---

### Post by GWBouge on 2011-04-02
> **MarkTrent said:**
> If I can get fast write speeds and the best storage efficiency using Windows, why should I use Linux?

... for any of the other countless reasons people opt to use Linux?  I'm no file system expert, but I will say that I get similar (although not quite as fast) writes to my eSATA 2TB NTFS drive as I do with it in ext4, so I'm not sure why you would experience such a drastic decrease in speed.  Granted, the ONLY reason it's in NTFS format is because I dual-boot, and I'd like to have access to it on the Windows side, or if I take it with me to a friend's Windows PC.

I'm not trying to be a <insert remark here>, but use the best tool for the job at hand.  If that extra 1.5% of storage space is worth whatever reasons you tried out Linux ... well, that's a choice.

---

### Post by jtarin on 2011-04-02
I don't see[ ZFS ]("http://zfsonlinux.org/")listed?

---

### Post by Rubi1200 on 2011-04-03
Although it is apparently not 100% stable yet, Btrfs may be worth looking at:
[http://en.wikipedia.org/wiki/Btrfs](http://en.wikipedia.org/wiki/Btrfs)

---


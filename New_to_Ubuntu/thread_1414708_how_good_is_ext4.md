---
title: "how good is ext4"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by degarb on 2010-02-23
Is ubuntu or ext 4 good at tolerating bad sectors on a cd?  I know in spinrite it can identify these so they aren't written on.   

So, what kind of issues might I have with a drive with many bad sectors?  (data ext usb drive and for vdi vm.

---

### Post by warp99 on 2010-02-23
> **degarb said:**
> Is ubuntu or ext 4 good at tolerating bad sectors on a cd?  I know in spinrite it can identify these so they aren't written on.   

So, what kind of issues might I have with a drive with many bad sectors?  (data ext usb drive and for vdi vm.

Ext4 isn't used for CD's since they use a completely different file structure (Joliet is an example). As for personal experience Ext4 seems no more or less fault tolerate than Ext3. Now at one time there was a corruption issue with Ext4 but AFAIK this has been mitigated. 

Recently Google stated that they were going to move all of their servers from Ext2 to Ext4. So if it's good enough for Google, well ... ;)

---

### Post by sgosnell on 2010-02-24
Yes, the filesystem on your HDD has nothing to do with CDs.  The overlying OS or the package used to burn the CD has something to do with it, but not ext4 or any other filesystem you may be using.

---

### Post by degarb on 2010-02-24
Was late. I meant hd, not cd.  I got a cheap used HD and has many bad sectors.  I was wondering if linux can just work around the bad areas.

---

### Post by ibuclaw on 2010-02-24
> **degarb said:**
> Was late. I meant hd, not cd.  I got a cheap used HD and has many bad sectors.  I was wondering if linux can just work around the bad areas.

All operating systems are capable of working around the bad areas, but if your hard disk drive is starting to continually report bad sectors / blocks, then I'd advise just to get a new one, as it may only cause pain and data loss in the future.

Regards
Iain

---

### Post by doas777 on 2010-02-24
> **ibuclaw said:**
> All operating systems are capable of working around the bad areas, but if your hard disk drive is starting to continually report bad sectors / blocks, then I'd advise just to get a new one, as it may only cause pain and data loss in the future.

Regards
Iain

it's my understanding that bad blocks are remapped via the hard disks firmware and controler board. I saw an interesting misuse of the badblocks command the other day that could brick your drive as a result.

ext4 seems pretty good. it can do a diskscan on a 1tb volume in about 30 seconds, versus the 40 minutes or so that ext3 took. now i can have my server back up after powerfail inside of 3 minutes, instead of waiting hours.

---

### Post by mcduck on 2010-02-24
> **degarb said:**
> Was late. I meant hd, not cd.  I got a cheap used HD and has many bad sectors.  I was wondering if linux can just work around the bad areas.

The "badblocks" (and "fsck") command will allow you to search, mark & disable bad sectors on a hard drive, but I really wouldn't bother. When a hard drive starts to gain bad sectors it's getting way too close to it's end of life, you definitely don't want to store anything even remotely important on such drive.

If the drive already has many bad sectors it will gain more of them at rapidly increasing speed. You'd better just throw the drive away and get a new one. 

edit: like doas777 said, modern hard drives also automatically remap bad sectors for you, so they will only start to appear to you/your system at the point when the disk itself has so many bad sectors that the drive's firmware isn't able to map them away any longer.

---

### Post by ibuclaw on 2010-02-24
> **doas777 said:**
> it's my understanding that bad blocks are remapped via the hard disks firmware and controler board. I saw an interesting misuse of the badblocks command the other day that could brick your drive as a result.


It is to my understanding that you should **never** use badblocks manually, for reasons you just said. :)

On the other hand, I have used it for setting up a disk for encryption once.

Regards
Iain

---

### Post by mcduck on 2010-02-24
> **ibuclaw said:**
> It is to my understanding that you should **never** use badblocks manually, for reasons you just said. :)

On the other hand, I have used it for setting up a disk for encryption once.

Regards
Iain

Agreed. Actually even the badblocks manual recommends that it should only be used through other disk tools (like fsck).

Personally I recommend just getting rid of disks that have bad blocks. Drive that is going to fail any day isn't really usable even for testing purposes.

---

### Post by degarb on 2010-02-24
> **mcduck said:**
> Agreed. Actually even the badblocks manual recommends that it should only be used through other disk tools (like fsck).

Personally I recommend just getting rid of disks that have bad blocks. Drive that is going to fail any day isn't really usable even for testing purposes.


You guys are no fun.:D  I guess I am going to take legal action to get my $10 back.  Now, off to find a cheap lawyer....

---

### Post by The Cog on 2010-02-24
With regard to ext4, I advise against it. Every PC I have installed on ext4 (seven installs, three different PCs) has died with horrible filestem corruption. They took between 1 hour and 10 weeks for it to happen, but they all died in the end.

I don'y know if it's ext4, or Ubuntu's specific version - four were Jaunty, 3 were Karmic.

When Lucid comes out, I think I might try BTRFS. ext4 has taught me the value of frequent backups, so I don't have a lot to lose.

---

### Post by bodhi.zazen on 2010-02-24
> **The Cog said:**
> With regard to ext4, I advise against it. Every PC I have installed on ext4 (seven installs, three different PCs) has died with horrible filestem corruption. They took between 1 hour and 10 weeks for it to happen, but they all died in the end.

I don'y know if it's ext4, or Ubuntu's specific version - four were Jaunty, 3 were Karmic.

When Lucid comes out, I think I might try BTRFS. ext4 has taught me the value of frequent backups, so I don't have a lot to lose.

I had a single problem with ext4 , other then that I have been using it for a while, both in Fedora and Ubuntu.

ext4 is faster and outperforms ext3 , and is noticeable on under powered computers such as netbooks.

btrfs seems interesting, and I am looking forward to taking it for a spin, but, IMO, ext4 is more "stable" then btrfs, so hard to advise btrfs over ext4.

---

### Post by sgosnell on 2010-02-24
I've also been using ext4 since it first was available, in the alpha or beta stage of Jaunty, IIRC, with zero problems.  I like it.

---

### Post by The Cog on 2010-02-25
Hmm. 

I wonder if it's something to do with the way I install. I always have Ubuntu in a logical partition, and always do a fresh install. I manually choose the partition to install to. Once I'm happy that the new system feels stable, I edit fstab and add my /home partition, which brings in all my documents and application settings.

---

### Post by PRC09 on 2010-02-25
Been using since it was first available as well and not a single problem yet.........

---

### Post by sgosnell on 2010-02-25
Why do you put the OS in a logical partition?  Not necessarily criticizing, but I'm curious as to why you would go to that trouble.  I've always put it in a primary partition, not trusting nesting that much.

---

### Post by bodhi.zazen on 2010-02-25
> **sgosnell said:**
> Why do you put the OS in a logical partition?  Not necessarily criticizing, but I'm curious as to why you would go to that trouble.  I've always put it in a primary partition, not trusting nesting that much.

Logical partitions work fine for most any modern OS. People do this when they want more then 4 primary partitions, and because Windows usually already has 2 primary partitions (Windows + a recovery partition) if you boot more then one version of Linux you will need to use logical partitions.

Personally I have used logical partitions for years, so I doubt the problem is with logical partitions.

---

### Post by sgosnell on 2010-02-25
OK, like I said, I was curious.  I never had more than one partition for Windows, and if I boot another Linux distro I do it from an SDHC or USB drive.  On the one computer I still have Windows on, it's on a separate HDD.  I just never got into dual-booting, and haven't used any Windows version since XP.  I don't see why using a logical partition would be a problem, just wondered why anyone would go to the trouble.  Your explanation makes sense, I guess.

---


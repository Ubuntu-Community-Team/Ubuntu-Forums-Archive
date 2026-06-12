---
title: "[SOLVED] Which RAID"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by burnetbj on 2008-12-02
OK here goes

System will be as follows

Ubuntu 8.10 
Asus AN32-SLI Deluxe
AMD Opteron 165
nVidia 7800gt 256
Corsair 2x512 = 1Gb 
Corsair 750w PSU
Have upto 4 500Gb WD 16M cache SATA
and 1 250Gb WD 16M cache SATA

I currently have 1 of the 500Gb drives with 7.04 on it and the 250Gb with all important data on it 

What I would like to do is put all the important data on the 250Gb freeing up the 500Gb drive so I have up to 4 free 500's 

I want to put 8.10 on the system with a RAID setup so I dont have to worry about losing data anymore. I purchase more HDD's thinking I would want a better RAID but after reading looks like RAID 1 with 2 500Gb hdd would be the best for me as seems most people dont like the others for some reason or another

I just want to make this as redundant as possible and painless as possible as I am still a struggling user

Would it be better to free up the 250 for the system and then RAID 1 with 2 500's for media or would it be easier to do system and RAID all as one 

Please remember I am still very Rooky at best please speak human :)

Thanks for any help

---

### Post by jbrown96 on 2008-12-02
I think that a lot of people are confused about RAID. It is a redundancy system, not a backup solution. Think of it in terms of corporation. They use RAID and have backups. The purpose of RAID is so that if a drive goes bad, their server can continue to operate until a new drive can be loaded (and the array rebuilt). They also use off-site backups, so that a catasophe at the office will not take down all their data. Unless you need to have access to that data at all times, and cannot handle any interruption, I wouldn't use RAID. It adds a lot of complexity, especially if you don't know what you're doing. Hardware RAID is easier, but then you're looking about US$130 for a card. 

Here's what I do, and I like to think that I'm very serious about backups. 
I have a 1TB drive in my HTPC (encrypted). I have 2 1TB drives (also encrypted) that I use for backup. They are kept in a safety deposit box. On Thursday, I retrieve one of them, and use rsync to make a backup. On Friday, I return the drive. The next week I use the other drive. This way a drive is always kept safe at the bank, and that data is only a week old.  
The failure scenarios boil down to two situations: drive failure and catasrophe.
A drive failure means that there is a problem that only affects a single drive. However, they could all have drive failures at the same time. Really bad luck but it can happen, and there's nothing you can do (the more backups/redundant disks the less likely).
A catasrophe is where something happens to the environment that the drives are in (i.e. fire, flood, stolen, etc.). This is where my system shines, and why corporations use off-site backup. A catasrophe doesn't matter unless it can take out a bank and my house. 

RAID will protect against drive failures, but it also introduces another failure point: the RAID card. I've never used one, but I have heard that if the card goes, the array might not be salvageable. 

Here are my reasons to go for backup instead of RAID:
1) easy. no configuration. You can make it as complicated as you want (cron jobs that use rsync) or just drag and drop folders in the file browser. 
2) Cheaper. No RAID card.
3) Safer. How important is your data. Mine is probably worth more than anything else I own. There's nothing like off-site backup, or at least disconnected from the computer (small fireproof safes are only about US$25).

If you do decide to go with RAID, the more drives the better. RAID 5 is the way to go. I would look at using all 4 drives in RAID 5.

---

### Post by nhasian on 2008-12-03
you should consider using your single 250 gig drive as your boot drive, then all four other drives in a raid5 array for your /home directory.

---

### Post by linux_tech on 2008-12-03
The advantage to RAID is better performance in disk access and 
fault tolerance. If one drive goes out then you can replace the drive 
and repair the array so you do not lose any data.  RAID is good but if you really value your data I would still backup to either a server that is offsite or a tape that can be stored offsite. RAID 5 stripe with parity
can be done with as little as 3 drives.

---

### Post by hyper_ch on 2008-12-03
As said, RAID is no true backup solution. It just keeps the whole thing operational if one drive goes bad... however if you delete a file from the raid it will be gone on all raid devices.

As for backup, I have a small server at my parents home (fully encrypted of course) into which I nightly rsync the important data).

---

### Post by Kellemora on 2008-12-03
I'll chime in too AGAINST RAID!

For many it's quite complex and gives a false sense of security!

If your controller fails, you've lost everything, because the odds of finding an identical controller in a year or two is slim to none.

And RAID is technically obsolete already and will be within a couple of years.

The only purpose of RAID is to keep your file server up and running through a drive failure, nothing more.  You still have to back-up your data, preferably off-site.

You gain no extra space with Raid unless you go to full Raid arrays like Raid 5, 10 or 50.  Although they do run faster seek times too.

I use mirroring so that what is on one drive is backed up to a second drive and the second drive is backed up off-site.  And the mirrored drive is bootable, so if sda fails, I can drop sdb in it's place and be back up and running in minutes.  As far as I'm concerned, that's the only way to go!

TTUL
Gary

---

### Post by hyper_ch on 2008-12-04
kellemora:I think he means software raid.

---

### Post by kernelhaxor on 2008-12-04
A wonderful howto which explains 'fake' raid on most motherboards and how to do RAID with software .. might help: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---


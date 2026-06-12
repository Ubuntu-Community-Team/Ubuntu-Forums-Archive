---
title: "Disk has a few bad sectors Ubuntu 10.10 Help!!!!"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by gaurish108 on 2011-02-10
Hello,

I just freshly installed Ubuntu 10.10 and I under Administrations-->Disk Utility I get a message saying that my
disk has a few bad sectors. 

 Before this I was using Ubuntu 10.04 and there was no problem.  I removed Ubuntu 10.04 by deleting the partition and then installed Ubuntu 10.10. 

Is this a cause for concern?  Is it possible that it was deleting the partition that caused the problems? Do you think I should have formatted it first?

---

### Post by srs5694 on 2011-02-10
Yes, it is cause for concern. No, deleting the partition could not have caused the problem. If this report is accurate, it indicates that the disk may be starting to fail. We're talking about a physical failure here; it could not have been caused by normal partitioning operations. The disk could continue to work fine for months or it could fail rapidly tomorrow.

I recommend you first obtain more information. Utilities like GSmartControl (it's in the repositories) will produce a more detailed report, or maybe you can get one by clicking or double-clicking the "SMART status" line in Disk Utility. (I'm not that familiar with Disk Utility, so I don't know what it can produce.) You could also check Hitachi's Web site; they may have a tool you can run to check the disk, either from Windows (if you dual-boot) or as a stand-alone boot disk.

If the SMART status indicates that you've got any bad sectors, then at the very least you should keep good backups and watch it carefully. Given the low price of hard disks today, I'd just replace any drive that even might be beginning to fail; IMHO, it's not worth the risk on any computer that houses data you care about.

---

### Post by robsoles on 2011-02-10
Installing an operating system will no more give a hard drive bad sectors than just using the hard drive in general will. Deleting partitions etc may lead to bad allocation tables but it won't make bad sectors by itself - wear and tear of continuously reading and **writing** is the common culprit, shocks/acts-of-violence are the least common and in the middle would be electrical problems; like static, surges and brownouts.

I speak only from my experiences and claim no particular expertise.

Did you really check the hard disk for bad sectors just before installing 10.10, using the 10.04 'Disk Utility'?

Hard drive management software is usually written to 'rule out' bad sectors "quietly/silently" up to a certain tipping point at which the user is alerted that the drive is reaching the end of it's usable life.

The one drive I've had die on me whilst using Ubuntu was flagged by a warning a "really good warning message" about two weeks before it finally carked it - the couple of drives that have died on me in Windows managed it with no more warning than scandisk being called on a few startups before the data on the drives was much less likely to be recovered.


Is the disk utility there offering you to view 'SMART data' for this drive? Well worth a peek if it is capable.

---

### Post by gaurish108 on 2011-02-10
Thank you for that information. On viewing the SMART data I have attached what I got underneath. 

The RED area is the bad sector warning. Hope this data might indicate something. I will also run the Hitachi diagnostic tools. and check.

In the mean time is it possible to isolate these bad sectors? 

What I am surprised about is that this computer is 10 months old. How could the hard-drive have failed so soon?

---

### Post by srs5694 on 2011-02-11
If I'm reading that correctly, your drive has 65,542 bad sectors -- a value that's far too large. It's time to replace the drive, unless you think the SMART utility is producing a false alarm. (You could try another utility, such as one provided by the disk's manufacturer, just to be sure. Don't dilly-dally, though; if the disk is in as bad a shape as it appears to be, it could fail completely at any moment.)

Don't bother trying to isolate the bad sectors. Although the "badblocks" program can locate the bad sectors, and you can feed its output into other programs to map them out, learning to use the tools will take valuable time that would be better spent driving to your local Best Buy, Staples, or whatever to buy a new hard disk. There's also the risk that you'd use the tools incorrectly, thus creating new problems.

As to the early failure, that's hard to say. Most electronics devices fail either very early (in the first couple months) or very late (after years of use). It's conceivable that you've actually had this problem since very early and have only just noticed it. It's also possible that one of the factors robsoles mentioned (static, physical jolts, etc.) could have damaged the drive. It might also have just randomly failed at an unusual time.

Since the computer (and presumably also the hard disk) is just 10 months old, it may still be under warranty. Since you've got Linux on it, I wouldn't trust the retailer to be able to copy your data over to a new drive, but you could consider options for in-warranty replacement -- either back up your data, take the machine in for a replacement, and then restore your data; or swap the drive yourself, contact the disk's manufacturer about a replacement, and then sell whatever they send you (or use it for extra storage yourself). You can make some calls to find out what's possible -- but again, you should act quickly, since the drive may be deteriorating further.

---

### Post by robsoles on 2011-02-11
concur entirely with srs5694 and on mention of that it **might be under warranty** I can't hold my tongue, just in case you don't feel advanced enough to open your PC's case :)

Actually, even if you take the drive out of the case at home/office quite happily, consider putting MS Windows on the drive before taking it to the shop/dealer that you got it from - unless they sold it to you with Ubuntu on it or you see them openly advertising Linux Systems (not Apple), you might find them trying to blame Ubuntu for the failure of the drive.

I had a very terse conversation with the fellow who sold me the drive that Ubuntu 'dobbed in' nice and early, when I took it back under warranty (6 month mark, lots bad sectors just like you...), directly after telling him that my Ubuntu OS alerted me that the drive needed to be replaced.

He upped his testing and started telling me how it was probable that Ubuntu had burnt my drive out - 4 minutes of *telling* him that every other drive I had bought from him (dozen+) was being managed by Ubuntu installations on different computers, and considering three of those drives were from 2 years ago, he gave in and replaced the darn drive.


This thread seems to cover ghosting a failing drive fairly well: [http://ubuntuforums.org/archive/index.php/t-1100701.html](http://ubuntuforums.org/archive/index.php/t-1100701.html) - might help you :)

---

### Post by mcduck on 2011-02-11
Bad sectors are physical damage on the disk surface, which is something that *operating systems can't cause*. (if the tech guy tries to claim otherwise, he either doesn't actually know what he's talking about, or is actively trying to fool you to pay for the repair when you shouldn't have to.)

So, any bad sectors you see are always a result from either a faulty or failing hard drive, or bad usage (like shaking/dropping a laptop while it's running).

In case of 65,542 bad sectors on a 10-month-old drive, it's definitely a case of manufacturing defect (unless, of course, you have repeatedty dropped the drive or something...)

Also, while it *is* possible to reallocate some bad sectors, even the fact that any appear at all is always a sign that the drive is about to fail and should be replaced as soon as possible.

---

### Post by Paqman on 2011-02-11
That's a huge number of bad sectors. Back up the data on that drive immediately.

---

### Post by Luinar on 2011-02-11
My HDD is showing as having 26 bad sectors. I only found this out after installing Ubuntu on this machine. HOWEVER, shortly after I got this PC, I had booted Windows one morning to be greeted with a message telling that critical hard drive failure was imminent and to back up all data. Which I promptly did and... 2 years later I'm still using that drive. :-O

So yeah, you may get extremely lucky and get some more life out of it, but with a value that high I would definitely take the advice in this thread on board and back-up, back-up, back-up!

---

### Post by philinux on 2011-02-11
Install gsmartcontrol and double check this. Also double check with manufacturers software if poss. 

It could be a false reading.

Check in /var/log/messages to see if there are any real read/write errors being reported.

---

### Post by frotzed on 2011-02-11
I agree with the above assessments that bad sectors on a disk are not caused by the OS, but typically by a failing HDD.

In addition to the diagnostic tools mentioned above, also note that Seagate has Seatools for DOS.  [http://www.seagate.com/www/en-us/support/downloads/seatools](http://www.seagate.com/www/en-us/support/downloads/seatools)

You burn the .iso to a disk and boot from CD to check your HDD.  Has proven mostly accurate in my experience.

---

### Post by bilallucky on 2011-02-11
Is the disk utility there offering you to view 'SMART data' for this drive

---

### Post by philinux on 2011-02-11
> **bilallucky said:**
> Is the disk utility there offering you to view 'SMART data' for this drive

See OP post #4 for screenshot.

---


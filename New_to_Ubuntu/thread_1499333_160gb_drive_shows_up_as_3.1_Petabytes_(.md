---
title: "160gb drive shows up as 3.1 Petabytes :("
date: 2010-06-01
forum: New to Ubuntu
---

### Post by yamfox on 2010-06-01
This is a hard drive that is essentially fried, but I am wondering how I am to fix this issue. Can I manually change the size the drive reports as?

---

### Post by Ozymandias_117 on 2010-06-01
Man I wish my hard drive would turn into 3.1 Petabytes! :P

---

### Post by Frdbrkl on 2010-06-01
To answer your question...you can make it say it's a Rolls Royce, but it won't fix the problem. LOL.

You can try.....

a. Start from beginning. Broken Pins? M/S jumper correct? Cabled properly and secure?  No daisy chained CDroms on IDE primary to keep safe.  BIOS settings correct?(head and cylinder parameters can cause this-but Petabyte?)

b. The software for the drive from the manufacturer. NO LOW LEVEL FORMATS ON MODERN DRIVES! WD has DataLifeguard etc.  Many times a simple test will reveal problems and help in the troubleshooting and repairing.

c. dd or one of the other programs from "the ultimate boot cd".  Download it or buy one off ebay for 5 bucks. NOT FOR BEGINNERS OR INTERMEDIATES. KNOW WHAT YOU'RE DOING!

d. If you're really clever,have a bit of electronics knowledge and grapes the size of medicine balls, you can piece together a new drive using the old platters in an identical casing or simply change the onboard controller if it's a controller issue.  This solution rates up there with the previous. Not for the faint of heart, and a last ditch effort.  If it works, you want to back up quickly!

Apologies in advance for the caps, but this is a beginners forum, and these are serious warnings.

Lastly...check the warranty!  Many drives carry a 3 or 5 year warranty.

Free Hard disks are good, mmmkay!???

Hope this helps!

---

### Post by srs5694 on 2010-06-02
What utility is reporting a 3.1 PiB size? My suspicion is that the drive isn't actually reporting its size that way, but that it's reporting a size of 0 and the utility has a bug that's causing the size to be corrupted (say, if it subtracts something from the reported size, which could cause the value to "roll over" to a very high value). There was a bug in my gdisk program that did this, but I fixed it in version 0.6.7. (I don't recall what the reported size was.)

To more directly answer your question, I don't know of a simple way to force a drive to appear to be any particular size for all purposes. You could modify the drive's size in a specific program by locating the code that determines the drive's size and modifying it to set a specific value. That might conceivably be enough for some purposes. A similar hack to the Linux kernel could get it working more generally. If the drive is fried enough to be misreporting its size, though, I wouldn't trust it for anything, even if I could work out a hack to make it look like it's working. Even 1 TB drives cost less than $100 these days, so IMHO it's not worth trying to rescue a 160 GB drive. If you've got valuable data on the drive you want to recover, though, that may be another matter -- but then you also just need to get a clean data stream from the drive; the reported size isn't directly relevant, unless it interferes with dd, ddrescue, or some other data recovery rool.

---

### Post by yamfox on 2010-06-02
I do not have the money to purchase a new drive at the moment. Every tool I have tried including UBCD reports it as 3.1 petabytes.

---

### Post by philinux on 2010-06-02
I reckon we got a nautilus bug. I thought I saw this the other day but I couldn't repeat it at the time.

This is properties for my file system.

It's a 250 GB drive with 30 Gig used according to system monitor.

Nautilus is reporting 128 TB, I wish.

[edit] [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/588848](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/588848)
Please add any comments to the bug.

---

### Post by yamfox on 2010-06-02
It is now fixed. I plugged the drive into an older computer I had in the closet and ran Parted Magic and guess what? It recognized it as 149.5 gb right away. I formated it and now it's fine. I reckon it had something to do with my bios. Thanks everyone!

---


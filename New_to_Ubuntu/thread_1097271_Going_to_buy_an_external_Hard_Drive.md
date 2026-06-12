---
title: "Going to buy an external Hard Drive"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by suitedaces on 2009-03-15
Will it be compatible with ubuntu and will I be able to partition it so I can have 250gb to back up vista and 250gb to back ubuntu? 

Not sure about the spamming rules, so I'm going to post the spec rather than the product itself. If that's not enough, just tell me and I'll show you the hard drive I'm thinking of if it's not breaching the rules. 

# Based on the latest SATA hard drive technology.
# Auto installation.
# Plug and play secure and reliable USB backup and storage solution.
# Includes *BrandName* Secure LockWare, auto back-up software and USB cable.
# Preformatted for immediate use.
# Compatible with **Windows 2000/XP/Vista and Mac OS X**.



Is the lack of linux there an oversight, or is there good reason for it? Sorry if this is a stupid question, I'm just reluctant to spend £50/60 without certainty.

---

### Post by fatbotgw on 2009-03-15
Yes it should be compatible...I don't know of any reason why it wouldn't be.

As for the partitions, you'll have to repartition it if you want two seperate partitions for vista and ubuntu.  GParted will work for this.

---

### Post by Sir Jasper on 2009-03-15
Hi,

I just bought an external drive (attached via USB port) I am very pleased with it but it seems to have a maximum speed of about 3.3 GB per minute but I am only getting about 0.6 Gb per minute. That is fine for me as I don´t have a lot to transfer.

If speed matters to you get good advice here or check before you buy?

Cheers

---

### Post by egalvan on 2009-03-15
> **Sir Jasper said:**
> Hi,

I just bought an external drive (**attached via USB port**) it seems to have a maximum speed of about 3.3 GB per minute I am only getting about 0.6 Gb per minute. That is fine for me as I don´t have a lot to transfer.

If speed matters to you get good advice here or check before you buy?

Cheers

USB-2 maxes out at 400Mb/s.

You need Firewire-II or eSATA for faster speeds.
Or the up-coming USB-3.

ErnestG

---

### Post by Kellemora on 2009-03-16
Hi SD

I'm not sure about the particular drive you are talking about, BUT RECENTLY some new hard drives being sold are WINDOWS ONLY hard drives.
I've seen a few posts on here about them!

So far, I've not had any trouble with any hard drives I've purchased recently, not even all the externals!  BUT, I do have one older Western Digital 120gig external that will NOT work on Linux at all!  Requires a Doze driver for some reason to get it to be recognized, came on a CD with it.  Newer drives don't need OEM drivers to get them to work, must be built into the drives themselves I guess.

My data file servers external HD's are formated in EXT 3 and I use Rsync to back it up to a Mirror formatted as NTFS, so if worse comes to worse, (like the office burns down) it can be read just by plugging it into a Doze machine somewhere, which would be readily available nearly anywhere.

TTUL
Gary

---

### Post by stchman on 2009-03-16
> **suitedaces said:**
> Will it be compatible with ubuntu and will I be able to partition it so I can have 250gb to back up vista and 250gb to back ubuntu? 

Not sure about the spamming rules, so I'm going to post the spec rather than the product itself. If that's not enough, just tell me and I'll show you the hard drive I'm thinking of if it's not breaching the rules. 

# Based on the latest SATA hard drive technology.
# Auto installation.
# Plug and play secure and reliable USB backup and storage solution.
# Includes *BrandName* Secure LockWare, auto back-up software and USB cable.
# Preformatted for immediate use.
# Compatible with **Windows 2000/XP/Vista and Mac OS X**.



Is the lack of linux there an oversight, or is there good reason for it? Sorry if this is a stupid question, I'm just reluctant to spend £50/60 without certainty.

Yes, it will work just fine.  The ntfs-3g package is installed by default in Ubuntu so if you choose NTFS you can read/write OOB.

I would completely reformat the drive as to get rid of the cr@p that external hdd makers put on there.

---


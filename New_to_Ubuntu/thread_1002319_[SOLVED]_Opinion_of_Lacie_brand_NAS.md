---
title: "[SOLVED] Opinion of Lacie brand NAS"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Kellemora on 2008-12-04
Hi Gang

One of my primary backup drives has failed and I need to replace it.

It was suggested that I consider a LaCie 301257U - 1 TB NAS in lieu of another USB 500 GB Hard drive.

This is a 2 hot swap Sata II unit with built in network services of FTP, HTTP, SMB, AFT, and Apple Bonjour.  Protocol is TCP/IP.

The documentation shows it is Linux compatible, but the supplied software is only Windows and MAC.  I assume using a Browser to access Administration Features is how it's done on Linux.

The one thing I'm curious about is that the minimum requirements to use a NAS (all of them I looked at too) require Windows or MAC with 512megs of memory.  What does the memory in a computer have to do with a hard drives functionality?

The reason this brand was suggested was that feature for feature it is 200 bucks less than the competition, and I can get it for slightly under 300 bucks.  I found it on Tiger Direct for 329 bucks as the lowest on-line price.

LaCie also makes a 500gig NAS with almost no features to speak of, that I can pick up two of those for about 80 bucks each.  Use one for storage and the other for backup (I think?).

To be blunt, I know little to nothing about NAS anything!
I don't really like RAID 0 or 1 and the more expensive 1 TB model only has RAID either BIG or Mirrored Raid 100.
Since the drive that went bad was a backup, I could reverse the system and use the NAS as the file server and the remaining USB 500gig drive for the backup of the NAS.  I also have off-site backup, triple redundancy!

If I set the NAS to BIG, I will need a 1 TB USB Drive to back that up or at least another 500gig USB.  But I have no idea what capabilities are available to backup a RAID NAS in Linux.

So any information about NAS or another suggestion would be greatly appreciated.

Thanks
Gary

---

### Post by anewguy on 2008-12-04
I can't answer your question directly, but I can offer you some advice:

a few years ago I purchased a USB connect external Lacie hard disk from TigerDirect.  I have no idea whose problem it was, but the hard disk was trash from day 1 - bad blocks everywhere.  I even took the drive out of the USB box and connected directly to my internal IDE - same problems, so I know it was the drive that was trash.  Now, I have gotten other things from TigerDirect, so I don't want to bad mouth them, but in this instance I was left "stuck" with a bad drive - neither they or Lacie would do anything about it.  Needless to say that has left a bitter taste in my mouth for TigerDirect and Lacie.  I am sure the vast majority of people are satisfied, but there are some problems there.  If you look at their website and read the user reviews of some of their barebone kits, and in particular the case and power supply, you will find that many (at least those who wrote a review) received broken cases, power supplies that failed right away, etc..  So, I guess this is just a little bit of a beware - if the price is considerably lower at TigerDirect, I might question the product.

Again, I don't want to bad mouth TigerDirect or Lacie - I can only give you my personal experience with them.

Dave ;)

---

### Post by Kellemora on 2008-12-05
Hi Dave

Thanks for your reply!

I wasn't getting the NAS from Tiger Direct and the few things I have purchased from them have all been in top shape.  But in almost every case, I found the same item a few days later for cheaper locally and without shipping costs too.

In the past few years I've purchased MANY hard drives that had several bad blocks from day one.  And some top names too!

I've never heard of LaCie brand until our supplier mentioned them.  Apparently he's got several to unload thus the reason for the cheap price.

My personal thoughts are to stay away from NAS altogether and stick with what I know works well for me.  I used to use Western Digital without problems for years, now it seems Maxtor is the better of the two.  The hard drive that just failed was a cheap Seagate, only 2 years old if that.  Since it was just for redundant backup I took the cheaper route.  All the rest of my backup externals are Maxtor, never lost a one of those yet.

Someone said I could probably just put another drive in the external box, then someone else said it would have to be a duplicate drive as to the one that was in there?  Think I'll just go with new something, don't know what yet though.

TTUL
Gary

---

### Post by anewguy on 2008-12-05
One question on your Seagate drive - do they still provide a 5-year warranty on their drives?

Dave ;)

---

### Post by Kellemora on 2008-12-05
Hi Anewguy

Yes, Seagate has a 5 year warranty on all of their NEW hard drives!

The local company I buy stuff from super cheap sells Refurbished equipment.  I have no problem with that because MOST of the things I buy as Class A Refurbished is Brand New, just didn't work out of the box and needed something repaired, like a power supply or something.  I tend to shy away from Class B Refurbished because that is USED Stuff.

There is no telling HOW LONG this hard drive sat in inventory before I purchased it.  The label clearly states, Seagate Certified Repaired HDD and the warranty expired on 08-Feb-2008.
Since Seagate only works in even years, I can guess it sat on the shelf for at least 4 to 6 months before I purchased it.
So it had a 2 year warranty probably, but expired about 16 months after I bought it.  It had NO ERRORS when I bought it, and NO ERRORS when I tested it only a few months ago.

Like the NAS I'm looking at he has in stock.  Tiger Direct has it reduced to $329.00, he has it for $289.00 + local sales tax.
I'm sure it's Class A Refurbished, because he know I don't want used and has never tried to sell me anything Class B yet.
I purchased my last laser printer from him too and Konica has sent me parts for it for free, even though it's long out of warranty.  I only paid $265.00 for it brand new Class A Refurbished of course!  And I do a LOT of printing!

TTUL
Gary

---

### Post by doas777 on 2008-12-05
I've always found LaCie to be a weak brand in general. I kinda consider them a twin of belkin. who knows, it may work just fine for you for years.

personally instead of a nas, I'm gonna pick up onna them 1TB internals for 89.95 and share it out off samba.

have fun and hope it works out for ya

---

### Post by anewguy on 2008-12-05
I have also over the past 20 years bought tons of used parts - sometimes back in the beginning it was the only way to be able to afford to get it! ;)  Even now, I'm torn because I also have a place I love to get used stuff from and has been good to me, so I'm glad to hear there are others who also have the same opportunity where they live.

Best of luck!  Let us know how that NAS works out for you (I'm curious as I'd like to get NAS with RAID sometime next year).

Dave ;)

---

### Post by Kellemora on 2008-12-06
I ang

With all the computers I have around here, I think I'm going to build up a file server from scratch.

I'm one of those who LOATHE RAID with a passion!  And with good reason too!

I can buy brand new top of the line computers, built-ups for between 300 and 350 bucks NEW, not Refurbished, from a local company that doesn't skimp on cheap parts either.  For example, The smallest size power supply he uses even in bare bones is 650 watts.  300 bucks is bare bones, but comes with the dual core CPU of your choice including fans and extra fans.  350 is with 4 gigs memory.

TTUL
Gary

---

### Post by Kellemora on 2008-12-06
Hi doas

Thanks for the heads-up!

I've decided NOT to go with NAS aferall.  

And this model ONLY comes in RAID versions too, which turned me off from the git-go.  I HATE RAID!

TTUL
Gary

---

### Post by Paqman on 2008-12-06
> **Kellemora said:**
> Hi Gang
The documentation shows it is Linux compatible, but the supplied software is only Windows and MAC.  I assume using a Browser to access Administration Features is how it's done on Linux.


Yep, I would imagine it'll use a browser to control it.

You *may* need Windows or a Mac on the network to initially set up the NAS. After that you shouldn't need it.

> 
What does the memory in a computer have to do with a hard drives functionality?


Not much. They're just being conservative.

> 
But I have no idea what capabilities are available to backup a RAID NAS in Linux.


Backing up a NAS is no different to backing up any other data, especially once you've mounted the NAS's contents on your local machine.

Rsync is a good Linux backup utility. It's a CLI tool that can be used to synchronise two folders. The nice thing about it is that only the differences between the source and destination are moved, which is very handy if it's all being donw over a network. There's a nice GUI available called Grsync.

What's is it you dislike about RAID, btw? I use RAID1 in my NAS, it protects me against a hard drive failure causing data loss. You've got to admit that's pretty useful, given how unreliable hard drives are.

---

### Post by Kellemora on 2008-12-06
Hi Paqman

> Rsync is a good Linux backup utility. It's a CLI tool that can be used to synchronise two folders. The nice thing about it is that only the differences between the source and destination are moved, which is very handy if it's all being donw over a network. There's a nice GUI available called Grsync.


I've been trying to get rsync to SEE hard drives on my other machines now for roughly three months.  I've read every piece of documentation I could get my hands on and nothing works.

I can run rsync manually to local drives on the same computer, or from computer A to computer B, but as far as copying a file from computer A to computer B automatically I'm missing something because it flat out don't work for me.

> What's is it you dislike about RAID, btw? I use RAID1 in my NAS, it protects me against a hard drive failure causing data loss. You've got to admit that's pretty useful, given how unreliable hard drives are.


I already have redundant backups, including off-site.  Actually NOT backups but MIRRORS.  I don't like backups either, hi hi.....

OK, Raid 1 is a mirror also, you do not gain any space, and both drives are in the same location.  
With Raid 5, hot swap, at least you gain more space, including rebuild, but you still need to back it up.
I actually have two beefs about Raid, which has now increased to three beefs.  Raid is obsolete, reached it's max.
But my main two beefs are, your risking everything to a Controller and no Raid data is recoverable without the exact controller.  Try finding one 3 years down the road that's IDENTICAL to the one in your Raid Array.

Mirroring is almost as risky as Raid 1 as it is.
Data that changes on the original drive, will be mirrored to the second drive.  So if a file does become corrupt and you don't catch it, your mirror is overwritten with the corrupt file.
But it saves all those backup rebuilds.

We had a 4 thousand dollar Raid hot swap system.  The ONLY benefit we saw from it was higher access speed!  Sure, drives failed as expected and were replaced with no loss of data.  UNTIL the controller went south.
When we went to check our off-site backup to reload the data, we found that instead of the data being backed up as we thought, it was just a file of links back to the failed Raid array.  In other words totally useless to us.
The ONLY thing that saved us was I had so many redundant backups that we could recover all of our lost data.

If I was running a Server, YES I would use a Raid 50 system, just for the speed and no downtime, unless of course the controller goes south.  

If you haven't guessed, I don't trust any backup systems anymore.  We've had tape drives fail, tapes that couldn't read, you name it.  So each and every computer here in daily use (that's 8 of them) contains two identical drives, mirrored.  Not much different than raid except it does not require a Raid controller.  Each Drive is Bootable, before being used for storage.  Meaning, using WinDOZE terminology.  If Drive_C fails, I can pull Drive_C and move Drive_D in it's place, install a New Bootable Drive_D and boot right back up where we left off.
Attached to each machine via USB is an External Hard drive Three times a day the data on Drive_D is compared to the External Drive, similar to rsync and changed files updated.
Because of the possibility of corrupt files, we COPY the contents of each External Drive to a Master Drive in a different building through the LAN to a new folder for each DATE.  When the drive gets FULL, the old Folder falls off to make room for the new folder.  This way we have roughly 3 to 4 months of duplicates.  This master drive is Mirrored off-site.
Plus, important files are archived to permanent media, such as CDs or DVDs burned at a very slow speed to get burn depth in the media to insure readability.  They are checked and filed in the vault.

Simply stated, why go with FakeRAID or RAID 1, which only gives a false sense of security, especially if the controller fails, when you can just as easily MIRROR standard drives and make them bootable to boot?  Unless you have RAID for SPEED reasons of course!  In that case, RAID 5 or 50 is the way to go!

TTUL
Gary

---


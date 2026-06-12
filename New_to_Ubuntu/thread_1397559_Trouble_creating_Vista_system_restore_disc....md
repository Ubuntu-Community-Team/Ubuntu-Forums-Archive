---
title: "Trouble creating Vista system restore disc..."
date: 2010-02-03
forum: New to Ubuntu
---

### Post by solutionorppt on 2010-02-03
I have partitioned and defragmented 120 GB on my HD and I am preparing to install Ubuntu in a dual-boot setup. I have backed up all of my important files on an external HD.  However, I can't seem to find any way to create a system restore disc in case of a catastrophic mistake along the way here. Went on MS site, and a video shows me how to create one using buttons that don't actually exist in Vista. (Insert favorite profanity here.)

I have a system restore partition built into the HD, but if something goes awry, I'd like to be able to boot from a disc. I have more than enough space to copy the restore partition onto the external but have concerns about actually being able to restore from there over USB.

Any suggestions?

---

### Post by lukeiamyourfather on 2010-02-03
If you have any Seagate or Maxtor drives then Seagate has awesome free software for backing up complete drives and partitions. There's also lots of free tools to do this like Clonezilla. Cheers!

---

### Post by solutionorppt on 2010-02-03
It's a western digital my book (500 GB) if that matters... my concern is that I won't be able to access the drive via USB if Vista fails (more than it does at everything else in general) or something crashes during installation.

I also feel that it's worth mentioning that the desktop I'm doing this on is now out of warranty, so if anything happens that I can't repair, I'm pretty much SOL.

---

### Post by tgalati4 on 2010-02-03
What has worked for me in mirroring an XP and Ubuntu dual-boot system:

Install a second hard disk--unformatted--of equal or greater size.

Enumerate your drives:  (write down the drive assignments)

sudo fdisk -l

Presume that your boot disk is /dev/sda and your second, blank disk is /dev/sdb: (yours may be different)

sudo cp /dev/sda /dev/sdb

Swap drives and boot to verify that the copy works.

Recapture the extra space if you used a bigger drive:

sudo gparted

---

### Post by solutionorppt on 2010-02-03
Oh, about 45 more minutes of wading through MicroSloth tech support forums led me to a page where they inform Vista users that Vista no longer has this utility, that you have to contact the manufacturer...

So if, like me, you're using an HP w/Vista as the original OS go to:
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00882383#](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00882383#)
for directions

---

### Post by Mark Phelps on 2010-02-03
IF what you're really interested in doing is saving off your Vista partition so you can restore it later, a couple of free solutions are available.  Look around for Macrium Reflect and EASEUS Partition Manager (or is it Master?).  Both will allow you to backup and restore your Vista partition.

---


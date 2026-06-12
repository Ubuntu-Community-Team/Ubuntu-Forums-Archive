---
title: "Extremely slow to copy a large file to an external HD drive."
date: 2008-12-14
forum: New to Ubuntu
---

### Post by flutti-tutti on 2008-12-14
Hi
I have a 14GB file created as a backup of my entire Ubuntu system, following the tutorial of the week for February 25, 2008, Heliode's "Howto: Backup and restore your system!"

I need to copy it to my external NTFS hard drive connected through USB.  It takes a long time to copy this 14GB file (from an ext3 partition) to the external hard drive.  Nautilus is used to copy it, and its speed is ridiculously slow; it might take a few days to complete copying.  

The external USB hard drive has a 120GB free space, which is not fragmented.   The "System Monitor" showed sporadic 60% CPU usage.

Is there anything I can do to improve its transfer speed?
Thanks.

---

### Post by malathion on 2008-12-14
Is your interface USB 2.0 at every level? (hard drive interface, controller on your mobo)

---

### Post by cariboo on 2008-12-14
Have yopu tried copying from the command line?

```
sudo cp bigfile /dev/sdb
```

The above is just an example, as your device label will more than likely be something different.

Jim

---

### Post by JKBurton on 2008-12-14
Wow, 14 GB in a few days, huh? Reminds me of the  days when I stored files on cassette tapes. Ouch! :)

Hmmm, are you sure it's NTFS and not FAT32? FAT32 disks have a maximum filesize of around 4GB, so if the file starts copying quickly then stalls, maybe the error checking for that is broken and the copy's just gonna hang forever.

Even if you're sure about NTFS, I'd give it a test since it's easy. Just create a file close to, but under, 4GB and try copying that one to the external.  On my EXT3 external that only takes a few minutes.

You can create a 3GB test file from the command-line (Applications/Accessories/Terminal) with the command:
```
dd bs=3000k count=1000 if=/dev/zero of=testfile

```

(On my laptop, it took about 3 minutes for "dd" to create the file, so don't panic if it looks stuck) Now try copying "testfile" from your home directory over to the external drive, and see how long that takes you.

Come back and let us know if the testfile works okay, or if it takes forever too.

Edit: Remember to delete testfile from both drives once you're finished.

---

### Post by Kellemora on 2008-12-14
Hi FT

I just finished mirroring 36gigs to a blank USB 140gig external using grsyn with verbose and show transfer turned on, took 1 hour 14 minutes, no errors.

So you definitely do have something amiss there my friend.

You are plugged directly to a USB2.0 port ON THE COMPUTER aren't you?  You cannot go through a hub or switch for External Drives, or so they say.  I've done it accidentally and it worked, but then the drive was unmountable.  Plugging it in where it belonged fixed it though, so I lucked out for once!

I would prefer to do this over the LAN to the off-site drive, but have never yet got rsync or grsync to find network drives.  So, I tote an external along with me to the office and tote it back home at night and copy the data to the master drive down there.  Some day I'll figure it out though, I hope.

TTUL
Gary

---

### Post by flutti-tutti on 2008-12-19
Thanks for your responses.    

will experiment from the command line with a smaller file (3GB).   
(My 14GB file included a guest OS with applications in VirtualBox.)    

Before the experiment, I tried to backup my entire system without the guest OS, using "Simple Backup".   

Now, creating a new troubling problem, it used 100% cpu time for a good one hour, and somehow created a huge file(s) occupying up to 160GB - 86% of the disk.   I could not locate this huge file(s), and have posted a question in a new thread.     Thanks.

---


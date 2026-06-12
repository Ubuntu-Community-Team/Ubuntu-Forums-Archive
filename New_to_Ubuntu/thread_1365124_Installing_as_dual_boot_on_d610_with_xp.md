---
title: "Installing as dual boot on d610 with xp"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by Papa-san on 2009-12-26
Hello folks!
I received an older Dell latitude D610 for Christmas. (I love it!) I'm a writer, and don't plan to do too much more than that and research... I'm keeping XP, but have been an Ubuntu junkie for a few years now.
I had a C610 for years with Breezy on it, and that's when I fell in love with Ubuntu.
My Desktop is running 8.04, and I am comfortable enough with installing it on this laptop... I just need to know what to look for as far as wireless, sound, and video problems. 
The other issue I need to address is hard-drive space. 
I need to have enough room to install a good game on the windows side, but I want to avoid the space issue I have on my Desktop.
That Desktop and this laptop have 40 gig hard-drives. After a few months, I began having problems updating (Desktop) because of space. 
I have 23 gigs allocated for Ubuntu on the Desktop and 17 for windows. I think this is a good division, but I think my /home is too big, and / not big enough.
Can someone help me look at the other one to see where I went wrong so I can keep this new system working smoothly in the future?
I would appreciate it!
John

---

### Post by Papa-san on 2009-12-26
I have 32.25 Gigs of space on this Laptop's HD.

I will be setting up a separate /home directory, and most of my writing goes onto a removable thumb-drive.

---

### Post by Papa-san on 2009-12-26
To allocate some space from the XP partition, do I need to use something in windows? Or can I just use the Ubuntu installer to do it?

---

### Post by audiomick on 2009-12-26
Hallo.

I hope I have understood your questions correctly.

To resize your xp partition, you can use gparted (linux tool), but I have seen quite a few suggestions to use windows tools to do that.
Clean out first, de-install anything you don't want, delete all redundant data and so on. De-frag, maybe a couple of times if the xp install has been running for a while, or you removed lots of stuff. Shrink the partition, then restart xp a couple of times and let it do any disc checks it wants to do.

To look at the setup on the desktop, one choice is system> administration> system monitor (or something similar to that. Mine is called "systemüberwachung" ;) ) The last tab, "resources" shows you how big and how full your partitions are.

Another choice is to install gparted, or get a gparted live cd
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
and look at it with that.

If you are storing everything to external media, your home can be quite small. I have seen posts from one bloke who has a large data partition and stores everything there, who says his is only 1GB. I wouldn't go that far, but if you are storing the bulk of your stuff externally, 10 gig or so should be ample, I think. I also think it is easier to shift stuff out of home than to make room in / when it is full...

My / is up to 6.4GB now, after successive updates from 8.04 to 9.10 and pretty indiscriminate installation of anything that has interested me in the meantime. A fresh install I did recently had about 2.7Gb (with a separate home).
Most people in the forums recommend between 10 and 15GB for / when /home is on a separate partition. In your case, I would tend towards 10GB.

That leaves swap.
If you want hibernate to work, your swap has to be as big as your RAM. Apart from that, how much you need depends on how much RAM you have. If it is not very much (256MB or 512MB), you should perhaps consider a bit more. If your RAM is over a GB, you may never really get into the swap space much at all. However, it is not recommended to install without any swap space at all. At a guess, leaving out the hibernate consideration, 1 GB might be enough. If you use a lot of RAM intensive applications, maybe 2GB.

---

### Post by Miljet on 2009-12-26
I have always run Ubuntu in 20 gb partitions and have never had a problem with running out of space. But I don't use a separate /home partition either.

You can let the Ubuntu installer resize and create your partitions. Most people advise shrinking Vista partitions from within Vista itself to avoid problems, but it doesn't matter for XP. Just be sure to defrag Windows first.

For what it's worth, I think that I am the only person in the world that had problems with 8.04. I installed it on two different computers (laptop and desktop) and never could get java to work correctly. Upgraded to 8.10 right after it was released and haven't had a problem since.

---


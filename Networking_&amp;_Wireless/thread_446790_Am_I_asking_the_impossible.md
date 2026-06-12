---
title: "Am I asking the impossible?"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by MarkGH on 2007-05-17
I have a desktop PC that is dual-boot XP & Debian 3.1.  This machine is practically always booted into Windows, thanks to my wife who will not go near Linux, but that's another story...

I use a laptop running Kubuntu 7.04 and access shared XP folders on the desktop via a wireless router.

But how can I access the Linux drive on the desktop from the laptop?

I have tried using ext2ifs from fs-driver.org and it allows me to read and write to the Linux drive from within XP on the desktop - but XP will not allow that drive, or any part of it to be shared across the network.  It tells me that it just doesn't exist.

Is there a way of making the ext2 drive on my desktop PC available to my laptop via the network, with the desktop PC running Windows?

I can't be the only person wanting to do this, surely!

---

### Post by ezrollers on 2007-05-17
A possible solution could be to share one of your windows (NTFS or FAT) drive. 
Write data from your laptop to win drive.
You can then write data from win drive to linux drive.

That would get data from your laptop to your linux drive while running windows

---


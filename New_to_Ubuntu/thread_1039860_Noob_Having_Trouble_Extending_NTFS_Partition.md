---
title: "Noob Having Trouble Extending NTFS Partition"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by cyan on 2009-01-14
Hello, everyone.  I'm a linux noob who knows just enough to get himself in trouble.  I am running Ubuntu 8.04 in dual boot with windows on an Asus EEE PC.  

I need help extending an NTFS partition.  [Here]("http://copilyanez.com/images/Screenshot2.png") is a screen cap of my partitions as they stand right now.

First I created a new NTFS partition (sda7) that I thought I could move over between sda1 and sda5.  I intended to then extend sda1 by the size of sda7. But when I moved sda7, I wasn't able to expand sda1 and then couldn't boot Ubuntu anymore. So I moved sda7 back to where you see it in the picture.

Any guidance in how to extend my windows partition without borking my system would be greatly appreciated.

Thank you!

---

### Post by albinootje on 2009-01-15
> **cyan said:**
> 
First I created a new NTFS partition (sda7) that I thought I could move over between sda1 and sda5.  I intended to then extend sda1 by the size of sda7. But when I moved sda7, I wasn't able to expand sda1 and then couldn't boot Ubuntu anymore. So I moved sda7 back to where you see it in the picture.


Why don't you make your Linux partition (sda5) smaller at the beginning ?
And then use the freed space for sda1 ?

Make sure the make backups of your data beforehand.
You never know when there's a power-failure etc.etc.
Making regular backups is a good thing anyway.

And to do the resizing, partitions need to be unmounted, so make sure to boot from a Linux live cdrom (a recent Ubuntu installation cdrom is OK).

---

### Post by zvacet on 2009-01-15
Shrink your Ubuntu partition from left to right so that unallocated space be between Windows and ubuntu partition.On that unallocated space expand your Windows.After that you can remove sda7 and add that space to Ubuntu.It will be good (but it depends of you) to have separate home partition.If you decide to make one follow [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.

---


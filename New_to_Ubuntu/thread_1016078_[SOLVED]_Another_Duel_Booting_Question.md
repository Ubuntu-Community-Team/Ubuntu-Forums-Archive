---
title: "[SOLVED] Another Duel Booting Question"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by biggiemokey on 2008-12-19
So I was going to set up a dual boot a while ago but never got around to it, now I think I'm going to finally take the plunge since I recently got a network drive, just have a few questions.

I was planning on this setup:
Windows XP - NTFS
Data - NTFS
Ubuntu - ext3
Swap - SwapFS

Is this setup good?  I was thinking about using ext3 for the Data, which will be shared between XP and Ubuntu, since I heard that it is faster and I can use something called FS Drive in Windows for it to recognize ext3 format.

Is it worth it to set up a /home partition?  I have read in some guides that it is useful but I have also heard it gets annoying as Windows will not read from it, and I want to keep all of my data (including Documents and stuff found in "home") in one place.

And finally, how much space should I give to each partition?  I have 160GB HDD and 2 GB RAM.  I don't know how much to give SWAP, or how much to leave on the Windows and Ubuntu partitions to leave for updates.  I am expecting to have room left over on my Hard Drive since I now have a network drive, and at least 90 GB will be stored on there.  I would like to focus on performance/speed.

Thanks in advance for any help.

---

### Post by Locke_99GS on 2008-12-19
To more seemlessly integrate with Windows, I would personally keep the Data partition as NTFS - Windows can read ext3, but requires extra stuff. Ubuntu can easily read and write to NTFS.

The size of the swap is up to you; if you have very little ram, you may want more swap space than you do ram. If you want to use the hibernate feature, you will want at least as much swap space as you do ram. If you have plenty of ram, you don't even need a swap partition - but it is better to have SOME swap space, just in case.

I have 2g of ram, and use 768m as swap space without any problems. I also don't intend on hibernating this machine.

As far as giving /home it's own partition - you don't have to, but it does make upgrading and other such things much easier in the future.

The size of an ext partition won't effect it's speed, big or small. 


What you have listed so far seems like the average dual boot setup.

---

### Post by Yardarm on 2008-12-19
For the swap size, I've read that you really don't want any more than 2x the size of your RAM.  The reason being that would allow a complete swap of RAM memory.

i.e. completely dump existing contents of RAM to half of the swap partition and completely reload RAM with the other half.

Any more space to the swap partition would go unused.  Then again, I've never caught my computer using the swap partition at any point ever.  And running through the Tombuntu's recommended setup for Ubuntu 8.10 on my Eee PC solid state drive, the recommendation is to use no swap partition at all (for reasons of wearing out the drive).

---

### Post by ilrudie on 2008-12-19
> **Locke_99GS said:**
> To more seemlessly integrate with Windows, I would personally keep the Data partition as NTFS - Windows can read ext3, but requires extra stuff. Ubuntu can easily read and write to NTFS.


I think this depends on which OS you plan to use most of the time.  If you are going to be using Ubuntu most of the time use ext3.  If you are going to be using Windows most of the time then use NTFS.  Just my opinion...

---

### Post by biggiemokey on 2008-12-19
Thanks for all the replies, but I'm still wondering:

1) Is /home partition really useful?  I plan on saving all of my data so that it is easily accessible from both OSes.  I was thinking to save it in C:\My Documents, where I save it in Windows now, and just place a shortcut on the Ubuntu desktop.  This information would still be in a separate data partition from Windows.

2) How much space for each partition?  I have 160 GB HDD and 2 GB RAM, so I'm thinking 4 GB of Swap space.  I don't know how much room to leave for Windows XP and Ubuntu, if anyone knows this info or where to find it I would really appreciate it.

EDIT:  I had another question, is there native support in Ubuntu for NTFS?  I thought there was, and then I found this: [http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)
As someone new to Linux, this seems very complicated after a quick read through of the thread.  Would it be easier to make the data partition ext3 and use FS Drive in Windows, since I know how XP works better?  Or just go with FAT32...I see it criticized but I'm not sure why.

---

### Post by Locke_99GS on 2008-12-22
1) A /home partition is useful if you do alot of reinstalls, or have multiple Linux OS's installed and want the same /home for all of them.

I personally find it useful, but for the average guy that just wants to turn it on, and have it browse the web and write documents, you wouldn't really benefit from it.

2) How much really depends on what you use each OS for, and how often. I use a stripped down versino of XP for gaming *only*, and do everything else with linux.

Off the top of my head, here is how my sda is partitioned:
~50g NTFS for XP
768m swap for swap
10g ext3 for /
~90 ext3 for /home

My sdb is 100% ext3.

NTFS support in Ubuntu is seamless, and works great out of the box since Hardy. (i think?) I am using Intrepid, and the read/write with my NTFS partition is flawless without any configuration, aside from adding a mount point and it's entry in fstab.

That article is a couple of years old, you don't need to worry about it.

---

### Post by zvacet on 2008-12-22
@ **biggiemokey**

I will recommend separate home partition.I found on forum that in Itrepid [fs-driver]("http://www.fs-driver.org/") doesn´t work as it works in previous releases.That is the reason why I will suggest to make shared partition ( for files you want to access from both OS) and format it as NTFS.

---

### Post by biggiemokey on 2008-12-22
Thanks for all the help - I think I will set up a /home partition so that I can try out different distros, as I want to try KDE and XFCE.

---


---
title: "Dual-booting version 9.04 in an HP Laptop with Vista"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by LzF on 2009-04-24
Hello there!
 
This is probably a question already answered but I can't seem to find any help on the matter. 
 
I have the Live CD for Ubuntu 9.04 and would like to install it on my HP Pavilion, which came pre-installed with Vista. I have freed over 30 Gigs of space following the tip to go over Computer > Manage > Shrink Hard drive. Now I have The drive C:\, 30 gigs Unnalocated space, and D:\, the Recovery Drive, in that order.
 
Most How-tos, tips and articles on the web assume you don't have this third partition at the end of the Hard Drive, and therefore when it comes to it during the installation, Ubuntu Recognizes the free space and installs itself there if you choose the option "Largest Continuous Space" instead of Manual Partitioning.
 
Well, in my case Ubuntu indeed found the free space, and shows it on the top of my screen. However, when I select the option for Largest Free Space, the graph on the bottom of the screen changes! It assumes the Windows Vista partition is almost the original size, and allocates mere 2,5 Gigs for Ubuntu! It still recognizes the Recovery Partition, though.
 
Now, there is the option to slide the available space for Vista to the Left, and Ubuntu occupies the newly-freed space. But I have read several posts saying that if you choose to do any partitioning other than the Shrink Option above, you may destroy the File System of Vista and it won't Boot.
 
Anyone with similar problems? I really need the Ubuntu for work but I can't compromise the Vista, nor the recovery partition. I would gladly take some help in Manually Partitioning the HDD if it does not kill Vista.
 
And while on it, does anybody know if setting the Ubuntu OS in between two physical drives is a problem? Will the Recovery partition still be accessible through Windows?
 
I know these questions are not really Linux related, but I guessed I had a better chance finding someone who knows the problem here than anywhere else.
 
Thank you all ;]

---

### Post by Melk79 on 2009-04-24
There was a statement about this issue in the release notes found [here]("http://www.ubuntu.com/getubuntu/releasenotes/904#Wrong%20display%20when%20installing%20to%20largest%20continuous%20free%20space%20on%20disk").  It states it will use the free space only despite the graph.

There is no problem with having ubuntu between the windows and recovery partition.  The recovery will still be accessible.

---

### Post by LzF on 2009-04-24
Hey Melk79 thanks for the help!

I ended up installing manually with the help of some friends, it all worked out fine! I'm just adjusting some quirks with the speakers, the sound only works with headphones, but I'm sure i can fix it after some digging on the internet.

Can't believe I missed that release note, though!

---


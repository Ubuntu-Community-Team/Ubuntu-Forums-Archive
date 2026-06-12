---
title: "vista dual boot &amp; partition woes - again"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by aa4bb on 2009-10-28
On a Dell Inspiron 1525 80G HD running the Ubuntu Live disk 9.04 after I had used Vista Disk Management to shrink the C: partition all that it would, to about 56G and left 9G unused and a 9G Recovery D: That doesn't quite add up but it's approximately right.

At any rate, I run the Live disk and choose to install Ubuntu. In partitioning step, I select the first option, Install side by side. This doesn't correspond to any of the many descriptions I've read, but it seemed to imply that the install would use the 9G of free space. I certainly didn't want to wipe Vista, I didn't have the courage to use Manual (too many horror stories) and I thought I had used "Use maximum amount of free space" before and it only resulted in a 2.6G space for Ubuntu, way too small.

At any rate, after this install, Vista C: has reclaimed the 9G unused. Ubuntu has 2.6G, and I can't do much with it.

Why does partitioning have to be so incredibly difficult with Vista?

---

### Post by oldfred on 2009-10-28
This link has some info on shrinking Vista and some of the issues.

Windows Disk Cleanup tool to houseclean
defrag at least twice
Windows Vista - partition your hard drive using Disk Management, if XP use Gparted
25GB at an absolute minimum 
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Some info on partitions:
partitioning
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

If you use something other than Vista to resize the partition read this:
starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

And if you only ended up with 2.5 this is why. There is a slider you have to move.
HOWTO: 2.5 GB System Partition - What Went Wrong? 
[http://ubuntuforums.org/showthread.php?p=7658271](http://ubuntuforums.org/showthread.php?p=7658271)

---

### Post by aa4bb on 2009-10-28
Thanks! Now I remember reading about the slider but I didn't recognize it or think about it as I looked at that screen. I'll go give it a try...

---

### Post by Buzzsawjfb on 2009-10-28
I don't want to hijack your thread or anything but I also didn't want to get in trouble for making a new one.

My problem is similar, but more my fault.

I bought an (netbook) Acer Aspire One 751 I think, it ran decent with windows vista as long as I didnt do anything crazy. I started to get anoyed with everything taking long so I remembered my friend talking about how much faster ubuntu worked on his vista machine.

Inspired by irritation I look up the official Ubuntu Netbook Remix install tutorial and install it on a seperate partition. All goes well, I was running a dual booting linux/windows netbook. Well after using the netbook remix version I decided I wanted to move on up to full fledged Ubuntu and (!!!) deleted the ubuntu partition via Disk Manager (along with the ubuntu memory card I used to install it) thinking that it would just go back to being a windows only computer. Well after a few hours of web browsing I shut down my computer.

Now when I turn it on it just goes black and says "operating system not found". Like I said I have a netbook so no disc drive, I also don't own a memcard reader except for the one built into the netbook. I do have an old 128mb usb drive, but i doubt that'll be worth anything. If I have to I can buy a little bigger one, but if I have to do anything more expensive than that this netbook is scrap. I backed up all my files onto a 500gb external hard drive, so I at least have those. If there is a way I could use the external one that would be great too. I just really want to get into my "recovery" partition so I can refresh the windows install. I'm sticking to running ubuntu live from now on... or until I get something other than a netbook.

I'm sorry to bother you guys, I feel like an idiot doing something I am not familiar with. If there is anyone who could help me I would appreciate it soo much. If not... well lesson learned.

EDIT: I do still have my vista install partition and a "recovery" partition pre-installed by acer on the hard drive. I just shrunk the vista install one and created a new partition (the one that i deleted later on).

---

### Post by aa4bb on 2009-10-28
I think your best bet is to start a new thread with the appropriate title. I bet you'll get good advice and be able to salvage your computer.

My good news is that I followed the information given in response to my message and had a successful outcome. Vista and Ubuntu dual boot successfully with plenty of room on the Ubuntu partition.

---

### Post by Buzzsawjfb on 2009-10-29
> **aa4bb said:**
> I think your best bet is to start a new thread with the appropriate title. I bet you'll get good advice and be able to salvage your computer.

My good news is that I followed the information given in response to my message and had a successful outcome. Vista and Ubuntu dual boot successfully with plenty of room on the Ubuntu partition.

Will do, thank you!

---


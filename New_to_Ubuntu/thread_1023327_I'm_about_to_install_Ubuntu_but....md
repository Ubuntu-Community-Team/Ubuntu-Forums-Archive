---
title: "I'm about to install Ubuntu but..."
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Jerriy on 2008-12-27
...before that i tried to partition the c-drive to make up free space (with vista's in-built partitioner (CP >> disc management >> shrink) but I noticed that despite the fact that there is plenty of empty space the available size (more than 50% of it is free) the available shrink volume is ridiculesly low (C drive is ove 230 GB but the available shrink space is less than 2 MB!!!

I looked here and there for explanation (including scowering around older posts in this forum) and that geve me a hint that it could be because of the stored files on the C-drive, which are not all in the same side or area of the disc. A defragger utility map showed me that the drive has a few "immovable" files stored not only at the "begin" or middle of the drive but also a few all the way at the "other end".

Even when booting up the machine in safe mode the "immovable" files are still there (though presumabmy in a smaller size than they were before). 

So, since the defragmenting of the disc can't solve this, I need an advise as to how to about this nasty Microsoft Vista conundrum (Yes I suspect that it isn't an accident that there are immovable files all over this Vista-preinstalled machine) 



Oh By the way merry christmas :)

---

### Post by thunk77 on 2008-12-27
No, don't use vista's partitioner.
Download a copy of Gparted ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)), burn it to a CD (it's a Live CD), boot from it and do your partitioning from there.

However if you install from a standard Ubuntu CD, there's a very nice partitioner already in there. I suggest you use it.

---

### Post by SlalomMan on 2008-12-27
Vista's partitoner is fine. I used it the first time I installed Ubuntu, but I like GParted better. XP's partitioner is crap, though.

I had that issue when I installed, and all I had to do was de-frag a few times. Vista's defragger is functional, but stripped down, so it's not the greatest. I'd recommend finding another defragmenter, which google can find for you.

Here are a few I found:
[http://www.vistarewired.com/2007/02/15/defragment](http://www.vistarewired.com/2007/02/15/defragment)
PartitionMagic

The problem is that on a hard drive, the files aren't all automatically put at the beginning, so defragging condenses the files into one spot. Think of it as organizing items on a shelf to fit more into the same space.

---

### Post by Jerriy on 2008-12-27
Thanks for tha reply

Yes I have already burned the live CD so in that case I'll do the gparted thing and prepare the c-drive for a dual-boot partition (that's what I intend to do - install ubuntu and keep vista (for a while at least :)

---

### Post by neu2buntu on 2008-12-27
.....you will have to defragment the disk first!! as the files are all over the place then try again ...slalomman has already postaed this,just noticed there

---

### Post by Jerriy on 2008-12-27
> **SlalomMan said:**
> Vista's partitoner is fine...I'm sure it is fine at partitioning that 0.1% of my c-drive but I hope I'm not being too demanding that I want to partition a bit more than just 0.1% of that drive.

---

### Post by Helios1276 on 2008-12-27
Vista limits the amount of space you can free up due to shadow copies/pagefiling etc. Turning these off (momentarily) can allow you to free more space for an Ubuntu install.

---

### Post by Jerriy on 2008-12-27
> **neu2buntu said:**
> .....you will have to defragment the disk first!! as the files are all over the placeActually files are not all over the place. Only the few "immovable" files are there on the wrong side of the drive.

So the $64000 question is: does anyone know a "super duper" defragmenter that is capable of moving the immovable ones?

---

### Post by SlalomMan on 2008-12-27
> **Jerriy said:**
> I'm sure it is fine at partitioning that 0.1% of my c-drive but I hope I'm not being too demanding that I want to partition a bit more than just 0.1% of that drive.

The reason why Vista won't let you do more than a small percentage is because there are those immovable files. I would strongly suggest defragging first; when I first tried to install ubuntu on an old laptop, I used a liveCD of QTParted, which really messed up my XP partition. Luckily, Ubuntu was good enough that I didn't need xp. hehe.

---

### Post by Jerriy on 2008-12-27
> **Helios1276 said:**
> Vista limits the amount of space you can free up due to shadow copies/pagefiling etc. Turning these off (momentarily) can allow you to free more space for an Ubuntu install.Done all that. Like I said there is plenty of free space (more than 50% of the drive) 

So, even after taking page-file into consideration there should be more than 0.1% of the drive available but according to Vista it isn't. I've heard that the command-prompt version of Vista's partitioner might allow more space available, but if there is one I haven't found it. 

I really suspect that the "immovable" files are the culprit but I can't be sure of that since I'm not an expert in these matters.

---

### Post by neu2buntu on 2008-12-27
maybe just try the ubuntu live cd,and choose install and when you get to the install to drive section ,hopefully it can resize it already(you are not commited to an install at this stage) so you will know the available disk space.....if anything is wrong just go back and nothing will be changed,but as far as i can remember the partitioner will sort this all out for you

---

### Post by Helios1276 on 2008-12-27
space and Vista are a constant issue, it fills a hard drive and often refuses to be trimmed, its like a weed!

---

### Post by Jerriy on 2008-12-27
Not only does Vista take-up a lot of space, it pre-emptively claims the free portion that it hasn't occupied yet! :)

---

### Post by neu2buntu on 2008-12-27
why not just make the complete switch to linux (ubuntu)...i have and can do all the stuff i did with windoze plus more, just do a full install of ubuntu 8.10 and be happy!!! i know some gamers need windows for the occasional game ,but think of all the spy add malware ,viruses and trojans that love your windows install....

---

### Post by mkvnmtr on 2008-12-27
Back up your data. It's important. Users with a lot of experience are saying to use only vistas partition tools to resize a vista partition. There are a couple of tutorials how to use GParted but it is better not to. The defrag with a good tool is the most important after the back up. Defrag several times.

---

### Post by _duncan_ on 2008-12-27
Suggest you back up important data before doing any more defrag / shrinking. GParted, Patition Magic, etc. are really good tools, but there is always a chance of something going terribly wrong when messing with partitions.

I've seen one too many horror stories from people losing important data after shrinking their NTFS partition.

---

### Post by Bartender on 2008-12-27
Did you make recovery DVD's?
I have a suggestion that may seem drastic but I know that this has worked.  If you have recovery DVD's and are confident they're good, wipe the drive entirely with a GParted LiveCD.  

Then, using GPartedLiveCD, create a primary partition at the "front" (left hand side) and format it as ntfs file system.  This partition will be for Windows.  You can create another partition out of the remaining space.  If it were me, I'd make an extended partition first, then create at least one logical ext3 partition inside. I say "at least one" because I'd manually create partitions for / and /home but this isn't necessary if you're not familiar with the process.  The ext3 partition or partitions are for Linux.

Get out of GParted, boot up with your first recovery DVD in the slot, and Windows will install to the ntfs partition, leaving the extended ext3 partition free.

---

### Post by Helios1276 on 2008-12-27
> **Bartender said:**
> Did you make recovery DVD's?
I have a suggestion that may seem drastic but I know that this has worked.  If you have recovery DVD's and are confident they're good, wipe the drive entirely with a GParted LiveCD.  



Dont those type of cd's usually rely on a backup partition?

---

### Post by Jerriy on 2008-12-27
No you're right I'm not familiar with all that extended/logical stuff yet. My priority now is to shrink, nay chop the Vista drive one way or another. I had your Idea in tha back of my mind but as a last resort (I indeed have a recovery CD). I just thought there was a way some expert could tell me how to drag a couple of so-called "immovable" files from one end of the drive (the back end) to join the rest of the files in the cluster at the front end.

---

### Post by appi2012 on 2008-12-27
The page file is immovable. And if that's at one end, you wont be able to shrink from that end. So by turning of the shadow copies and page file, as someone suggested, you can remove the immovable part. Then you should be able to partition more. After you've installed ubuntu, then you can go back and turn the page file back on.

Hope that helps

---

### Post by neu2buntu on 2008-12-27
i did this ages ago in vista and defrag went ok...maybe this is a virus that has got to another part of your disk ,files do get scattered but not as bad as to only give you so little free space,....do as i suggested earlier and try the live cd install it is all reversable,just try it to see what free space it shows

---


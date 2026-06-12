---
title: "What Ubuntu to Load?"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by daveritah on 2010-02-25
I would like to load Ubuntu onto my PC. I have a Dell 1501 with Windows XP and AMD 64 processor. I have 104.99 MB of physical memory and 1.96 GB of virtual memory with a 1.03 GB of page file space. I would like to have a dual load, until I decide whether to delete my XP.  Here are my questions
1) Which Ubuntu would be the best suggested one to Load (32 or 64) bit.
2) If I load the 32 bit, can I upgrade to the 64 bit at a later time.
3) Are there any advantages to using the 32 over the 64 or vice versa.
 
I am new to Linux and Ubuntu and would appreciate your comments, Thanks - Dave

---

### Post by Temposs on 2010-02-25
1) If you have a 64-bit processor, you should run a 64-bit Ubuntu. It works fine :-)

2) No. Well, you would have to reinstall the OS. You couldn't just click a button and upgrade.

3) If you have a 64-bit processor, you will get a performance boost from using a 64-bit OS.

Also, please do NOT use Wubi to install Ubuntu. It causes problems for lots of people and the problems are harder to fix.

---

### Post by PhoHammer on 2010-02-25
> **Temposs said:**
> 1)

Also, please do NOT use Wubi to install Ubuntu. It causes problems for lots of people and the problems are harder to fix.

Agreed, DO NOT use wubi.

And are you saying that you only have 1.03 GB of HDD space for Ubuntu?
That would be pushing the limit for minimum space required, I believe...

---

### Post by 2hot6ft2 on 2010-02-25
> **daveritah said:**
> I would like to load Ubuntu onto my PC. I have a Dell 1501 with Windows XP and AMD 64 processor. I have 104.99 MB of physical memory and 1.96 GB of virtual memory with a 1.03 GB of page file space. I would like to have a dual load, until I decide whether to delete my XP.  Here are my questions
1) Which Ubuntu would be the best suggested one to Load (32 or 64) bit.
2) If I load the 32 bit, can I upgrade to the 64 bit at a later time.
3) Are there any advantages to using the 32 over the 64 or vice versa.
 
I am new to Linux and Ubuntu and would appreciate your comments, Thanks - Dave

Virtual memory and page files are used by windows and have no relevance to linux in general or ubuntu.

Looking at the specs. for the Dell 1501 here:
[Review Dell Inspiron 1501 Notebook]("http://www.notebookcheck.net/Review-Dell-Inspiron-1501-Notebook.2594.0.html")

> Memory
1024 MB, DDR2-533 SDRAM, max. 2048MB, 2x512MB

So 1 or 2 GB of RAM so you can't go any higher than 2GB of RAM and from what you said "I have 104.99 MB of physical memory" I believe you actually have 1 GB of RAM.

If you mean you have 104.99MB of free disk space then no ubuntu wont fit in 104 MB it takes at least about 4GB + swap of at least 1GB. Actually I just checked a usb install I did and it's using 2.52GB with very few changes so 3GB would be a minimum which wouldn't allow for many changes at all.
> Harddisk
80GB 5400rpm Samsung HM080II

and
> Processor
AMD Turion 64 X2 TL-50 1.6 GHz 2x 256 KB L2 Cache
Your processor can handle and would benefit from a 64 bit OS. I have the same processors on mine and I use the 32 bit OS for now. I may go 64 bit later but I am sticking with 32 bit until 64 bit matures a bit more.

1) Depends on 2 and 3
2) To go from 32 bit to 64 bit would mean a fresh install you can't upgrade 32 to 64 it doesn't work that way
3) 64 bit can support greater than 3.3GB of RAM, 32 bit supports up to 3.3GB of RAM. 64 bit is a little bit faster. 32 bit has more apps designed for it but that's changing fast.

Other things to check for compatibility using the forum search would be:
> Graphics adapter
ATI Mobility Radeon Xpress 1150 - 128 MB 256 MB Hypermemory, GPU/clock rate: 400/400 MHz
> Soundcard
ATI SB600 HD Audio
and
> Networking
Dell Wireless 1390 802.11g, 10/100 LAN, 56K Modem 

And I agree with the others do a real install not a WUBI if you decide to do it.

---

### Post by daveritah on 2010-02-25
The partion I have created in the hard drive has 10 GB of available space to load Ubuntu into. - Dave
Should I create more space, my total hard drive space is 80 GB on the C:/, presently I am using about 45 GB of that space for my XP.

---

### Post by 2hot6ft2 on 2010-02-25
> **daveritah said:**
> The partion I have created in the hard drive has 10 GB of available space to load Ubuntu into. - Dave
Should I create more space, my total hard drive space is 80 GB on the C:/, presently I am using about 45 GB of that space for my XP.
Good you just answered the question I was about to ask.
10 GB is fine. You may want to open up about 2 GB of space for a swap partition, it's kinda like Virtual memory and page files but linux uses an actual disk partition for it where windows uses it's own file system.
It doesn't matter where on the disk it is so it can be at the very end (the right side). Windows is partial to the beginning of the disk where linux doesn't care. The installer can format it to linux swap so you don't need to format it to anything in particular windows.

---

### Post by 2hot6ft2 on 2010-02-25
When you run the installer on the livecd and it gets to the partitioning part choose manually choose partitions and click on Forward to load the manual prtitioner. Then you can click on the partition you have reserved for ubuntu and set the format as either ext3 or ext4 (I'm still using ext3 for mine). Set the mount point to "/".
Click on the other for the swap and just set it to format type "linux swap".

Don't be intimidated by it being manual partitioning. It just gives you more control so as long as you don't tell it to use the windows partition it wont disturb it. And it wont make any changes to your HD until after step 7.

---

### Post by daveritah on 2010-02-25
2hot6ft2 you suggested that I create 2 GB for swap partition. Can I do this with the Ubuntu loader, when I install Ubuntu? My only tool available for partitioning is EASEUS Partition Master Home Edition and I am not certain if I can use this tool, to create this swap partition. I am new and still learning how to work with partitioning so any help is greatly appreciated. - Dave

---

### Post by marshmallow1304 on 2010-02-25
> **daveritah said:**
> I create 2 GB for swap partition. Can I do this with the Ubuntu loader, when I install Ubuntu?

Yes.  The exact details are a little hazy in my memory, but it goes a little like this.

1) If you've allocated free space (not a partition) for Ubuntu, skip to step 3.
2) If you've allocated a partition for Ubuntu, delete that partition.
3) Create a new partition in the free space.  Set it to be used as Linux Swap, set size to 2 GB, and set it to the end of the free space.
4) Create a new partition in the remaining free space.  Set it as ext3 or ext4 as desired, set size to the max available, and mount point to /.


You can also do all sorts of fun stuff like making a separate partition for /home, but if this is your first install, it's probably best to keep things simple.


Edit: For future reference, you can also partition with the Ubuntu LiveCD.  You'd select "Try Ubuntu..." (first option) and use GParted (System->Administration->GParted)

---

### Post by daveritah on 2010-02-25
Thanks for the help - Dave

---

### Post by egalvan on 2010-02-25
Some Tech forums indicate that these Dells can see 2GB RAM modules.
(Of course, XP and Vista couldn't "see" more than 3GB, but that's Windows for you. And the main reason this is not recommended by these same forums
"Vista won't see it, so it's useless" :) )


Now, if you need (or want/desire) 4GB of RAM, I would suggest taking it to  a repair shop and see if it will boot with (and recognize) the extra RAM.
Or borrow the RAM from some place.
Or buy it contingent on it working correctly.

Test it with Linux, though :) . Preferably a 64bit version. )

---


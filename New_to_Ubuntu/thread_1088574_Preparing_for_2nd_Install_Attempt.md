---
title: "Preparing for 2nd Install Attempt"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-03-06
The 1st was unsuccessful, so here I go again. I'm looking for help when it comes to partioning.  I'm running XP too, so I need to set up for Dual Boot.  I haven't partioned my HD this time, so it's all on 110GB HD.  When the time comes, do I go with Manual or Guided?  Based of the instructions I'm looking at, I need to create 3 new partitions.  

Root---(at least 4gb?)
Home---(what size?)
Swap -- twice the size of Memory(2GB on the machine)

I'm brand new to Linux, so a lot of the lingo used if fairly foreign to me.  For each drive, can someone tell me the options I need to set it up for?  It's been a few days, but I now there options for ext,ext3, swap, /, mount, etc.  All a bit confusing to me. I'm hoping to get this install correct the 1st time around. I'm looking at this link for reference,
[https://help.ubuntu.com/8.10/switching/first-steps.html](https://help.ubuntu.com/8.10/switching/first-steps.html)
Thanks all.

JS

---

### Post by steve-shinn on 2009-03-06
Before you try installing Ubuntu you need to do 2 things :-

a) Defrag the XP drive at least a couple ot times
b) Shrink the XP partition to make room for the Ubuntu installation

After you have performed a) & b) and boot up in XP, it's gonna twitter first time around because you have shrunk the partition .... but don't worry about, just let it run the chkdsk routine and XP will then be fine

This guide should help :-
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

### Post by Big_Croc7 on 2009-03-06
If you choose 'guided' and tell it to resize your windows partition it should walk you through.  Back up first!  You shouldn't have to worry about filesystem types and mountpoints - the defaults should be fine.  If you have to choose at all I'd say use ext3.

---

### Post by konqueror7 on 2009-03-06
and about your swap size, i think it would be a waste to allocate it 4gb, i have a 2gb ram and i allocate only 1gb swap, and ubuntu rarely even use it...

---

### Post by js@lloyd on 2009-03-06
If I use the guided route, then I don't need to resize the partition prior to?  The guided process will take care of that?

---

### Post by steve-shinn on 2009-03-06
> **js@lloyd said:**
> If I use the guided route, then I don't need to resize the partition prior to?  The guided process will take care of that?


Correct, but make sure you defrag the XP drive a couple of times first, just in case you have XP files at the end of the drive, that could get obliterated by the partitioner.

---

### Post by treepolitik on 2009-03-06
I always do the manual way even though the colors are pretty:) for the new guided interface.  This time(when I installed Intrepid, Ubuntu 8.10), I decided to leave Windows XP and Ubuntu 10,000 MB apiece, which reads as 3.1 GB apiece in the guided partitioner interface(Not sure why: I was taught that one was supposed to move the decimal three places left):(  

Windows XP needs at least 8 MB according to their installation disk, but then it stops you if you don't give it around 2000(I had to install Ubuntu after I installed Windows).  That's only because I decided to start from scratch and have the whole hard drive to work with.  

You probably need to check how much of the Windows allocated space you are using.  **This is for the guided interface:** if you are using the whole hard drive for Windows, you might want to back up and start from scratch, because the guided did not let me shrink the Windows partition.

When I installed Ubuntu, I knew that it **needed 250 MB swap space** to make it work nice(That's one of the reasons I started over: *I don't like using cold boot,* which is holding down the power button for the new people).  So I put the swap space in.

**This is for the manual interface:**
I clicked on the free space entry, left ext 3 file system selected, put 10,000MB, put the Ubuntu partition as primary instead of logical and then put it as "/" in the pulldown menu at the bottom of the box, which is root.  

For the swap space, I selected swap instead of ext 3, put 500 MB(I want Ubuntu to be really fast), put primary again, and then "/" again at the bottom for root.   

I'm not really sure what the difference between primary and logical is, but I wanted Ubuntu to be my primary system.  Now when I start up my computer, an *Ubuntu interface lets me choose between Windows and Ubuntu,* rather than a Windows interface letting me choose between Windows and Ubuntu.  *If you know, please tell me if I am correct in associating these two events.*

I should also note, **do not forget to check the Ubuntu Live CD for errors!**  Last time I did that, the partitioner had an error *even though it had worked months ago,* and I ended up in the manufacturer's boot loop, which was trying to detect the ethernet through PXE-ROM(?) over and over again.:shock:  

When I popped the Windows CD in, it would install Windows, but couldn't get past the loop.  It needed a **super clean** partition, which means I had to select the **slow version rather than the fast.**  I also randomly decided to do FAT instead of NTFS this time.  

*(This is in case you need to install Windows before Ubuntu, for whatever reason).* There is an edition of Windows XP on The Pirate Bay (BitTorrent site), and it's still there as long as they didn't lose their trial.

And for the record, if you're upgrading from Ubuntu 8.04 to 8.10 (for yourself, as the Ubuntu download site recommends), I highly recommend doing so.  I'll put more on this in the Testimonials section later.:popcorn:

---

### Post by js@lloyd on 2009-03-06
Thanks everyone. I went the guided route, and it seems to of been successful install. Now, i'm just trying to iron out a bunch of newbie issues.

---


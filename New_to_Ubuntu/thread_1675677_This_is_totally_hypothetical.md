---
title: "This is totally hypothetical"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-01-25
So,
Lets say I use GParted and delete every partition on a hypothetical drive.

Besides the obvious losing everything and having to reinstall an OS, would this delete the drive's partition table?

If so, how would I create a new partition table?

Furthermore, is deleteing the partition table the end of that drive for good?

---

### Post by uRock on 2011-01-25
Gparted has the option to create a new partition table. The app will walk you through the process. If you use the gparted in the livecd, then you can post back here and ask question while doing it, if you need to. Its a pretty easy process.

---

### Post by skyzthelimit230 on 2011-01-25
OK,
Well, I'm right now playing with the idea of using gparted to remodel the way my drive is partitioned.

I basically want to shrink windows, and give Ubuntu more space on the drive. Thing is, I can shrink ok, but then extending the linux partition dosen't really work. I can't seem to increase the size (though shrinking it is ok)

Also, when I began the work of shrinking windows, the computer "crashed" or whatever and I got a weird screen with blinking colors. (though the partitions are uncorrupted and work fine)

---

### Post by Quackers on 2011-01-25
You don't say which version of Windows you are using. In Vista and Win 7 it is safer to shrink the C: partition using Windows disk management console - after defragmenting the drive at least once.
Please post a screenshot of your gparted screen.

---

### Post by skyzthelimit230 on 2011-01-25
It's windows 7, and I can post a screenshot using the windows disk manager if that is ok? (im not sure hot to make a screenshot with gparted)

---

### Post by Quackers on 2011-01-25
From the live cd desktop Applications > Accessories > Take Screenshot.

---

### Post by skyzthelimit230 on 2011-01-26
Alright, so I don't mean to be a complete moron.

In Gparted I can create the screenshot, and it says it saves in home/user; but how do I get to that image and put it on a USB, or get to the net to upload it here? I have no idea what to do after the initial screen shot is created

---

### Post by Quackers on 2011-01-26
It's easier to choose to save it to the desktop.
Doesn't the live cd desktop connect to the net? Ethernet maybe?

---

### Post by skyzthelimit230 on 2011-01-26
No....or at least, I don't know how to connect to the net via the live CD. I dont see any ooption in either the context menus or the UI. It is connected via ethernet physically

---

### Post by Quackers on 2011-01-26
Don't you have an applet like this in the top panel?

Oh dear, my image doesn't appear :-)
It's like a sound wave sign going upwards :-) or it may be 2 white arrows, one going up and one going down.

---

### Post by skyzthelimit230 on 2011-01-26
Haha yeah you're right, looks kindof like a sine wave....

anywho, well on the top i see terminal, gparted, screen capture, and some other applets. I can't remember all of them

---

### Post by Quackers on 2011-01-26
Is the live cd desktop connecting to the net now?

---

### Post by skyzthelimit230 on 2011-01-26
No, that applet doesn't appear :(. The wifi looking one.....

---

### Post by dBuster on 2011-01-26
Having just shrunk my windows partition I learned something very important.

You must shrink the windows partition using windows only.  Because of the different places that windows places stuff on that partition.  If you do not you run the risk of losing the windows partition functionality to boot into windows.  There are other posts here in the forums that talk about resizing windows that may help, search them out.  I can say this, it is a PITA to shrink a windows partition due to locations of bits that windows uses.  It took me two other applications that move those bits around in order to clean it up enough to shrink it down and then I still was not able to shrink it as much as I wanted but at least I still shrunk it.

As far as increasing the size of the Ubuntu partition, if you have unallocated space on the drive you can increase the size of your Ubuntu partition if you are not using that partition.  Meaning if you boot from a livecd you can increase the size of it.  Generally without any harm.  You can not change or modify a partition if you are using it, ie one that you have booted from/to and have it mounted.

---

### Post by skyzthelimit230 on 2011-01-26
Ok, but why can't I shrink the windows partition at all? I can only shrink it 14441mbs, that's all the windows disk manager is allowing me to? I want to shrink it by 50 gigs.

I attached a snip capture for you to check out.

---

### Post by Quackers on 2011-01-26
> **skyzthelimit230 said:**
> Ok, but why can't I shrink the windows partition at all? I can only shrink it 14441mbs, that's all the windows disk manager is allowing me to? I want to shrink it by 50 gigs.

I attached a snip capture for you to check out.

Possibly because Windows stores data at the end of its partition. Have you defragmented the C: partition?
It is not uncommon for Windows to restrict the shrinking of its partitions.
Sometimes turning off the paging file will allow further shrinkage.

---

### Post by skyzthelimit230 on 2011-01-26
Yep, I defragged twice before shrinking....How do I turn off paging files? 

Thanks for all your advice :)

---

### Post by Quackers on 2011-01-26
This guide is for Vista, but Win 7 should be very similar (if not the same)
[http://www.mydigitallife.info/2008/02/26/tweak-windows-vista-virtual-memory-change-or-disable-paging-file-size/](http://www.mydigitallife.info/2008/02/26/tweak-windows-vista-virtual-memory-change-or-disable-paging-file-size/)

After resizing, don't forget to turn it back on :-)

---

### Post by irv on 2011-01-26
Here is a link I found on HowTo: Partitioning Basics: 
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

---

### Post by dBuster on 2011-01-26
> **skyzthelimit230 said:**
> Ok, but why can't I shrink the windows partition at all? I can only shrink it 14441mbs, that's all the windows disk manager is allowing me to? I want to shrink it by 50 gigs.

I attached a snip capture for you to check out.

Windows likes to hide particular parts at the end of their partitions which makes shrinking them darn tough.

I had found a thread here in the forums, which I apologize I can not find right now but if you search for it I am sure you can find it, it talks about two utilities that you can download that will take those immovable blocks that windows likes to put at the end of the partitions and move them for you.  I had to run that utility like 5 times I believe to get everything moved enough to shrink my partition.  

The drawback is that you have to download a trial of a program called "PERFECT DISK"  search for that and I am sure you will find the thread.  Actually I just found it for you [Vista partition/drive shrink problems...](http://ubuntuforums.org/showthread.php?t=1386502&highlight=perfectdisk)  I know it talks about vista but I am sure 7 is the same way.

Good luck!  Don't give up!  You can do it!

---

### Post by skyzthelimit230 on 2011-01-26
Thanks! I'll read them over tonight!

---

### Post by srs5694 on 2011-01-26
Others are doing a good job addressing your practical needs; but you've asked a couple of questions that you or other readers may find interesting on a more theoretical level, so I'll answer them....

> **skyzthelimit230 said:**
> So,
Lets say I use GParted and delete every partition on a hypothetical drive.

Besides the obvious losing everything and having to reinstall an OS, would this delete the drive's partition table?

Selecting the partitions and deleting them one by one does not delete the partition table itself. On most disks in PCs, the partition table comes in the form of a [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) data structure, and deleting the individual partitions just sets certain records in that data structure to "0" values. The remainder of the data structure, which define it as an MBR data structure, remains intact.

That said, it *is* possible to completely destroy the MBR (or any other type of partition table) data structure. This can be done quite easily with the "dd" utility by writing all 0s to the MBR:

```

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1

```

There's seldom any need to do this, but you might want to if the MBR is badly corrupt and is causing a utility to flake out or if you want to re-use the disk in some way that doesn't involve it having an MBR.

> If so, how would I create a new partition table?

Every disk partitioning utility has the ability to create a new partition table. Sometimes this is done automatically; for instance, if you launch fdisk on a disk with no partition table and then type "w" (to save your changes), it'll write out a fresh (but empty) MBR partition table. Other times you've got to do something explicit. With GParted, for instance, you must select Device -> Create Partition Table in its menu.

Sometimes you can create a fresh partition table even if the disk currently has partitions. I believe this works in GParted as just described, for instance. In fdisk, typing "o" at the main menu creates a fresh MBR.

**Beware, though!** Although MBR is common, it's not the only type of partition table. Some, such as the [GUID Partition Table (GPT),](http://en.wikipedia.org/wiki/GUID_Partition_Table) occupy more or different sectors than does MBR. If you overwrite a bigger partition table type, such as GPT, with a smaller one, such as MBR, and if your disk utility doesn't know enough to erase all traces of the other partition table type, you'll end up with a disk that's inconsistent. This can happen if you use fdisk on a GPT disk. Thereafter, GParted (and other tools based on libparted) will flake out and tell you the disk is empty when in fact it's not. GParted does a better job of erasing old partition table data than does fdisk.

> Furthermore, is deleteing the partition table the end of that drive for good?

No. Every hard disk is just a series of sectors, numbered from 0 through some maximum value. The partition table is no different from any other data on the drive, as far as the disk itself is concerned. If you erase the partition table, you can still access the drive, and partitioning tools can create a new partition table, as just described.

It's *very* hard to physically damage a hard disk using software. In fact, I don't know of any way to do so, at least not quickly. (In principle, doing repeated and constant seeks might wear out the drive more quickly than more conventional use patterns, but I'd expect this would take days to months, or conceivably years, to damage the disk.)

---

### Post by skyzthelimit230 on 2011-01-26
Hey, thanks for the info. It was super interesting.

Another question: I have a Dell utilities partition (its only a few hundred MBs in size). Can I delete this partition as it dosen't seem to be doing anything.

(I included a snip of my partitions in an earlier post on this thread).

Furthermore, I did some reading and I'm pretty sure that it is Windows storing its MBR on the end of the disc. The reason why I'm saying this is because in the past when making space to install Ubuntu, shrinking Windows posed no problem. I think PerfectDisc would be useful in this case to move the MBR and allow me to shrink.

And, in Windows, what is the D:\Recovery partition for? I tried defragging it, but the defrag tool doesn't seem to be getting rid of the file fragments.

---

### Post by dBuster on 2011-01-26
> **skyzthelimit230 said:**
> 
Furthermore, I did some reading and I'm pretty sure that it is Windows storing its MBR on the end of the disc. The reason why I'm saying this is because in the past when making space to install Ubuntu, shrinking Windows posed no problem. I think PerfectDisc would be useful in this case to move the MBR and allow me to shrink.

And, in Windows, what is the D:\Recovery partition for? I tried defragging it, but the defrag tool doesn't seem to be getting rid of the file fragments.

PerfectDisc did the trick for me.  Moved it all out of the way.  However, I wanted to free up 90 gigs for a new partition but I was only able to get 74 for some reason and yet I had moved it all with perfectdisc.  Don't know why but it gave me more than enough room.  I have roughly 35gigs in my current /home and that is what I wanted the new partition for.  So it worked out great for me.

Next, that recovery partition that you see on the Dell computer, having worked with Dell's extensively when I worked for the state of arizona, they like to put the recovery disc image there.  If you have the ability to burn the image to disc's then do so.  I used to create images for all the pc's I handled and if I got a new model I would create one set of master recovery discs for that series and then wipe it.  Not sure if they still have the ability to burn those images anymore due to the size of the monsters that windows creates but it most definitely is something to look into.  Now if your not worried about losing the recovery disc partition then by all means.  Or check with Dell and see if they can send you replacement recovery discs, say you had a bad hdd or something like that.

Just my two cents...

This household does not use windows on a regular basis.  The only time an old laptop, and the only one yet, with windows is fired up is when I do our taxes as I have yet to find turbotax for linux or a suitable equivalent.  Otherwise there would be no windows here at all.

---

### Post by srs5694 on 2011-01-27
> **skyzthelimit230 said:**
> Another question: I have a Dell utilities partition (its only a few hundred MBs in size). Can I delete this partition as it dosen't seem to be doing anything.

Probably, but I can't make any promises. At the very least, I recommend backing up the contents of the partition for future use. It might have some tools that will prove useful in the future.

> Furthermore, I did some reading and I'm pretty sure that it is Windows storing its MBR on the end of the disc. The reason why I'm saying this is because in the past when making space to install Ubuntu, shrinking Windows posed no problem. I think PerfectDisc would be useful in this case to move the MBR and allow me to shrink.

No, the MBR is, by definition, stored on sector 0 of the disk. (See the [Wikipedia entry on MBR](http://en.wikipedia.org/wiki/Master_boot_record) for details.) Your inability to shrink the Windows partition beyond a certain point has to do with where Windows is storing certain of its system files that it marks as unmoveable, but this is done at the filesystem (NTFS) level; it has nothing to do with the MBR.

---

### Post by skyzthelimit230 on 2011-01-27
Ah, thanks for the clarification :)

---

### Post by 12apennachi on 2011-01-27
This might sound like a stupid response but I was trying to do the same thing and since the logical ubuntu partitions are "inside" the one big extended partition you have to drag over the extended before you drag the logical. Worked for me with Win7 and Ubuntu 10.04. I figured I might as well say that before you create a new partition table on your hard drive. (I did that on my brothers computer on accident and I used testdisk to recover it and he didn't even know haha)

---

### Post by irv on 2011-01-28
I dug around in some older threads I had and I found this one that really helped me resize partitions on my hard drive. It worked like a charm and I never loss any data. I think you will gain some good knowledge from reading through it.
[http://ubuntuforums.org/showthread.php?t=1595534]("http://ubuntuforums.org/showthread.php?t=1595534")

---


---
title: "Need to access files on 'swap' partition."
date: 2010-08-18
forum: New to Ubuntu
---

### Post by Zeptinune on 2010-08-18
Hey guys it's been a loong time. Having issues with ubuntu 10 at the moment. Notebook version. Installed onto a 100GB partition, and it complained about my other partition (this 60GB one with all of my important stuff on it) not being used for anything. So I made it 'linux swap' seeing as it complained about it.

Now I cant change that drive back to FAT32 in 'disk utility' I really need the files from there. When I say to  change it to FAT32 it just sits on the little mouse animation for 2 hours...

I really need my stuff back lol.
Any suggestions?

EDIT: Also on a side note my computers fan is always blasting and my laptop seems really hot all the time. I went into options and then 'appearance' but I cant turn the 'visual effects' down, it's all grayed out and it seems to be set on 'none' anyway. I have the latest drivers installed.

---

### Post by mcduck on 2010-08-18
If you have formated the partition as swap, there are no files there any more.

Swap is just an extension to RAM, for temporary storage of stuff that doesn't fit in your memory when some program requires more RAM than  what you actually have available.. It doesn't contain a file system and thus you can't mount it or read it's contents (not that reading them would even make any sense, as, like I said, there are no files on the swap partition).

If you had files on the partition, they are lost now. If you did the change recently and haven't used the system much since, you might be able to recover something using tools like testdisk or photorec, but if the sections of the disk have already been written with swap data then recovering might not be possible.

(to format the partition to some normal file system you need to make sure it's not used as swap at the moment, and that it's unmounted. After that the Disk Management will be able to format it into whatever you want. Of course this doesn't bring your files back)

edit: what comes to heat issues, it's hard to say anything for sure without seeing the system, but if you really have already installed all the correct drivers for the hardware (especially the graphics card), the only thing I can think of is to check that there isn't some process running in the background with high CPU usage. You can simply use the System Monitor app from the System/Administration -menu, or open a terminal and run "top" to see the running processes.

---

### Post by nightshade209 on 2010-08-18
I don't think you are supposed to store files 'on' a swap partition. Swap is sorta meant to be for the OS to dump stuff from the RAM to. And if I am not mistaken, did you say that u allocated 60GB for swap? You do not need to allocate that much. It is approximately supposed to be double the size of your RAM, according to [this]("https://help.ubuntu.com/8.04/switching/installing-partitioning.html").(Yes, I know it's for an older version, but I do not think this will have changed.)

Secondly, if all the visual effect options are grayed out, it means they are already disabled. So the heating problem might be due to dust accumulation or something. Make sure there is nothing obstructing the fan either.

---

### Post by Zorgoth on 2010-08-18
Ummmmmmmmmm if your reformatted the partition to swap I don't think you are getting the data back.  The installation wasn't "complaining" about unused partitions, just notifying you.  When you change the type of a partition you wipe its data.  Maybe swap isn't like that if you're very lucky, but I doubt it.  Probably it overwrote the data to be zeros or something, but I am not an expert and could be wrong.

Messing around with a partition editor when you do not know what you are doing is *not* a good idea.

If you wanted to access the data, what you should have done is something like kept the type as is, *without* formatting the drive (you can format it to the same type as well, and chosen its mount point as some directory name you like, like "/storage" or something - before you format any drives, you will get a confirmation of which you are about to format), 

Sorry...

You need to unmount the partition to change its type.  First type 

sudo swapoff <name of partition>

in the terminal, where the partition name is something like /dev/sda5 

(exactly what it is you can determine by typing 

sudo fdisk -l

in the terminal)

Also, you do not need 60 GB of swap - swap is space on the hard drive used for when you run out of RAM.  Generally it is advisable to have your swap at least as big as your RAM (so you can hibernate), but if you had 60 GB of swap space used your computer would be unusable anyway - your hard drive is probably 50-100 times slower than your RAM.

---

### Post by Zorgoth on 2010-08-18
A note about hard drive data:

when data is deleted, it is not really deleted, just marked as space that can be overwritten and can't ordinarily be read and has no path pointing to it - there are tools which may be able to find some of that if it hasn't already been overwritten.

Stop using that partition as swap (or anything else) immediately if you want to maximize the chances of getting any data off.

In theory there are still traces of your data left even after you overwrite the freed data, but the cost of recovering it is literally thousands of dollars per drive.

---

### Post by Zorgoth on 2010-08-18
Also you should note that during the installation you confirmed a message saying that all data on that partition would be lost.  You should read those bits of text in the white boxes...

---

### Post by Zeptinune on 2010-08-18
Aa christ... I didn't think it would delete the data.. gosh... Well are there any good linux programs that can recover my data then, it's all really important... I think I have 60% of it backed up but because its on a separate partition I hadn't really bothered with backing it up because I just format C:/ instead, and I don't need to touch D:/

---

### Post by clhsharky on 2010-08-18
Zeptinune

This doesn't sound good, but there should be solutions. Hopefully some experts on recovery will be able to help.

Swap partition is formated on install, so a recovery is most likely  needed.
 A bootable cd with Parted Magic and the testdisk app will do, also need enough storage for recovered files. 
All so every time swap is now used theres a chance of losing data on that partition. I would stop using that computer till files recovered.
That may not be the only way, I would wait for more opinions.

Sharky

---

### Post by Zeptinune on 2010-08-18
What a disaster lol... I thought it would just use what i wasn't using for swap and keep everything else in-tact. Umm well I searched for 'testdisk' in the software manager and installed it but I don't think I can find it anywhere... I might go to sleep and try this tomorrow, the files wont go anywhere if my computer isnt running but there is a good chance its gone, i just have a bunch of small videos to get off the drive really, the rest, all music and such is pretty much already backed up I think. At least I hope...

---


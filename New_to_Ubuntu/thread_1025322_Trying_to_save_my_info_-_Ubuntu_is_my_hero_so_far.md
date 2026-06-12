---
title: "Trying to save my info - Ubuntu is my hero so far"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Magu12 on 2008-12-30
Hello all people! and thank you in advance for helping out a newbie on ubuntu (and everything linux related actually). So my dell laptop`s hdd died, tech with new one coming tomorrow and I need to get all my files backuped ASAP. Someone suggested i download ubuntu and use the linux enviroment to backup my files. So here i am at the desktop all nice and cool and i pop in my portable hdd, and when i try to open the first volume, labeled RECOVERY, it tells me "Canno mount volume"

help?

plz?

pretty plz?

with sugar on top?

---

### Post by mikewhatever on 2008-12-30
Can you post the output of <sudo fdisk -l> command without brackets from Applicatiions->Accessories->Terminal. Is the recovery volume on the external HDD?

---

### Post by Magu12 on 2008-12-30
Hey! thnx for replying. OK here's what you asked

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1314       19131   143117308    7  HPFS/NTFS
/dev/sda4           19131       19458     2621440    f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12058f35

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS


No, the RECOVERy is in the internal HDD

---

### Post by hyper_ch on 2008-12-30
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Magu12 on 2008-12-30
Hello hyper, thnx for the advice. I guess im a bit freaked out by the deadline i have. when you refer to brackets, i kinda get what you say, however im not quite sure on where to place them since the output looks on the post pretty much like it did on the terminal. im guessing you see this kind of output all the time, mind placing a few brackets on it so i get the idea? im sorry if im a pain but like i said these are the first hours of my life with anything non-windows and im unfamiliar with the terms and proper....etiquette?

---

### Post by Big_astur on 2008-12-30
He means this:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80000000

Device Boot Start End Blocks Id System
/dev/sda1 1 8 64228+ de Dell Utility
/dev/sda2 9 1314 10485760 7 HPFS/NTFS
/dev/sda3 * 1314 19131 143117308 7 HPFS/NTFS
/dev/sda4 19131 19458 2621440 f W95 Ext'd (LBA)
/dev/sda5 19131 19458 2620416 dd Unknown

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12058f35

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 14593 117218241 7 HPFS/NTFS
```

All the text you place between [noparse]```

```[/noparse] will look like that. You can quote my post to see how it looks.

---

### Post by Magu12 on 2008-12-30
Ooooooooooooh! yeah....that makes sense...hehehehehe, some things are painfully obvious once you see the answer...... thanx guys.

By the way, i dunno if this helps but here's the error im getting:

"$MFTMirr does not match $MFT (record 0). Failed to mount '/dev/sda2': input/output error NTFS is either inconsistent, or you have hardware faults, or you havea SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows TWICE.  the useage of the /f parameter is very important! If you have a SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1).
Please see the 'dmraid' documentation for the details"

Here's the fun part....I cant access windows. its utterly destroyed

---

### Post by mikewhatever on 2008-12-30
Correct me if I'm wrong, but /dev/sda looks like your internal HDD, and the recovery partition is the Dell Utility one. Now, why would you want to access that particular partition? Do you have any personal files there?

That said, I don't think Ubuntu live cd is a good tool for the job. Had it been the problem with Windows, it should have worked, but the problem is with the HDD. Use test disk instead.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Magu12 on 2008-12-30
hey mike

Unfortunately, yes. The recovery partition for is the one where all my stuff is. i was wondering why this partition got filled so quickly, but it seems that on dell systems, all the "My documents/music/images" folders are stored in the recovery. I do have access to other 2 volumes labeled MEDIADIRECT and OS (which are already safe and sound in my portable hdd) but all the really important stuff is in RECOVERY.... nice huh?

Ill check out the link. Wish me luck

---

### Post by Magu12 on 2008-12-30
hmmm maybe its the lack of sleep, but i read the info on the link and i cannot get what to do. could you walk me through it plz?

---

### Post by mikewhatever on 2008-12-30
Get a testdisk live cd and use the program called photorec.
[TestDisk Live]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")
[http://en.wikipedia.org/wiki/PhotoRec](http://en.wikipedia.org/wiki/PhotoRec)

---

### Post by Magu12 on 2008-12-30
Well...i really don't want to jinx it but this seems to be working. Im getting most of my files back.....awesome!

still can't find my docs anywhere but i still need some more time, pics, vids and games are safe. utilities are safe and misc software is safe...

guys, i really appreciate the help, truly. My memories and me thank you from the bottom of our hearts (well, ok, MY heart, my memories' zeros and ones...hahahahaha)

As soon as I can find a couple more things and dont run into any walls ill declare this case closed (or solved, however you want to put it)

Thanks again

I really need some sleep....its been like 27 hours since i woke up....ugh

---

### Post by Magu12 on 2008-12-30
YES!!!!!

YESS!!!!


Hard to imagine that my whole life fits in a convenient portable hdd.
Thanks everyone!!


PS - How do I set this thread to SOLVED? (oh my.....I'm such a noob!)

---

### Post by mikewhatever on 2008-12-30
Take care Magu, glad it all worked.
To mark the thread as solved, click on the 'Thread Tools' link at the top of the page.

---


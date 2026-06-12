---
title: "Angry windows 7 guy wants to beat me up over hard drive"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Darkhorse85 on 2010-05-04
HI

A guy I know is going crazy because he says he lost all his information on his external hard drive (ntfs) because after he plugged it into my karmic 9.10 desktop windows 7 does not mount the device and asks "do you want to format drive". A IT guy he knows says that ubuntu changes something on the Hard Drive ( something about RAW).

**How can he get his information back?**

BTW my hard drive also does not seem to work on windows 7 (FAT32)

 help a guy out, before he loses some teeth

---

### Post by -humanaut- on 2010-05-04
I seriously doubt the data is lost missed etc... the IT guy is dead wrong. Are you sure the drive was properly unmounted? I've moved plenty of drives from different machines if you don't properly unmount it the device can lock.

---

### Post by carl4926 on 2010-05-04
Load of old codswallop.

I have external HD's of differing formats - FAT NTFS ext4.... all work perfectly between OS's

---

### Post by Arla on 2010-05-04
Garbage, garbage and garbage.

I regularly swap my NTFS drives between windows 7 and Ubuntu (9.10 and now 10.04) with no issues at all.

Couple of thoughts to try, 

1. Remount the drive to the Ubuntu machine and see if it reads it
2. Take the external drive apart, make sure all connections are good putting it back together and try again (on Ubuntu or Windows)
3. Try GParted from a live CD/installed ubuntu partition (see what it says)
4. The drive may have (unluckily) died.

---

### Post by Darkhorse85 on 2010-05-04
OK so how do you unlock it? I realize that these might be simple problems. I have been using Ubuntu almost exclusively for 6 months and when things like this pops up i still feel like a noob.

---

### Post by doas777 on 2010-05-04
plug the drive back into linux, and then unmount or even jsut shut the machine down. 
then unplug the drive and test it again on windows.

---

### Post by natravis on 2010-05-04
Plug it back into the Ubuntu machine, if it pops up and you can access files, then rt-click on the drive on the desktop, select eject drive, then unplug it and plug it into the Windows 7 box.

---

### Post by Darkhorse85 on 2010-05-04
OK cool, I will give it a try.

---

### Post by QIII on 2010-05-04
More doo-doo from the "Linux sux" crowd.

FUD is amazingly persistent.

---

### Post by Darkhorse85 on 2010-05-04
he did plug it out with out unmounting, he still says its ubuntu's fault. Can this happen in windows 7?

---

### Post by lisati on 2010-05-04
> **Darkhorse85 said:**
> he did plug it out with out unmounting, he still says its ubuntu's fault. Can this happen in windows 7?

Surely not! And it "never" happened in earlier versions either! :)

---

### Post by bigseb on 2010-05-04
> **Darkhorse85 said:**
> 
BTW my hard drive also does not seem to work on windows 7 (FAT32)


 I have Windows 7 alongside Karmic (ie on one hardrive) and Windows 7 cannot see my Karmic partition. Karmic CAN see my Windows 7 partition though. Go figure...

Also, I have many portable storage devices that are constantly travelling between Karmic, Windows 7 and XP and never experienced anything like your friend. See if he can't do a disc error check (in Windows), that usually fixes drive readablity issues.

---

### Post by philinux on 2010-05-04
> **Darkhorse85 said:**
> he did plug it out with out unmounting, he still says its ubuntu's fault. Can this happen in windows 7?

Yes same thing if not unmounted, safely remove hardware in win speak.

---

### Post by lisati on 2010-05-04
> **philinux said:**
> Yes same thing if not unmounted, safely remove hardware in win speak.

Exactly what I was thinking.

I was recently doing some work for someone, and they provided me with some pictures via USB memory stick. My machine popped up a message that suggested that they'd just pulled it out of their machines, so it was a good opportunity to tell them about using "safely remove hardware".

The danger of not properly unmounting/"safely removing" a device is that if you've copied data to it, the data might not get written properly.

---

### Post by spaik on 2010-05-04
its not Ubuntu's fault. i have a tons of flash disks and external wd hard drive and i use them with ubuntu, windows, and mac and have never experienced anything like that, but i do know some ppl who lost their data and some times the hard because they dont use safely remove, eject, etc. so its very important that you eject (in mac) unmount (in ubuntu) safely remove (windows) any usb device before plug it out.

---

### Post by oldsoundguy on 2010-05-04
having a windows drive go from NTFS to RAW format is not uncommon .. and is a bitch to fix!

First thing will be to save all the data (using a Linux live disk and another drive)

[http://www.google.com/search?q=raw+on+windows+drive&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=raw+on+windows+drive&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

Pack your lunch on this one!

(and UBUNTU did not do it .. most likely it was unplugged with the power on .. our unplugged when mounted.)

---

### Post by Sylslay on 2010-05-04
Same for win "plug the drive back into linux, and then unmount or even jsut shut the machine down" start and shout down with usb drive pluged. Had similar problem with toshiba drive and 8.04.

---

### Post by LowSky on 2010-05-04
this used to happen to me a good deal of time. People would pull a USB drive from a Win PC and it wouldn't mount onto my machine because it was Locked. It would only happen with NTFS formatted devices. FAT32 is usually fine with hot-swapping. NTFS locks up because its a horribly written journaling file system.

---

### Post by QIII on 2010-05-04
At the risk of being repetitive (I think we have all repeated this a few times ...)

The issue can be demonstrated with your friendly neighborhood iPod.  There is a good reason why the irritating "Do not unplug" message flashes incessantly on the screen until you unmount, eject or "safely remove" the device.

Plug it into a Windows machine and see if it does it.  (But be sure to "safely remove" it after the demonstration!)

---

### Post by -humanaut- on 2010-05-05
:popcorn: I don't think repeating the same thing to this guy (or gal) is getting him anywhere. Just follow the advice given on here and if his data is lost its not ubuntu's fault NTFS not real friendly but like an echo of everone else it won't just erase automagically its your friends fault for just ripping the usb cable from the computer.

---

### Post by daveironhide on 2010-05-05
if your IT guy is not sure..i can tell you one thing that..even you delete something on your drive even that is recoverble....so dont give..up....try out recovery softwares...if everything fails..
> **Darkhorse85 said:**
> HI

A guy I know is going crazy because he says he lost all his information on his external hard drive (ntfs) because after he plugged it into my karmic 9.10 desktop windows 7 does not mount the device and asks "do you want to format drive". A IT guy he knows says that ubuntu changes something on the Hard Drive ( something about RAW).

**How can he get his information back?**

BTW my hard drive also does not seem to work on windows 7 (FAT32)

 help a guy out, before he loses some teeth

---

### Post by aysiu on 2010-05-05
This is actually a quite common problem with Windows users, and most of them never use those drives with Linux:
[http://www.google.com/#hl=en&source=hp&q=windows+wants+to+reformat+usb&btnG=Google+Search&fp=c475726044d7326e](http://www.google.com/#hl=en&source=hp&q=windows+wants+to+reformat+usb&btnG=Google+Search&fp=c475726044d7326e)

I'm almost certain Ubuntu has nothing to do with the problem.

That said, you can probably get the files off that drive *using* Ubuntu (Windows will offer to reformat the drive, but Ubuntu will just mount it--go figure).

If, for some strange reason, it's been corrupted so as not to mount in Ubuntu or Windows, you can just do data recovery on it:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles](http://www.psychocats.net/ubuntucat/recoverdeletedfiles)

---

### Post by srs5694 on 2010-05-05
If you can get your hands on the drive to plug it back into an Ubuntu system, you can try a few things that will help identify the problem and/or recover the data:


[list]
[*]Type "sudo fdisk -l". Note that's a lowercase L, not a digit 1, after the dash. This will produce a listing of all the partitions (on both your internal disk and the removable disk). Pay attention to the removable disk's entry (it'll probably define just one partition). If it has a partition type of "7" (really hexadecimal 7, or 0x07; also marked as "HPFS/NTFS" in the "System" column), then the partition is properly defined and the problem most likely resides in the filesystem itself. If the partition type is anything other than 7, changing it (by launching fdisk on that specific disk without the "-l" option and using the 't' command, then saving changes with 'w') may fix the problem. If the disk has no partition(s) defined, then either it was used as a "superfloppy" with no partition or the partition table has gotten corrupted. If the latter, it may be possible to fix the problem by creating a new partition entry, but I do *not* recommend you try this until you back up the raw data (as described shortly).
[*]Use blkid on the problem partition (as in "sudo blkid /dev/sdc1" if the disk is /dev/sdc and it's the first partition on that disk). This should identify the filesystem type. If it's identified as something other than NTFS, then something very bad has happened to it.
[*]Try to mount the partition, preferably read-only, as in "sudo mount -o ro /dev/sdc1 /mnt". Note that Ubuntu may try to mount the partition when you attach the disk to the computer, so this may not be necessary. If the disk mounts, you should be able to copy the files to your own hard disk. Then you'll at least be able to copy them to another disk for transfer back to a Windows system.
[*]Before doing any more intrusive tests, you can back up the whole disk using dd, as in "sudo dd if=/dev/sdc of=backup.img" to back up /dev/sdc to backup.img. This process will take a long time, and you must have enough free space to store the entire disk -- so if it's a 20GB disk, you must have 20GB of free space. Other backup tools, such as ntfsclone, can back up using less space, but they may not work if the filesystem is damaged.
[/list]


Data recovery tools, such as those others have suggested, may help, too, but some of them can make things worse under some situations, so I strongly advise making a complete backup with dd, as just described, before using them.

If the filesystem is damaged, the solution almost certainly lies within Windows, since Linux has only very minimal tools for checking or repairing NTFS volumes. An exception might be low-level file-recovery tools such as PhotoRec, which can identify many specific file types and recover them even if the filesystem is badly damaged.

As others have suggested, it's vitally important that you unmount a filesystem before removing any external drive. This is true whether the filesystem is FAT, NTFS, HFS+, ext3fs, or anything else; and it's true under Linux, Windows, OS X, or any other OS. The Linux text-mode "umount" command (that's correct; it's got just one "n") or various GUI options in Linux, Windows, OS X, or other OSes will do this job.

---

### Post by aysiu on 2010-05-05
> **srs5694 said:**
> 
If the filesystem is damaged, the solution almost certainly lies within Windows, since Linux has only very minimal tools for checking or repairing NTFS volumes. An exception might be low-level file-recovery tools such as PhotoRec, which can identify many specific file types and recover them even if the filesystem is badly damaged. What Windows tool would you use to repair a damaged partition table? I would use GPart in Linux:
[http://www.brzitwa.de/mb/gpart/index.html](http://www.brzitwa.de/mb/gpart/index.html)

---

### Post by doas777 on 2010-05-05
> **aysiu said:**
> What Windows tool would you use to repair a damaged partition table? I would use GPart in Linux:
[http://www.brzitwa.de/mb/gpart/index.html](http://www.brzitwa.de/mb/gpart/index.html)

there are a few. I had to google them last year. none were what I would call impressive but they can handle simple partition issues. 

[http://www.google.com/search?hl=en&client=firefox-a&hs=0Pi&rls=com.ubuntu%3Aen-US%3Aofficial&q=repair+partition+table&aq=0&aqi=g10&aql=&oq=repair+partition+&gs_rfai=](http://www.google.com/search?hl=en&client=firefox-a&hs=0Pi&rls=com.ubuntu%3Aen-US%3Aofficial&q=repair+partition+table&aq=0&aqi=g10&aql=&oq=repair+partition+&gs_rfai=)

---

### Post by oldsoundguy on 2010-05-05
> **aysiu said:**
> What Windows tool would you use to repair a damaged partition table? I would use GPart in Linux:
[http://www.brzitwa.de/mb/gpart/index.html](http://www.brzitwa.de/mb/gpart/index.html)


That is what a lady friend did when her drive set itself to RAW format (this is a flaw in Windows that they have yet to address) .. used a Linux disk to recover the files and data to a separate drive .. reformatted the drive using Gpart (it does NTFS) .. put the OS back on and moved the files back .. only the programs that had a lot of .reg entries did not install correctly and had to be removed and re-installed .. but most important NO DATA was lost including all of the Intuit files that had NOT been saved to another drive as they should have been!

---

### Post by aysiu on 2010-05-05
That's great.

Just so you know, though, there is a difference between GPart and GParted.

GPart is a partition table repair program (it tries to rebuild the partition table from a corrupt one). GParted is a partition editor (it deletes, adds, or shrinks partitions).

---

### Post by Keith1212 on 2010-05-05
It's always funny to hear ppl call themselves "it guys" yet they only know how to use windows. Or someone removes a virus with a program and suddenly there an "it guy".

---

### Post by srs5694 on 2010-05-05
> **aysiu said:**
> [quote=srs5694]If the filesystem is damaged, the solution almost certainly lies within  WindowsWhat Windows tool would you use to repair a damaged partition table? I would use GPart in Linux:
[http://www.brzitwa.de/mb/gpart/index.html](http://www.brzitwa.de/mb/gpart/index.html)[/QUOTE]

Note that the part of my message you quoted specified a problem with the *filesystem,* not the partition table. Personally, I would use Linux tools to fix partition table problems, but that's because I'm more familiar with Linux tools than with Windows tools. The tools I would use to fix partition table problems are fairly low level, since I personally have a deep enough understanding of the data structures to use them. I'd use fdisk, sfdisk, gdisk, or even a hex editor to do the work. If a partition were completely lost (that is, if I didn't know where it started), I'd use testdisk to locate it. In case of some weird GPT problems, I'd modify gdisk, since I wrote it myself and if gdisk wasn't adequate as-is, I'd want to fix it so it would be adequate.

My suggestion to use Windows to fix filesystem-level problems with an NTFS volume is based on the fact that there are, AFAIK, no Linux tools that can do anything significant to fix NTFS problems. (The Linux ntfsfix program does some very basic checks and then flags the partition as being uncleanly mounted, which causes the Windows CHKDSK program to check it when Windows next accesses the disk.)

---

### Post by aysiu on 2010-05-05
Ah, I get what you're saying. Thanks for the clarification.

---

### Post by teh603 on 2010-05-05
> **aysiu said:**
> This is actually a quite common problem with Windows users, and most of them never use those drives with Linux
That explains what happened to those two laptops that I had to work on that time... Ubuntu mounted the drive with no problem, but gparted said the NTFS file system was totally hammered and needed to be repaired in windows. Which didn't work because the drive was unmountable.

Both of these were running XP, by the way.

---

### Post by oldsoundguy on 2010-05-05
back to the OP .. have re-read it .. the "IT" is AT FAULT!  It was he that plugged the drive into the Ubuntu machine, not the OP .. and it was HE that took it out without un-mounting.  So, no matter what .. the IT is a jerk and needs to go to work at McDonalds where his "expertise" will be above the average employee's!

I learned a LONG TIME AGO .. that hot swapping hard drives .. be it with the old drive caddy method or USB, is just NOT a good idea, no matter the OS and no matter WHAT the book says!.. and I do not, in any way shape or form, claim to be an IT!

---

### Post by Rasa1111 on 2010-05-05
> **oldsoundguy said:**
> back to the OP .. have re-read it .. the "IT" is AT FAULT!  It was he that plugged the drive into the Ubuntu machine, not the OP .. and it was HE that took it out without un-mounting.  So, no matter what .. the IT is a jerk and needs to go to work at McDonalds where his "expertise" will be above the average employee's!
!

 yeah seriously. 

I constantly switch my external HD's between my Ubuntu PC's.. and friends [hack] windows machines.
even windows 7. 

I never do, and never have, had any problems like this...

but then again....

I do know how to properly remove a mounted device. :lol:

 If this dude cant figure it out and wants to keep blaming Ubuntu... 
perhaps his computers should just die....
and he can go on to handling something a little "easier".....
[I know, unmounting devices properly is difficult!]  :lol:

 If he wants to 'fight' someone over his own retarded ignorance...
well, that alone speaks volumes about his person...

 and You should probably forget he exists. 
no need, no room for people like that. :KS

good luck.

and tell him to grow the f up.

---

### Post by aysiu on 2010-05-05
I know a couple of hardcore Windows power users who insist they always physically remove USB drives without safely unmounting them and have never had problems.

Nevertheless, just to be safe--whether I'm using Windows, Mac, or Linux--I always properly unmount the drive before physically removing.

Don't know if that's relevant to this specific case or not.

---

### Post by oldsoundguy on 2010-05-05
> **aysiu said:**
> I know a couple of hardcore Windows power users who insist they always physically remove USB drives without safely unmounting them and have never had problems.

Nevertheless, just to be safe--whether I'm using Windows, Mac, or Linux--I always properly unmount the drive before physically removing.

Don't know if that's relevant to this specific case or not.

After losing a boatload of music files (and having to re-do  them from vinyl via using Dart Pro in Windows) I have NEVER AGAIN hot plugged or hot swapped a HARD DRIVE .. even now with USB enclosures.   

I do, however hot swap HARDWARE all the time via USB.

And, as I said before, I am NOT an IT .. but I know better! Experience being the best teacher!

---

### Post by srs5694 on 2010-05-05
> **oldsoundguy said:**
> back to the OP .. have re-read it .. the "IT" is AT FAULT!  It was he that plugged the drive into the Ubuntu machine, not the OP .. and it was HE that took it out without un-mounting.  So, no matter what .. the IT is a jerk and needs to go to work at McDonalds where his "expertise" will be above the average employee's!

Please review the original message:

[quote=Darkhorse85]A guy I know is going crazy because he says he lost all his information on his external hard drive (ntfs) because after he plugged it into my karmic 9.10 desktop windows 7 does not mount the device and asks "do you want to format drive". A IT guy he knows says that ubuntu changes something on the Hard Drive ( something about RAW).[/quote]

So there are three people involved here:


[list]
[*]Darkhorse85 -- the Ubuntu-using original poster
[*]Guy -- the Windows-using co-worker who plugged the disk into the Ubuntu system
[*]ITGuy -- the IT person who claimed Ubuntu damaged the disk
[/list]


The reports are all second-hand, and *none of us posting here has ever laid eyes on the drive or seen solid technical data on it,* with the exception of Darkhorse85. Many people here are *assuming* that the disk was damaged by being removed from the computer without being properly unmounted. Although there's confirmation (in post #10) that the disk was removed without being unmounted, we can't know what's *really* wrong with it or what caused the damage; it could be that the improper removal was not what caused the damage. (In my experience, Windows does normally repair disks that have been improperly unmounted, so there may well be something else going on here.) Darkhorse85 is unclear about who removed the disk; he only identified the person via the pronoun "he" with no antecedent. My guess is it was Guy, not ITGuy, who removed the disk, since Darkhorse85 specified that it was Guy who inserted the disk. Many people here are jumping on ITGuy's diagnosis and casting aspersions on him for improper drive removal with insufficient evidence. We don't even know exactly what he said about the problem. (Ever played the game "Telephone?")

I recommend that posters review the evidence and *ask for more data* before drawing conclusions from insufficient data. I made my original post (#23) in an effort to draw out such data. Perhaps the suggestions made to date will yield some positive results. If not, we need more hard data. Barring more evidence against him, blaming ITGuy is a bit like accusing the spinster down the road of riding broomsticks at night.

---

### Post by QIII on 2010-05-05
srs5694:

DarkHorse85:  "A IT guy he knows says that ubuntu changes something on the Hard Drive (  something about RAW)."  Second hand.  Still FUD.

DarkHorse85:  "he did plug it out with out unmounting, he still says its ubuntu's  fault. Can this happen in windows 7?"  Second hand.  "Ubuntu's fault" is FUD.  This can happen in Windows.  Second hand or not, we can only assume that the drive was unplugged without unmounting, which does risk the symptoms described.

What most are jumping on is IT guy's misguided assessment that it's "Ubuntu's fault".

Otherwise, they are suggesting resolutions to an all too common result of removing a USB device without unmounting it.

Have they properly diagnosed?  No.  You are right.

---

### Post by srs5694 on 2010-05-05
> **QIII said:**
> DarkHorse85:  "A IT guy he knows says that ubuntu changes something on the Hard Drive (  something about RAW)."  Second hand.  Still FUD.

DarkHorse85:  "he did plug it out with out unmounting, he still says its ubuntu's  fault. Can this happen in windows 7?"  Second hand.  "Ubuntu's fault" is FUD.

These are second-hand and not even direct quotes. Without exact quotes and context, we can't know what ITGuy was suggesting. For instance, maybe his exact words were "the disk was unplugged without unmounting it from Ubuntu, so Ubuntu left it in an unstable state and it was damaged." Somebody with only moderate knowledge, or even a lot of knowledge and an equal measure of bias, could easily take this to mean "it was Ubuntu's fault" even though that wasn't what was stated and might not have been intended.

Furthermore, without knowing what ITGuy was looking at, we can't know if he has information we don't have. For instance, perhaps he found evidence of a driver bug that corrupted data; or maybe something was changed that shouldn't have been, such as the partition table. Certainly Linux *shouldn't* have been messing with the partition table, so if it was trashed, that would be evidence of it being "Ubuntu's fault," since it was last used in an Ubuntu system. (That said, a damaged partition table could also be a random hardware failure, so blaming it on Linux would be premature).

This does bring up an important empirical question: Is unplugging an external NTFS drive any more or less dangerous in Linux than in Windows? Although NTFS is NTFS in either case, the patterns of buffers and caches used by both OSes are almost certain to be different, so it's conceivable that one would be more dangerous than the other. I can't say I've ever heard of anybody doing any tests along those lines.

> This can happen in Windows.  Second hand or not, we can only assume that the drive was unplugged without unmounting, which does risk the symptoms described.

Actually, Darkhorse85 did explicitly state that the drive was unplugged without unmounting, so there's no need to assume anything on that particular score. Whether it caused the problem *in this specific case* is another matter, though.

> What most are jumping on is IT guy's misguided assessment that it's "Ubuntu's fault".

Prematurely, I think. I'm not normally one to come to the defense of anti-Linux FUD; but I  believe much of the discussion here is degenerating into equally  destructive Microsoft and corporate IT bashing, and it's not even clear that ITGuy  was dispensing FUD. Innocent until proven guilty, I say.

---

### Post by uRock on 2010-05-05
You guys argue way too much sometimes. When Darkhorse85 posts that the problem is fixed we can say, "cheers," or when he posts that the problem is still there, then we can help him diagnose it.

---

### Post by QIII on 2010-05-06
This should not devolve into Windows bashing.  I don't feel that it  has.  It has been noted that the same symptoms can arise in Windows  systems completely divorced from any contact with Linux.

My intent is not to argue, but to discuss.  So don't take me wrong.

In any case, going any further with this would probably best be left in the Community  Cafe -- and the Forum Staff may do that with this post.  We're really  not helping the OP any longer.  In fact, he seems to have lost interest.

But I think that anything possibly being given as proof that some condition might  be "Ubuntu's fault" is a hasty generalization.  At best, all that might be proven is  that a particular instance/installation of Ubuntu generated a fault  either by virtue of a fault in that particular installation or indirectly through  EBCAC.

My point is that the gross generalization that "Ubuntu does something" and "It's Ubuntu's fault", regardless of the second hand nature of what was said and the possible intent of the mysterious IT Guy, generated FUD in the OP's mind.

The same FUD swirls around among Linux users with regard to Windows.  It is no more fair in that context.

I agree that the thread was not diagnostic in general, but ruling out the possibility that the fault may have occurred due to the fact that the device was not properly unmounted would have been diagnostic.  Diagnoses are often reached by ruling out general possibilities and focusing on feedback from investigating what is left.  Your questions, had they been answered, would also have been diagnostic.

I've done a fair bit of RCA and FMEA in my life (see my profile).  Eliminating possibilities is part of gathering data and evidence.  Bridge collapses.  Look at the piers.  They're fine.  Look at the wing walls.  They're fine.  No need to to pay any more attention to those as the source of the failure.  You have ruled them out.  Piers and wing walls aren't in your 100 year fix in this case.

My advice to the OP would be two-fold, and in no particular order:  Rule out improper removal of the device as the source of the fault and use available diagnostic tools to investigate other possible sources.

Possibly more important:  Don't fall prey to FUD.

---

### Post by QIII on 2010-05-06
> **uRock said:**
> You guys argue way too much sometimes. When Darkhorse85 posts that the problem is fixed we can say, "cheers," or when he posts that the problem is still there, then we can help him diagnose it.

I never argue.  There is no point.  I am right.  Always.

(Unless, of course, you talk to my wife.)

---

### Post by Darkhorse85 on 2010-05-06
The Problem is fixed, i just plugged it in ubuntu and unmounted it and then it worked in windows 7! Thanx!

---

### Post by philinux on 2010-05-06
> **Darkhorse85 said:**
> The Problem is fixed, i just plugged it in ubuntu and unmounted it and then it worked in windows 7! Thanx!

Moral of the story = unmount or safely remove to avoid having to read through 42 posts. #-o

---

### Post by warfacegod on 2010-05-06
Real moral of the story = we're all always right, all the time, except when it comes to our wives.

...And if you have a husband, well then he's wrong.

---

### Post by coorior on 2010-05-06
Never enjoyed reading so many posts at once that much !!! Thank you for making my day !! )))

---

### Post by Linuxforall on 2010-05-06
Honestly, if someone threatens me with bodily harm over this matter, I would immediately take it up with the police and also threaten dire legal consequences, I suggest you do the same here and tell him to stop blaming Ubuntu for his ineptitude.

---

### Post by Maheriano on 2010-05-06
Same thing happened to my brother. He took one of my dad's external drives from his computer down to his own house and plugged it into his Ubuntu machine. Unplugged it, brought it back up to our parents' house, plugged it in, wouldn't work. He had to go back to his house, plug it back in, unmount it, then back to our parents' house and plug it back in. Finally worked.

---

### Post by KdotJ on 2010-05-06
> **warfacegod said:**
> Real moral of the story = we're all always right, all the time, except when it comes to our wives.

...And if you have a husband, well then he's wrong.

lol +1

---

### Post by steveneddy on 2010-05-06
> **philinux said:**
> moral of the story = **unmount or safely remove** to avoid having to read through 42 posts. #-o

+1

---

### Post by mullinsn2000 on 2010-05-06
> **philinux said:**
> Moral of the story = unmount or safely remove to avoid having to read through 42 posts. #-o
Exactly!

I am in college and I do not like wasting my ink in my printer printing up the 100's of papers I have to print so I go to Staples.  One day after returning home and putting my USB drive into my Linux machine, it would not mount.  So I did a little research and decided to try it in a Windows machine.  "Mounted" fine, I then "Safely Removed" it.  I plugged it back in a Linux machine and all was well.  Next time I went to Staples I told the guy to safely remove it and he insisted that it was a waste of time.  I went to my car, grabbed my Linux laptop and then inserted it into it.  It would not mount, so I told the guy to get his manager and they could just give me a new flash drive.  I knew that nothing was technically wrong with my drive this time, but I wanted to do something to get it into his head.  Long story, a little shorter -- He now "Safely Removes" all flash drives.

---


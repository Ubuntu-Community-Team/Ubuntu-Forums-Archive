---
title: "Checkdisk and Defrag"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by Rayve on 2009-10-19
My real question: can I do a checkdisk or defrag from Linux, though I have installed it "inside" Windows via Wubi?  Will it help?  Background info below -

This is sort of a Windows issue - I think, but I figured I'd post it here to see what you fine folks think of it.  I installed Linux 9.04 via Wubi about a month ago, and have decided to do a real dual-boot (didn't realize there was a difference, new as I am), so I've been backing up folders and such on Windows I want to keep, and things from my Wubi Linux, into my external hard drive.  All goes well.

Then I decide to defrag my Windows (at least twice, I've seen recommended) so it will hopefully play nice with gparted when it comes time for that.  First, I use my antivirus SystemSuite from vcom, but it doesn't like it and defrag errors out.  So I try it from cmd doing ```
 defrag c: -v 
``` because I like to know what stuff is doing.  It tells me I have 11% frag and 22% file frag, so yes, I should defrag.  Back in the GUI, I right-click my C: drive and choose defrag, but it keeps popping up with "Pausing for Shadow Drive" or something, a quick Google reveals it's probably my backup (I have Carbonite... bought a long subscription before deciding to go Linux /facepalm) so I pause Carbonite, still no luck.  And checkdisk won't complete.

So now it's time to boot into Windows via Safe Mode so I can get the checkdisk and defrags done and get to partitioning my system for a real Linux experience!  Only thing is... it hangs up at the Windows/System32/Drivers/Mup.sys entry in Safe Mode booting.  I can't get past it.  I don't know what the other Windows boot options are for (Debugging, etc) so I haven't tried those.  I was thinking it might be my G11 keyboard since Google reveals several things could cause the Mup.sys to hang.  If I F8 and choose Safe Mode, can I unplug my keyboard and plug it back in after I'm in Safe Mode?  I may try that next...

Thanks so much.

---

### Post by 123456789123456789123456 on 2009-10-20
ok
after you baked up what you want.
before defrag, remove wubi, and that will remove the virtual hard drive that ubuntu is installed on.  It is a file on the hard disk, that the computer treats as a fantom drive.  It is protected and more likely defrag will be unable to move it.  After that file is deleted, 9.04 Ubuntu will be gone also.  Go through and remove any temp files the system has, all junk files, you can help do this through disk clean up, option under c: properties.  there are also programs like cc cleaner that can help remove these junk files, it will free up space.  After all of this is done, defrag the hard disk, drive c:

Then go to disk management, and tell Vista to Resize c:
See how much space can be given by this process, if this process does not provide you with a satisfactory amount of space, cancel out of the resize process, Ubuntu will be able to resize the drive for you.

As for checkdisk, after you get the c: cleaned out, and WUBI removed, defrag should act normally, and Vista should operate normally.

Two ways to do a dual boot, you can get a program called EasyBCD.  This program is for Vista, and allows you to change the Vista Boot Loader file, to add entries of other Operating systems other than windows.

To use this program, boot from Ubuntu CD, after resizing, and it gets to the install process, to give you a list of what will be done, click on options, tell ubuntu to install GRUB on the partition that Ubuntu will be installed on, and not to install on MBR.  After install, the computer will boot into vista only, use EasyBCD to tell Vista that Ubuntu is installed.  Save entry, and restart the computer, Ubuntu will appear as a boot option.

Other way is to have GRUB install normally, on the MBR, this will delete Vista's Boot loader, and install GRUB in its place.  GRUB will be able to boot vista.  However there may be problems down the road, and that Vista may wont its boot loader.  It may be better to use the EasyBCD option.

---

### Post by Rayve on 2009-10-20
Sorry, I should have added: I'm running Windows XP Media Center SP2.   How do I resize with that? 

I also just thought of a possibility of why my Safe Mode and Recovery options for Windows booting won't work - I got this new 500g hard drive last year and, not understanding a thing about partitions, copied my old hard drive exactly... so the D: Recovery Partition that is labeled really doesn't exist... I think that may have messed up some stuff for Windows.

I downloaded an .iso of Ubuntu 9.04 Desktop x86 edition and have the LiveCD all ready to go. 

Thanks for your response!  Continuing to back up more files now.

---

### Post by martrn on 2009-10-20
**WUBI**
[http://wubi-installer.org/]("http://wubi-installer.org/")

If you think of a hard drive partition as something in the real world, a metaphor if you like.  Lets say a hard drive is a building, err a big building or a small building depending on the size of the hard drive.  What about partitions ???  Partitions could be just that partition walls that separating the building into separate parts each with its own front door.  Where does wubi fit into this.  Well wubi space could be a little tent made up of thin material or wig-wam with spring poles inside a building or a partition.

Now if you are following this then you will realise how flimsy the tent or wig-wam is compared to a real building or part of a building with its own front door, then you will realise how quickly the, it can fall down.

What you are experiencing here is windows (the occupants of the building or part building) pushing your 'tent' around.

I would recommend saving anything you can, if you can and putting in a real partition or hard-drive for linux.

---

### Post by Rayve on 2009-10-20
martrn,

Thank you, that's what I'm attempting to do, I just want to make sure Windows will play nice with the new partition, so I'd like to checkdisk/defrag.  Since I'm having trouble doing that through the regular Windows channels, I was wondering if there is a way to do so through Linux, since at least my Wubi Linux is running fine.

---

### Post by anewguy on 2009-10-20
First, your mup.sys problem when trying to boot in safe mode.  I found this post elsewhere on the net the explains it pretty well in layman terms.

  gosh  Guru Poster (805 Posts) Guru Poster (805 Posts)  9/6/2002 2:04:15 AM 	 mup.sys is one of the last drivers loaded in safe mode. It could be another service failing right as mup.sys loads. However usually it's your video card drivers. In safe mode xp forces the current display drivers to render in vga mode. So if your display drivers are broken, safe mode isn't happening.  Resolution:  wait 10 mins or go into recovery console and disable your display drivers. 

The mups.sys file is actually used for doing things over a network, but you get this failure even if you are not on a network - hence your video drivers.

Dave :)

---

### Post by martrn on 2009-10-20
> **Rayve said:**
> .... Since I'm having trouble doing that through the regular Windows channels, I was wondering if there is a way to do so through Linux, since at least my Wubi Linux is running fine.....

No there is not.  Webi is a file within a partition on a hard disk.  Its a bit like I mentioned above.  However it can only see its-self, it can not see what is above, so it can not see the hard drive or the partition it resides on, it can only see the file to which it belongs.   Its a bit of a catapult really, when webi ubuntu loads, it catapults itself to the webi file, ignoring everything else to where it resides.

You can partition a ntfs disk from ubuntu (or gnu/linux) but you can not de-fragment it, and in anycase wubi hooks and stops you seeing the windoze drive.  Its better to get a pen drive to install ubuntu to that than webi, because that is its-self more reliable than a file on a windows system, although a bit late now.

Windows will just seek to ignore any partition not in ntfs, so should just ignore it, just make sure windows is the first partition on the hard drive, as it windows likes to think its the only partition.

---

### Post by Rayve on 2009-10-20
> **anewguy said:**
> First, your mup.sys problem when trying to boot in safe mode.  I found this post elsewhere on the net the explains it pretty well in layman terms.

  gosh  Guru Poster (805 Posts) Guru Poster (805 Posts)  9/6/2002 2:04:15 AM      mup.sys is one of the last drivers loaded in safe mode. It could be another service failing right as mup.sys loads. However usually it's your video card drivers. In safe mode xp forces the current display drivers to render in vga mode. So if your display drivers are broken, safe mode isn't happening.  Resolution:  wait 10 mins or go into recovery console and disable your display drivers. 

The mups.sys file is actually used for doing things over a network, but you get this failure even if you are not on a network - hence your video drivers.

Dave :)

Dave,

Thank you for the reply - now if I could only get into Recovery Console... :P  It comes back with a read error and I can only Ctrl + Alt + Del to reboot once more.  I think that's due to the Recovery Partition not really existing due to a noob error on my part last year before I understood partitions, but I just created a rescue disk from my SystemSuite software that says it helps with partitions, so I'll be trying that one next.

---

### Post by Rayve on 2009-10-20
Hmm, okay.  So I backed up everything I needed to my external hard drive, uninstalled Wubi, and then inserted my Ubuntu 9.04 .iso CD and rebooted my computer.

Ubuntu came up, first I checked memory and disc to be safe, and then I chose "install".  Went through the first 3 steps, but when it came time to resize the partition, I chose 160GB of my 450G hard drive (15G used by "Windows NT/2000/XP" I think the recovery partition) and left about 280 for Windows... well, while resizing, Ubuntu said it encountered an error.  Then my only options became 'use the whole hard drive' or 'manual partition' which I don't know if I'm comfortable with.

I'm going to reboot now and see if I have a Windows left.  But I need to partition to install Ubuntu side-by-side, does anyone know of another way I can try?  Using my Rescue Disk I made earlier tonight via SystemSuite didn't let me do anything with Partiitons either, my only option was to "delete", no move/copy/resize available.

FYI, the 15G portion is FAT32 whereas the main 435GB is NFTS according to gparted.

EDIT: Well, I have Windows still.  It did a chkdsk when it booted and said something about deleting and then inserting index file from $0 of file 25, whatever that means.  But it's up as though nothing ever happened, so *whew* on that one.

Any other possibilities for resizing, or am I just looking at a complete install of Ubuntu on my entire hard drive (or another Wubi install)?

EDIT2: Downloading a LiveCD for gparted to see if that will help at all...

---

### Post by anewguy on 2009-10-20
Do you know what the error message was from the partitioner while you were trying to install Ubuntu?  Did it perhaps say something about a mount point?  

Dave :)

---

### Post by Rayve on 2009-10-20
> **anewguy said:**
> Do you know what the error message was from the partitioner while you were trying to install Ubuntu?  Did it perhaps say something about a mount point?  

Dave :)

No, it wasn't a mount point.  I don't remember exactly what is was... but, gparted worked beautifully, Windows still functions, and I'll be looking up some howto's to make sure I put my / root in the root partition I made and the /home in the larger partition.  :)

Now, how do I mark this thread solved?  Defrag and chkdsk didn't work in Windows, but I was able to use gparted to partition, so the main goal was achieved successfully.  :D

---

### Post by anewguy on 2009-10-20
> **Rayve said:**
> Now, how do I mark this thread solved?  Defrag and chkdsk didn't work in Windows, but I was able to use gparted to partition, so the main goal was achieved successfully.  :D

To mark the thread as solved, just click on "Thread Tools" and clicked "Solved".

BTW - as long as Windows seems to be functioning ok, I guess you're alright, but the defrag is really a requirement before using gparted so that no file fragments are lost by the resizing.  After a fresh install of Windows, a defrag is always a good idea because the install places files on the disk then deletes them, leaving "holes", and the disk is fragmented.

Just glad you got things going!

Dave :)

---


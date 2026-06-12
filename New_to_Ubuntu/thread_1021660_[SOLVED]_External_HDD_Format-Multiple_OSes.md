---
title: "[SOLVED] External HDD Format-Multiple OSes"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by iAtari on 2008-12-25
I've just received a new Western Digital My Book Essential 640GB External HDD. I'm not sure what format it ships with. What format, if any, can read/write on ubuntu, OS X, and windows? Do I even need to do anything to the drive?

Thanks,
-iAtari

---

### Post by ByteJuggler on 2008-12-25
I think the only filesystem that all 3 systems can read and write is FAT32.  That is however not a very good choice for a 640GB disk.  (Linux can read/write NTFS no problem, as obviously can Windows, but OS/X cant, which forces you to using FAT32.)

---

### Post by iAtari on 2008-12-25
Hmm, what about a drive compatible with linux and OS X? I can use possibly use macdrive for the windows side.

---

### Post by Kellemora on 2008-12-25
Hi iA

Any OS can read whatever format is used on the Hard Drive provided it goes through the computer it's connected to.

I prefer EXT3 because it doesn't fragment.

My current file server is EXT3 and is used by all the computers here.  I have NOT installed any software on the XP machines to read the files on the file server.  I would have to if I connected those hard drives DIRECTLY to an XP machine of course.

My neighbor lady has an older MAC laptop and wanted some of my wifes recipes.  I had to convert the specific ones she wanted to .pdf format as they were stored in a recipe program specific file format, but could be exported to .pdf files.  I also converted ALL of them to Rich Text also, since her recipe program is olde and I don't think it's made anymore.

In any case, these were .pdf files stored on an EXT3 hard drive and just by connecting to our LAN, she could download them into her own computer with no problems whatsoever.

Why do I prefer EXT3?

Simple Really!
NTFS stores files like beads on a string.  This is OK until you make a change to the file.  Or some files make changes to themselves automatically.  This immediately fragments the file as the change is stored at the END of the string of beads.
EXT3 stores files in pigeonholes.  You change a file, it's stored back in the same pigeonhole, so it don't get fragmented.

Seek and Read times on EXT3 always stay on par, whereas NTFS continually slows down and takes longer and longer to access a file that's changed.  Even defrag doesn't speed up a highly fragmented file right away, because it's still in pieces, those pieces are just made contiguous, until you make another change to the file itself with the program that created it.  Then when the creation program writes it back, it can use the space it was in unless it grows larger than that space, then once again, it gets added to the end of the string of beads.

I have a friend who has an external hard drive he carries with him that he can use on any computer.  I will see him tomorrow afternoon and will be glad to ask what file system he is using on it.  Or how he has it set up.  He fixes register hardware at grocery stores, or actually the attachments to the registers and some other stores too, but I don't know exactly what he does to them for sure.  Just know it's more software than hardware related for what he does to them.

TTUL
Gary

---

### Post by iAtari on 2008-12-26
Thanks for the info, but i've come across another jam.

I first plugged the drive into my mac, worked fine, mounted, ect.
I then plugged the drive into my linux box, transferred some files onto it, and unmounted. When i tried to mount again, the drive continued to "click", wouldn't mount.  i then unplugged the USB cable, tried again with no luck.

On OS X, I get a "unable to read volume" error, and disc utility wont format or erase, giving me an "input/output error".

Any Suggestions? Is the drive just "dead"?

Thanks,
-iAtari

---

### Post by Kellemora on 2008-12-27
Hi IAtari

You will probably have to plug it back into the MAC and then select something similar to Safely Remove Hardware as found on Windows machines.

I know if I just unplug a drive from a Windows machine, it won't read on anything else UNTIL I plug it back into the Windows machine and then click the Safely Remove Hardware button, then which piece of hardware I wish to disconnect and then wait until it says I can unplug it.

I would imagine that Mac's are roughly the same way!  You have UNMOUNT the drive before you remove it from the system!
It must write something to the drive to release it?

If that don't work, there are some codes to clear it up and make it readable again.  I don't remember them in my head and I'm not in my office to look it up right now.  But will be glad to if trying to put it back on the MAC don't work!

TTUL
Gary

---

### Post by ByteJuggler on 2008-12-27
> **iAtari said:**
> Thanks for the info, but i've come across another jam.

I first plugged the drive into my mac, worked fine, mounted, ect.
I then plugged the drive into my linux box, transferred some files onto it, and unmounted. When i tried to mount again, the drive continued to "click", wouldn't mount.  i then unplugged the USB cable, tried again with no luck.

On OS X, I get a "unable to read volume" error, and disc utility wont format or erase, giving me an "input/output error".

Any Suggestions? Is the drive just "dead"?

Thanks,
-iAtari

A drive that makes clicking noises usually indicates hardware/mechanical problems.  Unfortunately it's my guess that the drive probably just coincidentally decided to die now (or perhaps more likely it already had a problem which only manifested now you started to use it in earnest.)

---

### Post by iAtari on 2008-12-31
Thanks for the replys-

As it turns out, I returned the drive as a hardware fault, and replaced it with a OneTouch 4 750 Gig, which I partitioned into two partitions, a smaller one for time machine and a bigger one for storing regular files, both formatted in HFS+. 

And Kellemora, I do eject my drives before removing them. ;)

However, I have one more question:

After loading the drive with about 20GB of data and ejecting it on a Windows machine with MacDrive 7, I plugged the drive into my mac to mount it, but it doesn't mount. The HDD status light blinks, signaling activity, but it doesn't do anything, nor show in Disc Utility. 

5 minutes later, after being initially plugged in, the drive mounts automatically on the mac, working as normal.

Could this be the cause of the drive indexing itself, or a MacDrive issue? OS X's Spotlight indexed the drive after it was mounted, but what happened in that 5-minute period?

---

### Post by Kellemora on 2008-12-31
Hi iAtari

I move slave drives around to different machines all the time.

Every once in awhile I hit the long wait you mentioned.

Usually this only happens when connecting to a Windows Box.  How long it takes depends upon how much new stuff I've loaded onto it.
And since these are usually client image files, it can sometimes take up to 30 minutes before the drive is ready to use.

And there is always a new file folder written on the drive when it's done too.  Actually two folders, I think one is called Systems Service and the other Replace.  The one marked Replace appears to be a Restore File.  Must be some setting inside of windows somewhere that does this?

One thing I've learned is scripts don't run to move files during the night on drives I move around.  They will work Manually, but not via a schedule.  Always leaves a log report that permission was denied or Drive was not accessible.  This is not a new problem, it's been doing it for many years now.

Dig this!  I have an XP computer in the front office, and one in my accounting department.  I cannot copy the days data from the front XP computer to the back XP computer.  I always get error message, drive not found, drive not available, permission denied.  You name it!  However, I can sit down at my Ubuntu machine, mount the front office drive, mount the accounting drive and copy the files from the front office to the back office going through the Ubuntu machine, no problems, no errors.
It's not a read problem as all the computers can read the files just fine.  Just can't copy from a doze machine to a doze machine.  I've never figured out why either!  

TTUL
Gary

---


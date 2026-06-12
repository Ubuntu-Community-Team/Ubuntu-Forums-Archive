---
title: "NTFS or FAT32"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by numbness05 on 2009-07-31
I have read many threads today and still cant really get a straight answer really... I am running Ubuntu 8.10 and have an external hard that is formatted to NTFS...

I have had constant problems writing to this drive since owning it and now cant even read from it when it does bother to mount..

I am a complete novice when it comes to playing with computers so please put it as simply as you can if you can of course..

I have been told to reformat it to FAT32 would probably do me far more justice as i am constantly switching between the work PC (windows XP) and my machine (Ubuntu 8.10) and that i should have any problems reading or writing in either of them..

So my first question is (again as simply as possible) is this accurate?

2nd question is how do I go about doing this in Ubuntu?

3rd Do i need to back up my data and remove it from the drive before attempting to reformat it?

Thank you very much in advance.

Any help will be much appreciated.

---

### Post by gettinoriginal on 2009-07-31
You do not say what you have tried, but this site post #2 should help.
[http://ubuntuforums.org/showthread.php?t=479967](http://ubuntuforums.org/showthread.php?t=479967)

---

### Post by ukripper on 2009-07-31
To re-format your NTFS drive in ntfs format follow this link -
[http://maketecheasier.com/how-to-reformat-an-external-hard-drive-to-ntfs-format-in-ubuntu-hardy/2008/09/29](http://maketecheasier.com/how-to-reformat-an-external-hard-drive-to-ntfs-format-in-ubuntu-hardy/2008/09/29)

Fat32 has restriction of 4GB file size which NTFS doesn't!

---

### Post by sydbat on 2009-07-31
The most important thing to remember is - make sure the drive is properly unmounted before disconnecting. This goes for both OS's (XP and Ubuntu). 

If you just unplug the drive without unmounting, it can cause data loss and/or corruption and you will have problems accessing it with either OS.

In Ubuntu, right click the drive and choose unmount.

In XP, there should be an icon next to the clock that does the same thing, but it says something like "safe to remove hardware" or whatever.

---

### Post by pedro3005 on 2009-07-31
And I would recommend using GParted for all this partitioning/formating stuff. You can get it running 'sudo apt-get install gparted'.

---

### Post by chuckmoney on 2009-07-31
First, yes, this is accurate.

To your third question, yes, you should always back up the data on any drive before reformatting it, since a reformat wipes the drive.

To answer your second question, the most simplistic way is to press Alt-F2 and then type "gksu gparted" to run the GParted partition editor.  Then simply right click the partition and select Convert To > fat32, then click Apply.  That's it.

---

### Post by kansasnoob on 2009-07-31
As a matter of personal choice I'd keep it formatted as NTFS and install two packages, ntfsprogs and pmount. They're both in Synaptic or you can install using the following command from Terminal:

```
sudo apt-get install ntfsprogs pmount
```

Both are explained briefly in the description at Synaptic. More on ntfsprogs here:

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

---

### Post by nhasian on 2009-08-16
numbness05,

really the best filesystem depends on what other devices you will be connecting the external drive to.  If its primarly being used on linux computers, i'd go with EXT3 or EXT4.  

If you are going to be moving the drive back and forth between computers with various operating systems NTFS or FAT32

If you plan on connecting your external drive to a PS3 or Xbox360 for video or audio playback then your only choice is FAT32.

---

### Post by Johan-Steyn on 2009-08-16
Hi, 

For what it's worth, the most limiting factor of FAT32 is that the maximum file size it can handle, is 4gb.

NTFS's file size is not limited (it stores files entirely within the MFT record which extends the file's data, as its flexible allowing files to have no maximum file size).

If the file size limitation is not going to be a problem - then go for it.

Regards,

JS

---

### Post by chuckmoney on 2010-04-16
Minor correction to JS's post above.  NTFS does have a maximum per-file size, but it's 127GB.  Thus, unless it's a hard drive image file of a very big hard drive, you're fine.

But then, you should be using partimage and ext2/3/4 for disk images anyway :P

---

### Post by Calash on 2010-04-16
> **chuckmoney said:**
> Minor correction to JS's post above.  NTFS does have a maximum per-file size, but it's 127GB.  Thus, unless it's a hard drive image file of a very big hard drive, you're fine.

But then, you should be using partimage and ext2/3/4 for disk images anyway :P

I thought it was 16tb practical limit.

Here is a nice link a co-worker pointed me to a while back that details the different file systems

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

The the OP question, I have never had any issues reading/writing to NTFS volumes.  However, for portability I pick FAT32.  Nice and simple and readable on older DOS systems.

---

### Post by e4uforums on 2010-04-16
Very good advice thus far. 

To summarize:

Always be sure to properly disconnect the drive from your OS before physically removing it.

To keep it simple, if your files are smaller than 4GB, go with FAT32 - nearly everything can read FAT32 so you should never have compatibility problems.

---

### Post by srs5694 on 2010-04-16
> **Calash said:**
> for portability I pick FAT32.  Nice and simple and readable on older DOS systems.

That depends on just *how* old it is. [Here's a page](http://www.cn-dos.net/msdos71/dosfat32.htm) giving details for various DOS varieties. Of course, as a practical matter, if you're running a real DOS system on a regular basis, it's probably got something recent enough to handle it. You might have problems if you dust off an old PC AT from 1988 you find in your attic, though....

---


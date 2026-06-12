---
title: "Mount Iso Starcraft No cd"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by cerealtx on 2009-02-14
hey im trying to get SC to work, i have tried mount it to /media/ and /mnt/ installed it fine but when i try to run it, it says i need the cd, any way around this i know i have done it in the past but i can't remember how

---

### Post by blueridgedog on 2009-02-14
Are you doing this in wine?  If so, I would assign a drive letter to the mount path and tell it to configure it as a CDROM.

applications - wine - configure wine - drives tab

---

### Post by VeeDubb on 2009-03-05
Since Starcraft plays just fine in both wine and Cedega if you have a legal copy, and a legal copy is $10-$20 and readily available, what's the point?

---

### Post by handy on 2009-03-06
> **VeeDubb said:**
> Since Starcraft plays just fine in both wine and Cedega if you have a legal copy, and a legal copy is $10-$20 and readily available, what's the point?

Many people prefer not to use their optical media when playing a game.  It is far more convenient to just call the game & play it, apart from the disk being kept in better condition, which is particularly helpful when children are using them, though many adults are also quite careless when it comes to looking after optical disks.

---

### Post by VeeDubb on 2009-03-06
That's fair.  

I've just always found personally, that the monumental inconvenience of "no-cd patches" and the fact that most games are only "mostly" functional if you've used on, more than outweighs the convenience created by not needing the disk.

To each their own.

---

### Post by yther on 2009-03-06
True, but this way, you don't have to use any patches or hacks.  You mount the ISO and Wine tells the game it's a CD.  Convenient, and generally faster access than using the real CD.  :)

---

### Post by handy on 2009-03-06
> **yther said:**
> True, but this way, you don't have to use any patches or hacks.  You mount the ISO and Wine tells the game it's a CD.  Convenient, and generally faster access than using the real CD.  :)

Sounds like a winner to me. ;)

---

### Post by wlraider70 on 2009-03-20
Could someone explain the process a little more clearly to me.

I have an iso, and i know where the wine cfg is, but 

I dont know where to put the iso or how to direct wine to that iso as a cd.

---

### Post by VeeDubb on 2009-03-22
First of all, you wouldn't tell wine that the iso is a CD.  It's not quite that simple.  You will need to mount the iso into your file system.  It doesn't actually matter where, although some places make more sense than others.  I won't explain how to do this, because it's really well covered in many places on this forum.

It also doesn't really matter where the iso is stored.

Personally, I have a folder set up in my home directory called wine_iso where I store the various iso filed I want to use for wine, and a second directory called wine_iso_mount where I actually mount them.

To get wine to look at that location as a disk drive, you don't want to edit your wine config manually.  Simply go into the programs menu, click on the wine submenu, and then on "Wine configuration"

From within that program, you can easily add a second CD rom drive.  Simply tell wine that /home/you/wine_iso_mount is a cdrom.

You have to mount the iso files as the root user unless you play with permissions.  The alternative, which I would have to research how to do, would be to use a separate folder to mount each ISO you wanted to use this way, and put a line in your fstab for each one so that they would all be mounted automatically at boot.  Then you could list as many CDROM drives as you needed in the wine config.  However, I wouldn't do this, as it would be incredibly messy, and wine might choke if you tried to tell it you had 42 cd rom drives.


After reading this thread, I've started doing this with a few older games that I either don't want to dig the disks out for every time, or games that I legitimately purchased, but lost the disks.  (I have literally purchased Morrowind GOTY three times, and can't find a single set of disks, and I've never loaned them out)

---

### Post by CatKiller on 2009-03-22
From [Blizzard's help section]("http://us.blizzard.com/support/article.xml?articleId=21150"), describing the changes in StarCraft patches: > StarCraft and StarCraft: BroodWar no longer require the CD while playing the game.  To play without the CD, please follow the following instructions:

If you own only StarCraft, copy "INSTALL.EXE" from the StarCraft CD to your StarCraft folder and rename it to "StarCraft.mpq".

If you own StarCraft: Brood War, copy "INSTALL.EXE" from the StarCraft: Brood War CD to your StarCraft folder and rename it to "BroodWar.mpq".  If you wish to play the StarCraft original missions then please copy and rename the install file from the original StarCraft CD as well, as listed directly above.

So install the latest patch, copy the files across, and play. Simple.

---


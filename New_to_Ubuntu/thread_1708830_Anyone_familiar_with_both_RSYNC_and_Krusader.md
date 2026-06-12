---
title: "Anyone familiar with both RSYNC and Krusader?"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by tg3793 on 2011-03-17
*************************
* The Not-so Quick and Dirty *
*************************

After comparing the source to the destination using Krusader it shows me that all files are not synchronized except for four symlinks. [COLOR=DarkOrchid]The source is ext4 and the destination is NTFS[/COLOR]. When I view the source and destination from within nautilus everything looks the same; date, filesize, owner, icon image, everything. However Krusader still reports it as differing.

_When I compare this same source and destination pair in LuckyBackup_ (using a Dry Run) I get:

```

=====================================
execution of 1st part of task : Sync Tin and Gold ( I ) DUPLICATE, starting
Syncing : /home/scribe/Tin/I/Tim/
to : /media/SignatureMini/I/Tim/ 
 sending incremental file list
  Databases/
  Malu/Adrian/
  Personal/Proj/New.Proj/Belfry/Backup Stuff/20000523 Misc. Stuff Littering Destop/Personal/Business/Warren and Associates (Geoffrey)/Clients(Drivers and Technical)/SiS 5598 (Timothy Gott)/
   Number of files: 162563
 Number of files transferred: 0
 Total file size: 24.93G bytes
 Total transferred file size: 0 bytes
 Literal data: 0 bytes
 Matched data: 0 bytes
 File list size: 4.76M
 File list generation time: 0.001 seconds
 File list transfer time: 0.000 seconds
 Total bytes sent: 4.77M
 Total bytes received: 10.94K
  sent 4.77M bytes  received 10.94K bytes  23.63K bytes/sec
 total size is 24.93G  speedup is 5210.91 (DRY RUN)
  execution of 1st part of task : Sync Tin and Gold ( I ) DUPLICATE, finished
=====================================

```The rsync command that LuckyBackup says it's going to execute is: 
[COLOR=SeaGreen]rsync -n -h --progress --stats -r -t --modify-window=1 -l -D --update[/COLOR]

_So, when I run that rsync command I get (basically the same thing as LuckyBackup):_

```

sending incremental file list
Databases/
Malu/Adrian/
Personal/Proj/New.Proj/Belfry/Backup Stuff/20000523 Misc. Stuff Littering Destop/Personal/Business/Warren and Associates (Geoffrey)/Clients(Drivers and Technical)/SiS 5598 (Timothy Gott)/

Number of files: 162563
Number of files transferred: 0
Total file size: 24.93G bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 4.76M
File list generation time: 0.054 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 4.77M
Total bytes received: 10.94K

sent 4.77M bytes  received 10.94K bytes  21.50K bytes/sec
total size is 24.93G  speedup is 5210.91 (DRY RUN)

```I'm really not thinking this is exactly the same thing that Krusader is reporting. And if it's not then:
**a)** Which one is correct?
**b)** or what option needs to be changed so that both of them give the same output?


_Also_, when I use Krusader it sometimes works great but then other times I get some weird /unexpected results. For instance:
- Before I rebooted I was getting a string of several open folders leading to the name of a file or symlink that was supposedly different from the source to the destination. But all of the folders leading to the file had no name within Krusader. I rebooted and I that appears fine now.



********************************
* Possibly Unnecessary Extra Details *
********************************

I've been around dos and windows for about sixteen years. And now that I'm ninety-five percent in the Linux world I have to figure out what the best backup solution will be replace my old SmartSync and FreeCommander solutions that I used to use.

Dozens and Dozens of forum postings and websites on this synchronization or that synchronization. Should I use rsync, LuckyBackup, a script that uses rsync? Should I use rdiff-backup, Krusader, grsync, conduit, unison, or oh oh the list of "good" recommendations goes on.

Ok so where do I stand right now?

After looking at so many other options I've decided that I 'want' to learn the command line but figured that a GUI would help my learning curve and also allow me to explore certain options that I might not have otherwise explored. The top contenders for me seems to be (in order of contending); LuckyBackup, Krusader, rsync, gnome-commander, and midnight commander. I'm still not fully set on any one of them, but I have put several hours of time into getting a little settled with especially the first two selections.

But I seem to be getting some inconsistent results. I'm pretty sure it has to do with a combination of a couple of things:
1) I'm trying to synchronize three hundred and eighty gigs of data from a Linux partion ext4 to a NTFS external drive.
2) I might not fully grasping all of the options and rights offered by the ext4 file system.

---

### Post by mastablasta on 2011-03-17
> **tg3793 said:**
> [COLOR=darkorchid]The source is ext4 and the destination is NTFS[/COLOR]. 

Not completelly sure but i think you just answered your own question here. 
 
Different filesystem save files differently. otherwise they would be the same. even wondered why is said 650 MB data when you burned 700MB on a cd? It's because CD has a different file system than hard disk.
 
 
> 
But I seem to be getting some inconsistent results. I'm pretty sure it has to do with a combination of a couple of things:
1) I'm trying to synchronize three hundred and eighty gigs of data from a Linux partion ext4 to a NTFS external drive.
2) I might not fully grasping all of the options and rights offered by the ext4 file system.
 
What are you actually trying to do? and why are you trying to sync files on two different file systems? is NTFS parititon some comon backup disk that other people use?
 
Othwise the Linux Mint backup tool is quite nice. Still i do it the old way - manually. compress all files and then move them to another computer via SAMBA. but i think this could actually be scheduled.
 
For realy safety and redundancy you would need to set up RAID. i somehow don't have the resources to do it - hence the manual backing up to another disk and DVDs.

---

### Post by tg3793 on 2011-03-18
- Yup I was thinking that it might have something to do with the file system differences; hence my mentioning it. But I was fishing for a definitive answer. Though simple confirmation like yours is good too :-)

- Also a yes. Since we live in a Windows world I like to be able to take my disk with me from time to time and have access to all of my data even if I go to a machine with no Internet Access. Though I'm starting to think consistent backups are more important than accessibility on Windows computers. And in that case I might format my external to ext4 and just carry [Ext2Read]("https://sourceforge.net/projects/ext2read/") around with m on a USB stick. Or alternatively format it to ext3 and use [Ext2fsd.]("http://sourceforge.net/projects/ext2fsd/")

I did about two or three minutes of searches on the  Linux Mint backup tool; searched in Google and at SourceForge. A cursory view of what I found would suggest that it's not a synchronization tool that would allow me to take my external drive and simply 'go' to a new location where there is a windows machine. If this is incorrect maybe you could send me a link on  Linux Mint backup and it's features.

Thanks.

---

### Post by mastablasta on 2011-03-18
Ok perhaps Mint Backup is too simple. Well it was developed by them so that users can back up their home and system file snad install a fresh mint every time (the preferable "upgrade" way for LinuxMint).
 
What about Clonezilla?

---

### Post by tg3793 on 2011-03-19
Well, I like CloneZilla for the specific purpose of making an image of an entire drive. However it doesn't carry the 'syncronization' benefit (unless I'm incorrect) of being able to throw over just the changed files from a selected directory.

CloneZilla excels at dealing with partitions and disks. And even if I threw all of my data in one partition I would still have to contend with the desired action of only updated the files that have changed when I wanted a backup.

---

### Post by The Cog on 2011-03-19
It might be a timestamp issue. Try widening the modify window. See this extract from the rsync manual:
>        --modify-window
              When  comparing  two  timestamps, rsync treats the timestamps as being equal if they differ by no more than
              the modify-window value.  This is normally 0 (for an exact match), but you may find it useful to  set  this
              to  a  larger  value  in  some  situations.   In particular, when transferring to or from an MS Windows FAT
              filesystem (which represents times with a 2-second resolution), --modify-window=1 is useful (allowing times
              to differ by up to 1 second).



---

### Post by tg3793 on 2011-03-20
Thanks ... Getting ready to call it a night here on the other side of the globe. I'll check on that suggestions tomorrow.

Again thanks.

---

### Post by tg3793 on 2011-03-24
> **The Cog said:**
> It might be a timestamp issue. Try widening the modify window. See this extract from the rsync manual:

"widening the modify window" ? 
I was giving this some thought before I got sidetracked on a 'Unison' branch of my backup research. ... I know that both LuckyBackup and Unison are both front end GUIs for the rsync command. Are you talking about one of them? 

If not then the whole idea of widening a modify window relative to a rsync kinda throws me.

---


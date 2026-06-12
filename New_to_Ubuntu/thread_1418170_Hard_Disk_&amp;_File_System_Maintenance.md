---
title: "Hard Disk &amp; File System Maintenance"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by gallifrey on 2010-02-28
Hi, 
   I have been running Ubuntu as my sole OS for about a month now, and aside from Computer Janitor, I have found no drive/fs cleaning tools, or defragging tools. I know this isn't Windoze, but surely there must be a way of maintaining your hard disk. I mean installs/uninstalls must leave detritus, and file moving must cause SOME fragmentation. Are there any apps, systems or methods in place that provide this functionality??

Your help and suggestions would be most appreciated!

---

### Post by mikewhatever on 2010-02-28
All that you mentioned does indeed happens in Ubuntu and GNU/Linux in general, but there is nothing as advances and sophisticated to deal with these issues as in Wondows. Fragmentation is not that much of an issue in most cases, but installation leftovers is, at least as much as you pay attention to it.

---

### Post by ikt on 2010-02-28
> **gallifrey said:**
> Hi, 
I know this isn't Windoze, but surely there must be a way of maintaining your hard disk. I mean installs/uninstalls must leave detritus, and file moving must cause SOME fragmentation. Are there any apps, systems or methods in place that provide this functionality??

Your help and suggestions would be most appreciated!

It's hard for us long time windows users to move on from this constant source of time wasting.

Instead of using apt-get, using aptitude is more efficient, but besides that there's not a whole lot to do.

For me I have filled the gap by working on bugs, reporting them, triaging them, updating them, etc

> and file moving must cause SOME fragmentation

Someone recently built a disk defragmentor for linux however performance gains were found to be under or around 1%, not worth the time or power.

---

### Post by Paddy Landau on 2010-02-28
> **ikt said:**
> Someone recently built a disk defragmentor for linux...
According to what I've read, defragmenting NTFS and ext3 or ext4 doesn't do anything useful, and in fact can reduce the life of your hard drive.

Anyway, I can give you these small ideas (and really you don't need anything else, because Linux tends to clean up after itself):

[LIST]
[*]Empty your trash.
[*]Clean up old redundant packages:
[LIST=1]
[*][FONT=Courier New]sudo apt-get -y autoremove[/FONT]
[*][FONT=Courier New]sudo apt-get -y clean[/FONT]
[/LIST]
 
[*]Clean Mozilla databases
[LIST=1]
[*]If you haven't already done so, install [sqlite3]("apt:sqlite3").
[*]Close _all_ Mozilla programs that you have open (Thunderbird, Firefox, SeaMonkey, Camino, Sunbird).
[*][FONT=Courier New]sudo find /home -xdev \( -name '*.sqlite' \) -exec sqlite3 {} 'vacuum' \;[/FONT]
[/LIST]
 
[/LIST]

Unless you have a severe shortage of space, doing this once a month should more than suffice.

---

### Post by oldos2er on 2010-02-28
If you're using ext3 or ext4, you don't really need to worry about fragmentation unless or until a partition is appr. 95% full. It's a good idea to run fsck once a month or so, which the system should perform automatically.

To clean up unneeded packages, run **sudo apt-get autoremove** 
To remove cached packages, run **sudo apt-get clean**

---


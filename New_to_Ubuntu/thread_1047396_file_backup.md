---
title: "file backup"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-01-22
Is there a way to backup a directory or selection of folders/subfolders and copy them to dvds so that when the selection is larger than one dvd backup pauses and you just insert a new disk? i've dealt with progressive backup before but now that i have a new computer set up i want to have a condensed hard copy of all my media.

---

### Post by mjheagle8 on 2009-01-22
hmm. there might be, but not that i know of.  just split your files into manageable(<4.7 gb) sections and burn them to dvds.

---

### Post by Messyhair42 on 2009-01-22
that's what i've done in the past but since i've taken so many photos (and i'm really bad about moving them from camera to computer) i don't have a good point in time to go back to. i was thinking there might be a script to do something like this. if not i might have to write my own

---

### Post by Roasted on 2009-01-22
Read up on "rsync"

It's a command which does a recursive synchronizing of directories and files.

Example: On my computer, I have two 500gb hard drives. On the first, I have:

80gb Vista
1gb Swap
20gb Root
360gb Home

2nd drive is 500gb EXT3 Linux.

My drive gets mounted to a folder I created in "media" called "localbackup." 

/media/localbackup 
(keep in mind I had to grant access rights to this folder)

Then I run my script...

sudo rsync -a --progress --delete ~/ /media/localbackup

sudo = root user
rsync = synchronizing command
-a = archiving
--progress = shows in terminal what it's doing, although it goes VERY fast.
--delete = deletes any files that don't exist. *********
~/ = home directory on my main drive.
/media/localbackup = backup drive.



*********** = What I mean by this is, say I have a file called. "BlueCorvette.jpg" and it gets rsync'd to my backup drive. Then, I rename that photo to "MyBlueCorvette.jpg." Well, it will copy over MyBlueCorvette.jpg and delete BlueCorvette.jpg. That way you don't have many copies of files and folders that simply are duplicated items. The same goes for deleting items. Say you delete a folder of music on your main drive. Then, you run your script. Since the music folder no longer exists on the main drive, it gets deleted on the backup drive. Make sense? 

If you want additional help or information, I can help you best I can. Read up on this before attempting it. You can do some cool stuff with it.

---

### Post by mjheagle8 on 2009-01-22
that works for a backup drive, but not for backup discs.

---

### Post by jerome1232 on 2009-01-22
This is how i've always done this, it has disadvantages though.

Tar all the files and then split the archive into 4 GB pieces. The disadvantage is if you lose a chunk, the whole archive is doomed.

```
tar cfv backup.tar /path/to/files
split backup.tar -b 4G
```

You end up with several files titled backup.taraa backup.tarab backup.tarac and etc...

Burn each file to a separate data disc.

to put it back together you use cat

```
cat backup.tar* > backup.tar
tar xfv backup.tar /destination/folder
```

---

### Post by mjheagle8 on 2009-01-22
that would work. great idea jerome! i didnt think of that.

---


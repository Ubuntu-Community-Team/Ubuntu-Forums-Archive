---
title: "How should I partition my External USB HD?"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by xArv3nx on 2009-01-24
I'd like to use it for backups, among other things. How should I partition it and which filesystem should I use?

For example, should I just make one partition for backups (it's a 320GB HD) and format is as EXT3?

Suggestions, please!

---

### Post by blueridgedog on 2009-01-25
My personal opinion is one partition and Ext3.  You can then use rsync to backup given parts of your file system to directories you make on the external drive.

My backup drives are called Backup and Backup2 and when I want to do a backup of my documents (in a folder unimaginatively called /documents) I do the following:

```
rsync -avHn /documents/* /media/Backup2 --delete
```

The delete switch deletes the items from the backup that have been deleted from the source.

---

### Post by zephyrcat on 2009-01-25
I would caution you against using ext3 for a backup drive. If you only use Linux, go ahead and use ext3. If use other operating systems, I would advise either NTFS or FAT32. Linux supports all three.

FAT32 - 4GB size limit on each file. Works on all systems.
NTFS - Windows and most Linux distributions will deal well with it.
EXT3 - Basically only supported on Linux.

---

### Post by phantomjoker on 2009-01-25
i would say i depends entirely on what your backing up - for example if you're planning on backing up a 20Gb partition on a computer than you will need 60Gb for just that back up 
(because personally i keep 3 backups
1. an old but reliable copy - maybe when the system was first installed
2. a recent working version
3. a very recent version)

But then if your backing up lots of small files i would have a large partition just for those.

I would also always recommend ext3, the amount of problems i've encountered on ext2 and FAT32 is unbelievable.

Finally - i find it extremely useful to have a small partition with a skeleton OS on it, just encase your computer crashes or goes horribly wrong - you can still get work done, read emails etc.

Hope this helps

---

### Post by russu52 on 2009-01-25
i would rather leave it as one whole and on ntfs. folders are good enough to be organised. ntfs is read by linux, mac and windows. i have a 500gb and a 320 gb usb hdd drives, single partition each. never had trouble since

---

### Post by russu52 on 2009-01-25
phantom joker has a good point - i have xubuntu on a usb pendrive (1gb) as an emergency :)

---

### Post by blueridgedog on 2009-01-25
> **zephyrcat said:**
> I would caution you against using ext3 for a backup drive. If you only use Linux, go ahead and use ext3. If use other operating systems, I would advise either NTFS or FAT32. Linux supports all three.

FAT32 - 4GB size limit on each file. Works on all systems.
NTFS - Windows and most Linux distributions will deal well with it.
EXT3 - Basically only supported on Linux.

I would add that if you don't have ISO images of DVDs, FAT32 is great, but Linux support for NTFS is really slow.  For reliability and speed EXT3 is the best.  Did the OP indicate that they were also running another OS?

---

### Post by SunnyRabbiera on 2009-01-25
Both NTFS and ext3 seem to be good options, if you use the drive on windows you can still make it read/write your drive with this:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

I have tried it myself and it works well

---

### Post by pi.boy.travis on 2009-01-25
I would use EXT3, especially if you are only backing up linux systems.

An excellent backup program is TimeVault.  It is similar to Time Machine on Mac OS X.

You can find the .deb here:

[https://launchpad.net/timevault](https://launchpad.net/timevault)

but be warned, it is still in development. . .

---


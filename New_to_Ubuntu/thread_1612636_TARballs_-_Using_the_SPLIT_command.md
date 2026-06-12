---
title: "TARballs - Using the SPLIT command"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by mistypotato on 2010-11-03
Hi,
Today's inquiry is about TARRING files.

Here is the command I commonly use...

 sudo tar -cvpz /media/ WD 250GB | split -d -b 4500m - /home/myhome/WD250.tar.gz.

Now, considering the source is about 60GB, this command results in approximately 10 files sequentially number from 00-10, each 4.5GB, of which I plan to burn on to DVD's.

The problem lies in the fact that only the first file "00" is a true tarball.  The others are just data files so to access files on DVD 05, for example, you have to restore the ENTIRE backup just to access files on DVD 05.  If you try to open any File other than the "00" file or DVD, you get an error.

**But HERE is the question.....**

Since my GOAL ultimately is to backup to DVD....

How would I make Each of those 4.5GB files INDEPENDENT of the others so that after I burn them to DVD,  I can extract ANY file on ANY disk without having to restore the entire backup?

Cheers!

---

### Post by mistypotato on 2010-11-03
Ok,
In my searching, I found an option  -M or multi-volume backups.

This sounds EXACTLY like what I want EXCEPT.....multi volume backups cannot be compressed :confused::confused:

That kinda takes the fun out of it since I have 3 seperate 65gb backups that I need to do and they need to be written to DVD's.

Still looking.

Maybe I should be looking a 7zip or another archiving utility ?

---


---
title: "What command can I use to display everything on a drive?"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by holadebob on 2010-03-20
I have an sda5 partitioned as an ext3. It has a boot flag attached to it according to Gparted. I have only one file (4G) on the drive and no hidden files exist, but the Disk Usage Analyzer shows 1, 4.2G item under sda5 usage 100%, and it shows my folder (4.2G) with 42 items showing 100% usage. If I right click on the drive icon it shows Contents 4.0G, Volume 40G Media, Free Space 30.6, and **6.1 Used** with 30.6 Free. None of these numbers make sense to me except my folder which is about 4.2G.
Is there a disk analysis tool that will show me absolutely everything on my disk, so I might figure this difference out? I understand operating, formatting stuff that takes room, but 3 or 4 Gigs seems an awful lot. 
Thank you folks

---

### Post by kwacka on 2010-03-20
Quickest way is using command line, e.g. cd to the root of the partition and  ```
ls -alR
```

or ```
ls -alR > list.txt
``` will list all the contents of the partition as a text file (list.txt) which you can examine with text editor/word processor.

Alternatively use a graphical display such as filelight.

---

### Post by 2hot6ft2 on 2010-03-20
> **holadebob said:**
> the Disk Usage Analyzer shows
It shows how files are distributed within your file system and NOT your drive or partitions information. See this thread which will answer many of your questions.
[[SOLVED] Low Disk Space Warning, A bug? Or a limitation?]("http://ubuntuforums.org/showthread.php?t=1410114")

It should have been named File System Usage Analyzer instead of Disk Usage Analyzer
The name is misleading.

---

### Post by holadebob on 2010-03-20
Here is the text except for the contents of the Clark Family folder.
.:
total 12
drwxr-xr-x  3 clark clark 4096 2010-03-20 16:37 .
drwxr-xr-x  5 root  root  4096 2010-03-19 12:31 ..
drwxr-xr-x 43 clark clark 4096 2010-02-13 18:31 Clark Family
-rw-r--r--  1 clark clark    0 2010-03-20 16:38 list.txt

./Clark Family:
total 176

More confusion, can you tell me why there is a Clark Family listing above under the root line? I am noob, and I read those access codes somewhere but can't remember them, but don't understand why the folder seems to be in two different places.
Thanks for your help, still struggling and learnin
Bob

---

### Post by holadebob on 2010-03-20
Just deleted everything I can detect on the drive and still shows this:

.:
.
..
list.txt

and it shows it is using 2G,
Are there hidden system files that big on the drive, you think?

---

### Post by 2hot6ft2 on 2010-03-20
> **holadebob said:**
> Just deleted everything I can detect on the drive and still shows this:

.:
.
..
list.txt

and it shows it is using 2G,
Are there hidden system files that big on the drive, you think?
Maybe not as 1 file but sure there are hidden system files. Open nautilus and click on View > Show Hidden Files then you can see all the hidden files and folders when you browse to various folders.

---

### Post by holadebob on 2010-03-20
Just used nautilus to do that, but it shows no files. Is it possible to see them any other way just to verify that they are legitimately taking 2 Gigs of space?

---

### Post by 2hot6ft2 on 2010-03-20
> **holadebob said:**
> Just used nautilus to do that, but it shows no files. Is it possible to see them any other way just to verify that they are legitimately taking 2 Gigs of space?
Have you tried emptying all the trash both root and users trash? I use QuickStart to do that type of housecleaning and other routine things. You can get it here:
[http://www.quickstart.freeforums.org](http://www.quickstart.freeforums.org)
I've used it in ubuntu with no problems since it was first written by one of the forum members a couple years ago. It's still being maintained too.

I'm not aware of another way of finding hidden files but I'm sure someone does.

Besides since I bypass trash when deleting things my trash never has anything in it.

---

### Post by holadebob on 2010-03-20
yeah, I deleted both of the trashes. Sounds like it's like the sys files in that old system called windows. :) Just doesn't seem logical (to me) for those files to be that large, maybe so.....
Thanks for your help.

---

### Post by oldos2er on 2010-03-20
You can show hidden files in Nautilus with Ctrl-h, or in terminal with **ls -la**

---

### Post by holadebob on 2010-03-20
Thanks Ann, 
This is the display...

clark@office:~$ cd /media/sda5
clark@office:/media/sda5$ ls -la
total 12
drwxr-xr-x 2 clark clark 4096 2010-03-20 16:58 .
drwxr-xr-x 5 root  root  4096 2010-03-19 12:31 ..
-rw-r--r-- 1 clark clark   17 2010-03-20 16:58 list.txt
clark@office:/media/sda5$ 
Which, according to my Googling, There are only 8+ Kb of data showing on the drive.
So gparted says the drive is using 775 Mb, and right clicking properties on the drive icon says the drive is using 2 GB.
There's probably an explanation - :)

---


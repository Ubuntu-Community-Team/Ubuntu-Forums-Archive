---
title: "what is the limit on number of entries in a folder?"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Hulabear263 on 2009-08-06
Howdy!
   I have noticed that with Windows XP there is a limit on the number of items in a given folder,
usually around 22,000 or so.  Any attempt to add more items causes this message to appear:
                   'The file or *Directory* cannot be created"
Doesn't seem to matter what sort of file or folder the system is trying to create.  I first came
upon this error while making a mirror of http:/www.nasa.gov and have since encountered it
with other very large web sites.  How do the web sites get around this limitation?  I have just
subdivided the files into special subfolders by sorting the files in question by name.  The hard
drive being used is in NTFS format.  Does Ubuntu also have such a limit?  Thanks!
                  'Bye!
                       HulaBear263

---

### Post by credobyte on 2009-08-06
ext3 had 32,000 file limit in 1 directory ( tough, I'm not 100% sure about this fact ).

---

### Post by SunnyRabbiera on 2009-08-06
You must be horribly dis organized to have the need for 22,000

---

### Post by starcraft.man on 2009-08-06
EXT3 - 32000
EXT4 - 64000 and beyond

>  32,000 subdirectory limit

In ext3 the number of subdirectories that a directory can contain is limited to 32,000. This limit has been raised to 64,000 in ext4, and with the "dir_nlink" feature it can go beyond this (although it will stop increasing the link count on the parent). To allow for continued performance given the possibility of much larger directories, Htree indexes (a specialized version of a B-tree) are turned on by default in ext4. This feature is implemented in Linux kernel 2.6.23. Htree is also available in ext3 when the dir_index feature is enabled.
[Wikipedia]("http://en.wikipedia.org/wiki/Ext4#Break_32.2C000_subdirectory_limit")

You really should ever need to hit the limit though.

---

### Post by The Cog on 2009-08-06
I came close to that once. I created 10,000 tables in a MySQL database just to make sure it was possible. Since each table has an index file, that's 20,000 files. And a table bookkeeping all the other tables of course. I'll have to keep an eye on that and make sure my real application doesn't break that limit. Hmmm.

---

### Post by credobyte on 2009-08-06
Just as an update .. I successfully created 80k files in 1 directory ( ext3 file system ) :o How it's possible with 32k limit ?

---

### Post by Hulabear263 on 2009-08-06
> **SunnyRabbiera said:**
> You must be horribly dis organized to have the need for 22,000


Hello Sunny:
   Actually I am very organized.  As I stated in my initial post, this problem showed up while I was
making a mirror of a web site using Quadsucker/Web .  [http://www.nasa.gov](http://www.nasa.gov) is the parent directory
and not only contained subfolders but also more than 22,000 jpeg files; after this approximate limit
was reached no further files were written to that directory unless I moved the files to holding folders
which I manually created.  This was rather tedious, especially since I was sorting by file name and
shifting the files to the appropriate folders.  This was being done under Windows XP onto a 500 GB
external drive with a NTFS format.  Is there an automatic way around this problem with Ubuntu?
How does the parent web site manage to deal with such a huge number of files in the same directory?
(Quadsucker was instructed to reflect the directory structure of the originating web site.)  I have
since encountered the same situation with other very large web sites.
           Thanks!
               HulaBear263

---


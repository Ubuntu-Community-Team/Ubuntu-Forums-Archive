---
title: "ext2/ext3/ext4"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Happyisgood on 2009-03-16
I keep hearing mentions of these three file systems.  So far what I have interpreted is that they are all designed the exact same and the only difference between 2 and 3 is an extra port or switch or something that signals messy shutdowns.  My question is...

Can I use an ext2 driver to mount ext3 file systems?

What is ext4 and how is it different from ext3?

When 9.04 is released next month, will there be a way to switch file-systems without reformatting?

---

### Post by jerome1232 on 2009-03-16
ext3 is ext2 with a journal added. You can mount ext3 file-systems as ext2 just fine. Having a journal makes for better/faster recoveries.

As I understand it you can mount ext3 as ext4 but you can't go back to using it as ext3 and it won't have all of the benefits that a file-system that was created as ext4 will have.

---

### Post by JohnLM_the_Ghost on 2009-03-16
> **jerome1232 said:**
> ext3 is ext2 with a journal added. You can mount ext3 file-systems as ext2 just fine. Having a journal makes for better/faster recoveries.

While definitely true about the journal part... I'm not too sure you should mount ext3 as ext2, because of metadata ext3 has and ext2 don't, you might get errors if data is written and file-system is remounted as ext3 again.

However if you mount it read-only, nothing is written - so it is perfectly safe.

---

### Post by expatCM on 2009-03-17
sorry but if the difference between ext2 and ext3 is the addition of a journal, what exactly is a journal in this case (what does it look like / where is it found)?

---

### Post by Kobalt on 2009-03-17
> A journaling file system is a file system that logs changes to a journal (usually a circular log in a dedicated area) before committing them to the main file system. Such file systems are less likely to become corrupted in the event of power failure or system crash.

Check this if you want to know more about ext4 : [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by iamkrazee on 2009-03-17
ext4 is a branch of ext3. Like ntfs-3g is to the generic ntfs drier. The main problem with ext4, atleast to me, is that ext4 won't get mounted on windows with the regular ext3 driver. Also, the setup does not recognise previously existing ext4 partition. For me, this was troublesome since I wanted to mount my /home formatted in ext4.

---

### Post by Happyisgood on 2009-03-17
Thanks for that guys, I looked at that wiki article and have a random question (which will NEVER come into play... but its good to ask)  it says that ext4 is limited in size to 16TB (By any standards, a huge amount of space) while HFS+ has a maximum file size of 2 EiB (I had to look that one up, its 1 million TB's) and the NTFS file system can contain 16 EiB (minus 1 KB.)

Why does ext carry this restriction.  And who would EVER use 1 EiB of data, let alone 16?

---

### Post by bodhi.zazen on 2009-03-17
See :

[http://www.linux.com/feature/31939](http://www.linux.com/feature/31939)
    [http://www.linux.com/articles/31966](http://www.linux.com/articles/31966)

ext4 : [http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)

[http://www.ibm.com/developerworks/linux/library/l-ext4/](http://www.ibm.com/developerworks/linux/library/l-ext4/)

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by LowSky on 2009-03-17
> **Happyisgood said:**
> it says that ext4 is limited in size to 16TB 

for File size Meaning one file (like a AVI or MPEG can be as large as 16TB), currently no file I know is this big or even close. 

EXT4 can see a drive space up to 1EB Which is 100,000 GB if my math is correct
Theororetically a 64Bit processor can only see up to 16EBs of RAM so we got a way to go.

---

### Post by Happyisgood on 2009-03-17
Cool, my new goal in life shall be to create a jpg file so absurdly detailed it will be one EiB :D

---

### Post by SunnyRabbiera on 2009-03-17
On windows you can actually read/write ext3 filesystems with this: [http://www.fs-driver.org/](http://www.fs-driver.org/)

Its unknown if it works with ext4

Actually Linux has more filesystems then just ext, there is XFS, JFS, ReiserFS (though its falling out of favor as its creator is a killer)

---

### Post by jerome1232 on 2009-03-17
Actually that driver accesses ext3 volumes as ext2, not really a big deal, just something to be aware of since the file system won't be journaled while being used within windows.

---

### Post by sdennie on 2009-03-17
> **LowSky said:**
> 
EXT4 can see a drive space up to 1EB Which is 100,000 GB if my math is correct


It's actually 1,000,000,000 gigabytes.  (Gigabyte->Terabyte->Petabyte->Exabyte)

> 
Theororetically a 64Bit processor can only see up to 16EBs of RAM so we got a way to go.

Theoretically, yes.  In reality, they are actually capped around 48bits (multiple terabyte-ish).  

I haven't looked at bodhi's links but, I assume they contain all the pertinent information.  I'm not sure if they contain the fact that mounting an ext3 partition as ext4 but not enabling extents (which are not enabled by default in this case) means that the ext3 partition can later be mounted as ext3 with no problems.  You gain some performance benefits by doing this without taking the risk of going full ext4 and needing a 2.6.28 kernel to reliable read your data.

---

### Post by LowSky on 2009-03-17
> **sdennie said:**
> It's actually 1,000,000,000 gigabytes.  (Gigabyte->Terabyte->Petabyte->Exabyte)



1,000GB = 1TB
1,000,000 = 1PB
1,000,000,000 = 1EB


Oh man, my math was way off...lol

---

### Post by sdennie on 2009-03-17
> **LowSky said:**
> 1,000GB = 1TB
1,000,000 = 1PB
1,000,000,000 = 1EB


Oh man, my math was way off...lol

Describing it as, "A LOT!" is correct in either case.  ;)

---

### Post by JohnLM_the_Ghost on 2009-03-17
> **sdennie said:**
> Describing it as, "A LOT!" is correct in either case.  ;)

Anyway according to [Moore's law]("http://en.wikipedia.org/wiki/Moores_law")... we might get pretty fast there...

I still remember having less than a 1GB hard drives! (200 MB for my first rig) And it wasn't THAT long ago!

Besides we have now 50GB movies already (bluray)... :)

---

### Post by sdennie on 2009-03-17
> **JohnLM_the_Ghost said:**
> Anyway according to [Moore's law]("http://en.wikipedia.org/wiki/Moores_law")... we might get pretty fast there...

I still remember having less than a 1GB hard drives! (200 MB for my first rig) And it wasn't THAT long ago!

Besides we have now 50GB movies already (bluray)... :)

Some napkin math says that Moore's Law will mean 1EB drives should be the norm in 10 18 month cycles.  That's around 15 years.  It will be a while.  (If my math is right.  Which is probably isn't).

Edit:
Just realized that my calculations were for Petabyte drives.  Take that as you will...

---

### Post by TheUnderTaker on 2009-03-18
Ext3/4 also have HTrees (a Hashed B-tree). Htrees speed up directory searches.

---

### Post by aptdude on 2010-06-07
> **Happyisgood said:**
> Cool, my new goal in life shall be to create a jpg file so absurdly detailed it will be one EiB :D
 
If the goal is file system capacity, check out Venti, part of Plan 9:
[http://plan9.bell-labs.com/sys/doc/venti/venti.pdf](http://plan9.bell-labs.com/sys/doc/venti/venti.pdf)
 
-- cu

---


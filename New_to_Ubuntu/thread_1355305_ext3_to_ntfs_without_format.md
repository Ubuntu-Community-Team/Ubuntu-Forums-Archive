---
title: "ext3 to ntfs without format"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by baha'a on 2009-12-14
[SIZE=4]Hello!

I use Ubuntu 9.10 on my laptop and I love it!

but I tried to install it on the PC (I have the live CD) and to do so

I tried to cut a piece of a hard drive that is NTFS and is 80 GB 

but there was extremely valuable information on it, I asked the 9.10 partitioner to cut 40 GB of it

it made a 16 GB partition (that is free space) and another 64 GB that is free to.

I searched on the Internet about how to restore my files and found that I need to get the hard 

exactly as it was before partitioning (size and file system) so I managed to get it back 

one block but I want to get the file system back to NTFS (it's ext3 now)

and then I will use some restoring program on widows XP ( and I hope to get my files back) 

so I can go for another round.

thanks in advance.
[/SIZE]

---

### Post by josephellengar on 2009-12-14
I doubt that you'll have much luck with this.  Recovering information, especially from a formatted partition, is nearly impossible.

---

### Post by cartisdm on 2009-12-14
One time I made the mistake of formatting over a 40gb NTFS drive to a ext3 and was able to get a decent amount of photos and data back but it wasn't easy.  I used TestDisk - CGSecurity and worked mostly out of the terminal.

It gets the job done but don't count on too much

---

### Post by baha'a on 2009-12-14
[SIZE=3]Thanks for replying

that's extremely bad

the most annoying thing that when I told the partitioner to make a new partition 

it didn't tell me that I well lose every thing and it didn't make 40 GB

but it made about 16 that equals the size of information stored on the hard

any way sense it has formated the hard and if there is no way to change the file system

from ext3 to ntfs without formating (is there?) should I try the shot and format it (telling it to change the file system)???
[/SIZE]

---

### Post by cartisdm on 2009-12-14
No, if you want to change the file system you're going to have to format (which will cause greater data loss).  If you really want your data then try TestDisk before you format again

---

### Post by baha'a on 2009-12-14
OK

I will see what I can do and tell you what happens.

---

### Post by Thocrun on 2009-12-14
There is a linux distro that can load from ram that can change partition size (Parted Magic), but idk if it'll help.

---

### Post by presence1960 on 2009-12-14
> **baha'a said:**
> [SIZE=3]Thanks for replying

that's extremely bad
[U][B]
the most annoying thing that when I told the partitioner to make a new partition 

it didn't tell me that I well lose every thing and it didn't make 40 GB

but it made about 16 that equals the size of information stored on the hard

any way sense it has formated the hard and if there is no way to change the file system[/B][/U]

from ext3 to ntfs without formating (is there?) should I try the shot and format it (telling it to change the file system)???
[/SIZE]

Not to be a wise guy, but that is why we recommend backing up all data you don't want to lose **PRIOR** to doing any partitioning/installation operations. As a matter of good practice you should be backing up your data to an external media on a regular basis as every hard disk is one day closer to it's death.

I would not mount that device which had your data on there. I would use testdisk ASAP after reading how to use it. If you mount the device with your lost data and a write operation is performed you can kiss any slim chance that you have of recovering your data goodbye. Testdisk [here]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by Marvin666 on 2009-12-14
Every format I've done was a low level/complete, that wiped every bit of the old system. If you used a hig level/quick format, there *might* still be some recoverable data, but retrieving everything would be impossible.

---

### Post by baha'a on 2010-01-09
thank you guys so much

I'm sorry that I didn't notice that you all replied because I didn't know I could tell the form notify me about new replies.
any way my elder brother how doesn't like linux that much (because I'm always talking about it he never tried it) wanted the hard back so he formatted the hard to ntfs

after formating I tried to get anything back so I used a recovery program but after waiting for hours it told me it found about 9000 files and when I told it that I want to save them it turned out that the program was share program (it's on windows) and it asked me to register so I closed it.
then my brother wanted to use the hard so he made a folder on it and started using it
but I still got hope that there is a chance to get something back

so does any body recommend me a recovery program.

thanks and I'm so sorry that I was so annoying.

---

### Post by cartisdm on 2010-01-09
> **baha'a said:**
> 
so does any body recommend me a recovery program.

thanks and I'm so sorry that I was so annoying.

No need to worry about being annoying, feel free to ask tons of questions on the forums.

Have you had a chance to look into TestDisk? I had pretty good results with that and I actually formatted my disk twice before I realized I was using the wrong disk

---


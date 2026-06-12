---
title: "Partitions"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by rtyb on 2009-12-26
So i have this basic questions:

-Why is it recommendable (or at least i've read) to mount both / and /home on diferent partitions? Is it absolutely necessary? How much space is it recomended? Half HDD for / and half HDD for /home (of course, after subtracting the swap)?

-What's exactly ''swap''? What are the rules on setting it --i mean space-- (i read somewhere that it's the double if you have 1Gb or less of RAM and it's half if you have 2Gb or more...but i'm confused:confused:. That was a long time ago, i don't remember now:()

---

### Post by Mahngiel on 2009-12-26
In regards to the splitting of your root and home partitions, i do believe it is more towards dual linux distro booters.  If you install Ubuntu on your entire hard drive, you only get 2 partitions, the main and swap.

Swap was designed for temporary extra memory and things like hibernation/sleep-mode.  General rule of thumb is twice what you have in RAM, with a max of 1Gb. Becase really, if you had 1 Gb of RAM, you wouldn't need 2Gb of virtual RAM...

savvy?

---

### Post by rtyb on 2009-12-26
Mmm...

Thanks for clearing my swap partition doubts.

but
on the / and /home side...

I've seen guides ([http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html](http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html)- although it's a UNR guide, i suppose it's recomended for any Ubuntu installation...isn't it?)

I don't dual boot distros.

PS: savvy? (yes, i know what it means) why savvy? who?

---

### Post by Radioman991 on 2009-12-26
My 0.02

Regarding separating the home and root partitions, is it necessary, no.

However, if you customize your desktop with certain colors, themes, etc., should you hose your install, or update your distro from a CD, you can do that without clobbering your data in /home.  Speaking as one who HAS hosed his system several dozen times, it beats having to set things back up the way you like.

The above should not be misconstrued as an excuse for not backing up, however. 

Happy Holidays.

---

### Post by jim-fwb on 2009-12-26
> **rtyb said:**
> So i have this basic questions:

-Why is it recommendable (or at least i've read) to mount both / and /home on diferent partitions? Is it absolutely necessary? How much space is it recomended? Half HDD for / and half HDD for /home (of course, after subtracting the swap)?

-What's exactly ''swap''? What are the rules on setting it --i mean space-- (i read somewhere that it's the double if you have 1Gb or less of RAM and it's half if you have 2Gb or more...but i'm confused:confused:. That was a long time ago, i don't remember now:()

I'm not a guru, but / has system files, the kernel, binaries, configuration files (under /etc) and other things. /home has our data files, e-mail, text documents, spreadsheets, music ... whatever.  Also some hidden files.  If /home is a separate partition it is relatively easy to upgrade the whole system, without having to reinstall all our data files.  --Even so they should be backed up anyway--

Swap is a place for the system to store data short term, rather than keep it in RAM.  No swap tends to be slooooooow for intensive use as the o/s has to read back & forth on the disk.  Swap is usually set at 2-3X RAM up to .... maybe 3GB, then less.  My other box had 4GB & never swaps even with BOINC apps running.  This one has 512MB, about 1.5GB swap which is not being used as I type this.  

More on linux directory structure: [http://www.ahinc.com/linux101/structure.htm]("http://www.ahinc.com/linux101/structure.htm")

and elsewhere.

---

### Post by Chris Edgell on 2009-12-26
This may or may not  pertain, if it doesn't, please let me know.  I have run across this description of partitions written by JKyleOKC:  

"Think of your hard drive as a big box that has a number of smaller boxes in it (the partitions). Its name is "sda" and the file system addresses it as "/dev/sda" without a number. The partitions are numbered: sda1 and so on, and addressed as "/dev/sda1" et cetera.

The letters (a, b, c, d) are assigned according to the connectors on the motherboard and the numbers according to the sequence of entries in the drive's partition table (an area at the start of the drive that tells where the data is located). This table has room for only four entries, which will be sda1 through sda4. To get more partitions, one of the four has to be an "extended" partition, which is another box full of partitions such as your sda5, 6, 7, and 8. You don't need to worry about these because the partition manager will take care of the details.

To access the contents of a partition, it has to be mounted. The file manager of the live CD normally does this for you, so that you can click on the partition's icon and see the list of directories it contains. One of them will be "home" and inside that directory will be at least one more, bearing your user name. That inner directory is the one you want to back up.

If the file manager does not show you icons for the partitions, you'll need to "mount" them to gain access. However let's not try to cross that bridge until it becomes necessary, since it can be a bit confusing at first! Tools are available to simplify it, fortunately.

With a little experience you'll find this stuff much easier to get along with; it's all pretty logical, just different from the systems that you're used to!"

Do you like reading this, or is it stuff anyone already knows?

---

### Post by rtyb on 2009-12-26
Thank you guys

You gave me to much information, i just wanted to be sure, i'm not a newbie.

Anyway

Real thanks!:P

lol:lolflag:

PS: Chris edgel....indeed, i enjoy that kind of reading =D

---

### Post by charlier653 on 2009-12-26
Yes, Thanks Chris!

---

### Post by Chris Edgell on 2009-12-27
Since two of you liked the way that man writes -- so smart, so clear, let me tell you where he wrote it, in case you want to follow up.  I gave you his name, here's the thread: 
     [http://ubuntuforums.org/showthread.php?t=1361193&page=4](http://ubuntuforums.org/showthread.php?t=1361193&page=4)

---

### Post by bodhi.zazen on 2009-12-27
Partitioning is more an art then anything else =)

First , for the majority of users, there is nothing wrong with the default partitioningg scheme (2 partitions, root and swap).

There are 2 major advantages of using multiple partitions.

1. Keep your data separate from your OS. This works on any OS. You can use a separate /home partition or a /data partition, the idea is you can reinstall your OS without losing your personal data.

2. Security. You can use different options in different partitions such as noexec or nosuid.

The security issues are fairly minor, IMO,  see :

See: 

[http://www.debian.org/doc/manuals/securing-debian-howto/ch3.en.html#s3.2](http://www.debian.org/doc/manuals/securing-debian-howto/ch3.en.html#s3.2)

And tip #13 on this page:

[http://www.cyberciti.biz/tips/linux-security.html](http://www.cyberciti.biz/tips/linux-security.html)

A third tweak you can do is to load some parts of your system into RAM. This can improve performance, and some people load large parts of /usr into RAM.

As an example:

[http://www.brighthub.com/computing/linux/articles/9170.aspx](http://www.brighthub.com/computing/linux/articles/9170.aspx)

There are other example if you google search.

This tweak may make a difference on some systems, and I would advise it on a netbook.

---

### Post by Chris Edgell on 2009-12-27
Hi bodhi.zazen,

Please tell me how did YOU like the post I quoted (#6)?  Does it fit with what you are saying in YOUR post?

What I'm really asking is: do you think this participation of mine, in this thread does more harm than good?

Directly to the point, is it bad to quote somebody else's troubles, as if it might be a solution to this persons problems?

Thank you for your opinion.

---


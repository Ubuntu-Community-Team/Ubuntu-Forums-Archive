---
title: "Can't open external HDD"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Marcogeek on 2011-03-02
Hello everyone!

I am new to this forum and also Linux. As you may know I can't open my external HDD. I have 2 of them (one is 1TB and the other is 1,5TB) but the 1TB works perfectly fine. When I try to open the 1,5TB one, this happens:

Error mounting: mount exited with exit code 12: Failed to read last sector (2930275119): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdd1': Invalid argument
The device '/dev/sdd1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

I have already asked my friend about this (he is a Linux g33k) but he doesn't have a clue.

Please help!

---

### Post by Chemtox on 2011-03-02
Hi Marco,

welcome to the forum, and to the wonderful world of Linux, where you will never get bored: solving small problems, or creating some of your own!  (but it's all worth it for the freedom and the power you get, and if you like technical challenges ;) ).

You're well in your way to become a proficient user, if you're already asking questions in the right place, and this is the right place to ask anything about Linux and Ubuntu, though very technical questions may not find a good answer...

But before you ask for a fish, to your friends or to your fellow Internet geeks, you should try fishing yourself!  99% of the time, someone already asked (and solved) the problem you just found, so all you have to do is search for it (here's a very useful [cheat sheet]("http://xkcd.com/627/") ;) ); and your problem seems to be in the 99%.

So what you want to do, is to search the main error message of your problem, removing any variable information from it, like that sector number --or dates, time, your username, your filenames, since those change for every user.  So we Google for ["Error mounting: mount exited with exit code 12: Failed to read last sector" "Invalid argument"]("http://www.google.com/search?q=%22Error%20mounting%3A%20mount%20exited%20with%20exit%20code%2012%3A%20Failed%20to%20read%20last%20sector%22%20%22Invalid%20argument%22") and voila, there you have it, plenty of fish (many of them in this same forum, so searching here would also have worked).

Now you have to look in these results for the ones with many similarities with your own situation (I see many reports for 1.5 TiB drives, most of them Western Digital), since there may be different causes for the same error (as your error message makes very clear).  That means that sometimes you will chase fish in circles, and you will find that many of them are no good for you; but if you keep trying, you will eventually succeed (well, 99% of the time ;) ). 

In short:  always search first!  and then, search again!  Learning to find things and to quickly filter the good from the bad ones is a very helpful skill (not just for Linux, not just for computers, for anything!), but requires practice.  When you have exhausted Google, *then* you should ask for help.  You also need to learn to ask for help: your question is lacking all the basic information about your hard drive (like the brand, the number and type of partitions on it, etc.) We will lend you a hand, but not make your whole homework!  (ok, except perhaps this time: [this fish]("http://www.linuxquestions.org/questions/linux-hardware-18/cant-mount-western-digital-elements-2tb-external-hard-drive-830807/") looks like the best bet for you ;) ).

Word of warning: I should not need to tell you this, but of course, playing with your hard drive's partitions may (and eventually will) lead to losing your data, by your own fault or a program's.  So be sure you have a backup, or that you don't mind losing your files, before you play around.

Sre&#269;no!

---


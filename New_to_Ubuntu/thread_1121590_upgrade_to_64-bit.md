---
title: "upgrade to 64-bit?"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by eddski on 2009-04-10
I want to try the 64-bit version, but I want to know if I can keep my old settings and folders? I know my system can handle the 64, and I just want to try it for the speed. Also, will Ihave any driver problems?

---

### Post by halitech on 2009-04-10
You can't "upgrade" from 32bit to 64bit, you have to do a complete reinstall. You could set up a dual boot with both versions if you want to try it or pick up a new drive and install the 64bit version there.

---

### Post by Joeb454 on 2009-04-10
If you have a separate home folder, or a backup of your home folder, then yes you can keep the same settings by keeping /home as it is.

And you shouldn't have any driver problems, though I don't know without knowing what hardware you have

---

### Post by gn2 on 2009-04-10
If you don't have a separate /home partition it can be tricky though.

One method which I have seen suggested elsewhere is to boot into a Live CD, delete the contents of / apart from /home then copy the contents of your user's home folder to / then re-size the partition down to leave room for a new /

During the installation of the new 64-bit, choose manual partitioning, retain the existing / partition but mount it as /home and create a new / partition. Use the same username as you had before.

---

### Post by Sef on 2009-04-10
> ...I just want to try it for the speed. Also, will Ihave any driver problems?

You will not see a lot of difference in speed, unless you are doing something that is CPU intensive, e.g., video editing, downloading pictures from sd card, etc.  

If the drivers work for 32-bit, then they should work for 64-bit.   Most companies have support for both.

---

### Post by LowSky on 2009-04-10
going to 64Bit isn't really about speed, but about the use of more memory. If your machine has 4GB of RAM or more than using 64Bit is the best option for RAM usage. Otherwise there really is no point in changing.

---

### Post by Paqman on 2009-04-10
> **LowSky said:**
> Otherwise there really is no point in changing.

I wouldn't bother reinstalling if you weren't going to anyway, but i'd say the flipside of the argument is that there's no longer any point to throttle your machine down to 32-bit, even if it only makes a difference on 10% of what you do with the machine.

Personally I do a lot of re-encoding video (I put TV and web shows on my Zen and watch them while commuting) and you definitely notice the speed on tasks like that.

---

### Post by eddski on 2009-04-10
Yes, I have 4GB ram, and I also /home, /usr, /, /tmp, /var, /boot on separate partitions. Now if I want to keep my settings, do I just not format /home, if that is correct, then just reuse the same user name? Would there be anything else I would need to do?

---

### Post by egalvan on 2009-04-10
> **LowSky said:**
> 64Bit isn't about speed, but  the use of more memory.
 If your machine has 4GB of RAM or more** then using 64Bit is the best option for RAM usage.** Otherwise there really is no point in changing.

Ubuntu's  32bit SERVER kernel sees 64GB of RAM just fine on most fairly modern mobo's (PAE capable)

There are ways of using the server kernel on an existing install...
I just don't have the forum post links handy...

\

---


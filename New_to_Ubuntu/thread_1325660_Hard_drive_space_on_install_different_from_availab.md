---
title: "Hard drive space on install different from available"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by urdrwho on 2009-11-13
I installed with the "install as a windows application" when I installed ubuntu.  I also picked 20 gigs of hard drive space.  Ubuntu is installed on an external hard drive attached to my laptop.  Works fine.

The only thing is that I don't think it gave me 20 gigs of space on the external where the root resides.  I only see about 3.5 gigs of space and I need more space.

The other night a pop up came on showing different partitions, it was in color and I think gave options to increase space.

I didn't have time then to think, read and consider what to do and closed the pop-up.  I have time now to do it but don't know how to get that colorful chart to pop up.

Hm?  When I look at the Sys Mon file systems this is what it reads:

/dev/loop0 - 3.8 gigs total        - 2.9 gigavailable     - 21% used
/dev/loop1/home - 3.8 gigs total   - 377.6 mb available   - 89% used
/dev/sdb1/host - 189.9 gigs total  - 102.7 gig available  - 45% used
/dev/loop2/usr  - 3.8 gigs total   -1.4 gigs available    - 61% used

I can't remmeber if the total size of the external is 150 gig or 200 gig. Why am I running so low on HD resources and I have just started using Ubuntu.  I have no space to move things to my documents.

In windows I would understand Sys Mon stats. 

Has Ubuntu created 4 different partitions, is that what I am reading?

Any ideas?

---

### Post by Paqman on 2009-11-14
It does look like the installer has set you up with a really small system.

Luckily there is an app which can resize systems like yours that were installed with Wubi. It's called [LVPM]("http://lubi.sourceforge.net/lvpm.html"). You'll want to boot up into Windows, make sure there's plenty of space and defrag the drive.

---

### Post by urdrwho on 2009-11-14
I looked at the LVPM app but I stopped when it reached a point that was not clear, such as was it partitioning the C drive (main laptop) or the F drive (external).

I would really like to know why it never allocated the correct space during the install.  I un-installed and re-installed.  Both times it never allocated the correct amount.

 > **Paqman said:**
> It does look like the installer has set you up with a really small system.

Luckily there is an app which can resize systems like yours that were installed with Wubi. It's called [LVPM]("http://lubi.sourceforge.net/lvpm.html"). You'll want to boot up into Windows, make sure there's plenty of space and defrag the drive.

---

### Post by Paqman on 2009-11-14
You don't want to partition anything with LVPM, you just want to use it to expand your virtual partition.

---

### Post by urdrwho on 2009-11-14
I tried but it doesn't give me the choice to resize home.  I only have the choice to resize root.

> **Paqman said:**
> You don't want to partition anything with LVPM, you just want to use it to expand your virtual partition.

---

### Post by Paqman on 2009-11-15
Resizing root would be a good idea, it contains all sorts of things that get filled up as the computer is used, like your APT cache. It's also where big fat temporary files that get created when you're doing something like authoring a DVD.

---


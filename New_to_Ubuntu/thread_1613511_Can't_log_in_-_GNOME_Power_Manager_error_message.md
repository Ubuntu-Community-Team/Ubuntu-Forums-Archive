---
title: "Can't log in - GNOME Power Manager error message"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by Bearly Able on 2010-11-04
I had no problems with my computer yesterday, but when I tried to start up today, I got as far as the log in screen, and a message stating "Install Problem!  The configuration defaults for GNOME Power Manager have not been installed correctly."

I've searched the forums, and all the advice seems to be that this error occurs with a lack of disc space, and I've tried various suggested solutions without success.  I can access the drive using a Live CD, and under "Properties" it shows that there are however many items, totalling 5.3GB, which sounds about right.  However, it also reports that the total capacity of the drive is 141GB, of which 141GB has been used, which can't possibly be right.

We suffered a series of power cuts last week, which didn't seem to have any ill effects at the time, but I'm wondering if the file system has become corrupted?  I don't know how to check for this or what to do next, and I'd be most grateful for any assistance.

Thanks in advance.

Lesley

---

### Post by oneNF on 2010-11-04
Hi just a couple, of thoughts. When I have a possible disk issue i always look at it using Gparted from a live cd to see if there is an obvious issue.  If you expect the disk to have 5.3gb but is showing full when mounted in gparted something has gone wrong and you may have to look at it using rescue disk live cd or similar [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Cheers all the best

---

### Post by Bearly Able on 2010-11-05
Thanks, oneNF.  I've tried GParted from a live CD, and it reports much the same thing.  i.e. /dev/sdb1 ext3 size 143.26GiB used 137.98GiB unused 5.28GiB.  This leaves me just where I was before, with no idea what to do about it.  I appreciate the link to System Rescue CD, but I don't know where to start with it.

I have all my data backed up, so as a last resort I could do a fresh install.  I also have the option to upgrade to 10.10 via the terminal, but I think trying that might just make matters worse.

Please can somebody advise me of the best route from here?

Thanks

---

### Post by Zzl1xndd on 2010-11-05
If you had been thinking of Upgrading anyway and everything is backed up I would probably just do a clean install. 

Less hassle and its always nice to have clean start of the OS.

Oh and :KS for making regular back ups.

---

### Post by Bearly Able on 2010-11-05
Thanks, tweakedenigma.  I'll probably end up taking your advice and doing a fresh install.  It just seems like a lot of hassle, trying to get everything set up again the way I had it.

For some unknown reason I've just been able to log in to the system for the first time in two days.  I don't know why - I haven't done anything recently to change it.

Running GParted from here shows the size of the drive as 143.26GiB, with 133.75GiB used and 9.51GiB unused, which still can't be right.  However, when I c;osed GParted, I got a warning message telling me I have only 1.8GB free space.

The Disc Usage Analyzer says I have a total filesystem capacity of 142.9GB, of which 137.9GB is used.  However, looking at the analysis, it shows / as 100% full at 10.9GB (7.1GB of which is home).  Where has the rest of the disc space gone, and is there any way to recover?

Thanks again.

---

### Post by Bearly Able on 2010-11-06
Thanks to those who replied.  I've now done a fresh install of 10.10 and everything seems to be fine.

---


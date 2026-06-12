---
title: "How can I go BACK from Ubuntu 10.10 to Ubuntu 10.04?"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by XSE256 on 2010-12-02
Okay.
So about 3 months ago after being absolutely sick of windows and all the crap I had to put up with it, I switched to Ubuntu 10.04.

Well, when 10.10 Maverick came out I jumped on the boat. In all honesty, installing it was annoying, and it is as bad as windows xp was for me.

The wireless takes forever to find my wifi. When I am on a page with alot of javascript, flashplayer or anything with video or animations, the screen darkens (as I know it will do to free up processor space to prevent a freeze or crash). The problem is it NEVER fixes itself unless i either cut off my internet connection or struggle to un jam it. When I do I have to disable ALL plugins except for the video I am trying to watch.

Daily it crashes. Multiple times.
It freezes. The screen goes black. Terminal text appears saing several things such are not working, have shut down, and a message that says "we cant find the daemon".

Also, I installed it via auto updates by turning on the LTS updates.
I am also dual booting on an 80 gig hard drive with windows XP.
60 gigs for Ubuntu, 20 gigs for windoze.

When I installed ubuntu 10.04, the bootup screen gave me these options to select in a DOS-like screen as follows:

Ubuntu (string of numbers) -24
Unbuntu (string of numbers) -24 [RECOVERY MODE]
Memory check
Microsoft Windows XP Professional..


After the Ubuntu 10.10 install, the boot screen read this:

Ubuntu (string of numbers) -34
Unbuntu (string of numbers) -34 [RECOVERY MODE]
Ubuntu (string of numbers) -36
Ubuntu(string of numbers) -36 [RECOVERY MODE]
Memory check
Microsoft Windows XP Professional.

It didnt seem natural. It felt like 10.04 was there running in the background.

I know there are all these things I cant do to make 10.10 run smoother but honestly I want to reinstall 10.04, I have the disk to do so.

I want to completely get rid of 10.10 and go back to 10.04 and still keep what is on my harddrive.

I also NEED windoze to stay intact. as suckish as that sounds I still have alot of tools I need that only work on windows (photoshop...).
Plus, my school's computers do not read openoffice, so I have to have the MS Office suite.
Yes I know Ive saved everything in the .doc and microsoft formats but the security at our school prevents the use of files made in openoffice or anything like that.
It's stupid.
10.04 worked PERFECTLY. 10.10 (in my opinion) sucks at the moment.

So how can I fix the problem so that I can have 10.04 with my files still on it, and also keep windows intact.

I am knowledgeable with a computer, Im just not sure how to go about this.

apologies on the length and newbness

---

### Post by TBABill on 2010-12-02
Ok, I'll try to answer some of this. That "string of numbers"  you saw was just the kernel version. It was probably 2.6.32-xxx in 10.04 and 2.6.35-xxx in 10.10. When you have more than 1 entry it's because the kernel has been updated so Grub shows you old and new for you to select from to boot into. That way if a new one does not work you can just restart and select the older one.

Second, you cannot just install and "save your files" on it. You must copy them to another drive (thumb drive, CD, DVD, external HDD) first. I'm only speaking of Ubuntu here and you don't have to do anything to Windows as long as you do NOT format/install on that partition.

you need to look at your partitions and know which partition has your current Ubuntu install on it. You can find out using Systam>>Disk Utility. Click on the partition and see below the diagram which partition it is on. Should be /dev/sda with a number on the end. That's key....make sure you reinstall to THAT partition when you reinstall. Just go through the install process, select that partition, mark it for formatting and mount point as / (root). Then just do what you did before.

Good luck!

---

### Post by merches on 2012-08-08
> **XSE256 said:**
> Okay.
So about 3 months ago after being absolutely sick of windows and all the crap I had to put up with it, I switched to Ubuntu 10.04.

Well, when 10.10 Maverick came out I jumped on the boat. In all honesty, installing it was annoying, and it is as bad as windows xp was for me.

The wireless takes forever to find my wifi. When I am on a page with alot of javascript, flashplayer or anything with video or animations, the screen darkens (as I know it will do to free up processor space to prevent a freeze or crash). The problem is it NEVER fixes itself unless i either cut off my internet connection or struggle to un jam it. When I do I have to disable ALL plugins except for the video I am trying to watch.

Daily it crashes. Multiple times.
It freezes. The screen goes black. Terminal text appears saing several things such are not working, have shut down, and a message that says "we cant find the daemon".

Also, I installed it via auto updates by turning on the LTS updates.
I am also dual booting on an 80 gig hard drive with windows XP.
60 gigs for Ubuntu, 20 gigs for windoze.

When I installed ubuntu 10.04, the bootup screen gave me these options to select in a DOS-like screen as follows:

Ubuntu (string of numbers) -24
Unbuntu (string of numbers) -24 [RECOVERY MODE]
Memory check
Microsoft Windows XP Professional..


After the Ubuntu 10.10 install, the boot screen read this:

Ubuntu (string of numbers) -34
Unbuntu (string of numbers) -34 [RECOVERY MODE]
Ubuntu (string of numbers) -36
Ubuntu(string of numbers) -36 [RECOVERY MODE]
Memory check
Microsoft Windows XP Professional.

It didnt seem natural. It felt like 10.04 was there running in the background.

I know there are all these things I cant do to make 10.10 run smoother but honestly I want to reinstall 10.04, I have the disk to do so.

I want to completely get rid of 10.10 and go back to 10.04 and still keep what is on my harddrive.

I also NEED windoze to stay intact. as suckish as that sounds I still have alot of tools I need that only work on windows (photoshop...).
Plus, my school's computers do not read openoffice, so I have to have the MS Office suite.
Yes I know Ive saved everything in the .doc and microsoft formats but the security at our school prevents the use of files made in openoffice or anything like that.
It's stupid.
10.04 worked PERFECTLY. 10.10 (in my opinion) sucks at the moment.

So how can I fix the problem so that I can have 10.04 with my files still on it, and also keep windows intact.

I am knowledgeable with a computer, Im just not sure how to go about this.

apologies on the length and newbness

==========================================================
I fully agree with you! It was my unlucky day when I installed Ubuntu 10.10 !

---

### Post by drs305 on 2012-08-08
Old thread - closed. Readers wishing to express their views may do so in Testamonials.

---


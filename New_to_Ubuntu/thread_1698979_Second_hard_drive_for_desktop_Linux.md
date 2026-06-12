---
title: "Second hard drive for desktop Linux?"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-03-03
Does anyone have any thoughts about having a second hard drive in your desktop computer?

I have heard that a second hard drive could be used for the "/home" directory/partition?
I don't fully understand the Linux file structure yet.

"/home" is where users store their information right?  Like if I had a bunch of music and pictures and spreadsheets and word processing documents, they would/should be in "/home" right?

I have read that some people put their "/home" directories on a second hard drive.
Does that mean that the main Linux operating system is on, say, drive 1, and "/home" is on drive 2?  Hypothetically, if you removed drive 1 (with the Linux OS), then all of your data would be safe and accessible on drive 2 right?  Like could you put drive 2 into another system at that point and access it do you think?

Also, I have heard that putting the swap partition on a second drive is a good idea.  Do you think so?

---

### Post by Perfect Storm on 2011-03-03
You don't need a second HDD to make a /home partition, it can be on the same HDD.

I have 2 HDD (500GB each)
It looks like this:
HDD 1
/boot
/swap
/ <root>
/home
/games

HDD 2
/multimedia
/storage


When you keep your /home separated you can re-install Ubuntu without loosing your stuff and setups of your users (which are in /home).

---

### Post by Hedgehog1 on 2011-03-03
The advantage of the separate /home in either a separate drive or a separate partition on the same drive is that you can install a new OS and not damage your data.

I just separated my data to a /home parition on the same drive myself.

Here is the guide to doing it after the inital install: [https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving").

A.I.'s setup is more, umm, Nerdy...

***The Hedge***

:KS

p.s. The concept is that the 'real' /home directory is ignored, and your partition called /home is used instead.

---

### Post by Canime on 2011-03-03
You are right in how you figured it out. The home directory can be on a different partition, and that partition can be on a different hard drive. I have tried to do the same thing, because simply I didn't have enough space on my partition to be happy with it. 

Honestly the best idea if you can fit it into your case is to add that second hard drive.

However, I find that all too often my second hard drive isn't recognized as a slave.

I've tried insistently to add that extra drive for extra space to no avail because alas, bios has trouble figuring it out. As an alternative, I have a massive external drive which I use for backups and sometimes virtual disks, (that saved my butt in one particular case from a nasty installation of Ubuntu 10.10), and you could employ something similar to your configuration in order to obtain massive hd space on your home drive.

---

### Post by Hedgehog1 on 2011-03-03
I missed the swap question:

If you are a MS windows use with very little RAM, having a separate drive for swap space is a decent idea (more ram is better)

If you are a Linux user with very little ram, you will use swap less, so the difference is not as noticeable (more ram is still better, but not as critical here).

If you have plenty of RAM, swap is only used for 'Suspend' and it's location doesn't matter so much.

---


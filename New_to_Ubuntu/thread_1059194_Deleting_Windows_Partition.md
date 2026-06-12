---
title: "Deleting Windows Partition"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Slaskie on 2009-02-03
I have tried Ubuntu 8.10 over the last week via Wubi and it works fine, so later today I am going to partition my hard drive into a dual boot between Windows XP and Ubuntu 8.10. My question is, if I later find that I simply no longer need windows at all, can I just wipe the windows xp partition off of my hard drive? Or is it more complicated? Thank you. :D

---

### Post by Elfy on 2009-02-03
No it's not more complicated - you can reformat it and resize existing partition or create new ones.

---

### Post by 7mkgw7q on 2009-02-03
It is a pretty simple process actually. There is a partition editor in Ubuntu where you can basically format and remove any unwanted partitions. Many people (myself included) people prefer gparted for the gnome environment, but there are quite a few programs. You might want to read a couple of walk-throughs before trying it though, because when you are dealing with partitions, it can get a bit hairy for the beginner.

---

### Post by theDaveTheRave on 2009-02-03
slaskie

check out this thread [http://ubuntuforums.org/showthread.php?t=238146]("http://ubuntuforums.org/showthread.php?t=238146")

This chap is doing the exact same thing.

If you are using Wubi you should have a copy of GParted on the instal.

I can't remember the exact process for setting up a dual boot, but having done this on an XP terminal about 1 month ago I recall that it was the easiest install I had done of Ubuntu.

From memory, when you boot up you should get an option to "install ubuntu" from the <wubi> part of the drive. From there is is similar to using the standard installation for a dual boot install.

Advice.

Get your windows drive down nice and small, using a couple of runs of defrag etc

Set up 2 paritions on your main ubuntu section. the first will hold all the "root" files and all the important boot procedure and executables. Then on the other set up a separate partition for your < /home > this will hold all of your personal files etc, and any web sites that you regularly visit will have the username / passwords stored in files within the < /home > then when you decide to do a clean install everything that you need to keep is safe, and you can "format" your remaining section of HDD for the new install without loosing all that infromation.

check out this thread []("http://ubuntuforums.org/showthread.php?t=283131") by bodhi.zazen it will help you to make that newly formated HDD from the windows partition appear where you want it too.

Good luck, and remember to report back on you install experience.

David

---

### Post by Slaskie on 2009-02-03
Actually I have already uninstalled Wubi (I was only using it to test Ubuntu) so I do not plan to use that for the install, I will be using a standard install from a disk. I spent some of my weekend cleaning up my hard drive (I went from having 20gigs of free space to 74gigs).  Thank you for your responses!

---


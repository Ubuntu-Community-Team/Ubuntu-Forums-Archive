---
title: "How to create a storage disk format launcher"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by lord_exile on 2011-04-28
I am having trouble creating a command launcher to format a internal hard drive that I am using as a slave drive. Can some one please help me ?

---

### Post by ajgreeny on 2011-04-28
> **lord_exile said:**
> I am having trouble creating a command launcher to format a internal hard drive that I am using as a slave drive. Can some one please help me ?
Why should you need a launcher to format a partition; you will, I assume only need to do this once, so a single command line sequence should be sufficient for you, and a launcher will not be needed.

Have a good read through the info here:-
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
where there is a section on command line formatting.

---

### Post by lord_exile on 2011-04-28
If that was the case you would be correct. I store data on these drives for a short period of time. At that point I move the data to its permanent location. I do not have a partition on the drives. I use the whole drive. So a quick launcher to reformat the drive would be the ideal option for me due to the security factor of this data. It is work related so I like being able to do a format on the drives.

---

### Post by ajgreeny on 2011-04-28
In that case you will find it easiest to write a shell script to do what you want and then make a launcher on the desktop (or wherever you want it) which points to that script.

The link I gave last time will be useful for the commands needed in your script, so have a good look at that, then come back again if you need to.

PS:  Your comment *"I do not have a partition on the drives. I use the whole drive."* is not, and can never be correct.  Even if you use the whole drive each time, there has to be at least one partition in order for it to be formatted.  Perhaps you know this, but your comment did not make that clear, so I just wanted to make sure we are speaking abouit the same problem.

---


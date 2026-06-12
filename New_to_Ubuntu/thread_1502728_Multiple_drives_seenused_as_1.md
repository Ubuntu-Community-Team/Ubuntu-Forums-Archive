---
title: "Multiple drives seen/used as 1?"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by Off Topic on 2010-06-05
I just shut down my HP Mediasmart Server for the last time until I find a way to run it with Ubuntu or another linux variant.

The MSS didnt show the 4 hard drives,  just the shared folders in one big storage pool.  I moved three of the four drives from the MSS to my Ubuntu server,  at the moment Im fine with using one drive for videos,  and using the smaller drives for music and file sharing.  Is there a way for the Ubuntu server to see all four,  or the three non system,  hard drives as one large storage pool?

---

### Post by diablo75 on 2010-06-05
I'm jumping on board with this thread because I'm in a similar situation.

I have PS3MediaServer running on one of my boxes sharing out a couple different paths (a few folder in my home folder, and a folder that represents an external hard drive located in the /media folder).

I was hoping for a way to perhaps "mount" some kind of virtual library that combined the contents of everything you threw at it into one path.

Edit to add:  In Windows 7, this feature is called creating a "[library]("http://windowsteamblog.com/windows/b/developers/archive/2009/04/06/understanding-windows-7-libraries.aspx")".

Second edit to add:  It looks like someone tried to submit this idea to Ubuntu Brainstorm and did an absolutely awful job at describing what they were wanting (look at the comments; nobody knows what the hell the submitter was requesting):  [http://brainstorm.ubuntu.com/idea/15095/](http://brainstorm.ubuntu.com/idea/15095/)

---

### Post by friv_livs on 2010-06-05
Tell each drive to mount to the same place in fstab?

Unless there is some problem with that method.

---

### Post by gsocker on 2010-06-07
Mounting to the same location will not work. What you need is software RAID or Logical Volume Manager(LVM). Not sure if the default install CD has support for either of these.

---

### Post by gsocker on 2010-06-07
Note that  those two are not the same thing. LVM will allow you to pool underlying devices into one big device. So will software raid. However, software raid has better options in terms of data security. 

The default LVM setup for multiple devices, as well as RAID level 0, will give you all the space on the drives to use. 

BUT: if ANY drive out of the 4 fails, say goodbye to your data.
This is because the data is stored across the 4 drives with no redundancy; if any drive fails it takes part of your data with it.
This will likely corrupt the filesystem to the point where very little can be recovered. 
 With mirroring or parity data you have security against(typically one) drive failure. It would be better to setup software raid level 1 or 5, or set LVM with something along the lines of raid level 1.

---


---
title: "Installng a second time after an error"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Churchwarden on 2011-02-22
Hello,

This is my first posting ):P

I have been using Ubuntu on my laptop running it from a memory stick.  I like its speed so I have tried to install it alongside Vista.  All went well until the installation wizard told me that there was a fault with the CD (not using a CD but let that pass)  The installation stopped asking for a report.  I could not send that becasue the computer hung for more than 30 minutes so I closed the window and checked to see if Vista would start.  It did (Phew!)

I reinserted the memory stick and tried again.  This time when I came to the stage where you drag the boundary to chge the sizes of the partitions there appeared to the be last installation of Ubuntu in addition to the new one that I am trying to install.

I am sure that someone will be able to tell me what to do.

TIA

Nick

---

### Post by seawolf167 on 2011-02-22
Welcome to the Forums!

Sounds like you might have a corrupted iso download, I'd try redownloading the cd and MD5 Hashing to ensure that you don't have any corruption.

[Ubuntu Download location]("http://releases.ubuntu.com/10.04.2/")

[How to MD5 Sum]("https://help.ubuntu.com/community/HowToMD5SUM")

You should be able to delete the "currently installed" version of Ubuntu and then overwrite it with your new installation.

Before you install though, I ***very highly ***recommend making a backup image of your entire disk so if something goes wrong you can restore your data & Windows OS. I'd use [Clonezilla]("http://clonezilla.org/"). Simply burn the iso to a cd, then boot from the cd and follow the on screen instructions to image your drive to an external hdd or similar.

---

### Post by Churchwarden on 2011-02-22
> **seawolf167 said:**
> Welcome to the Forums!

Sounds like you might have a corrupted iso download, I'd try redownloading the cd and MD5 Hashing to ensure that you don't have any corruption.

[Ubuntu Download location]("http://releases.ubuntu.com/10.04.2/")

[How to MD5 Sum]("https://help.ubuntu.com/community/HowToMD5SUM")

You should be able to delete the "currently installed" version of Ubuntu and then overwrite it with your new installation.

Before you install though, I ***very highly ***recommend making a backup image of your entire disk so if something goes wrong you can restore your data & Windows OS. I'd use [Clonezilla]("http://clonezilla.org/"). Simply burn the iso to a cd, then boot from the cd and follow the on screen instructions to image your drive to an external hdd or similar.

The difficulty that I have ATM with that advice is that the DVD drive on the laptop appears to have gone faulty.  It reads OK but doesn't write.

I have used a memory stick for the install I will try another complete download try the same again.

How do I delete the currently installed version?

Nick

PS I won't be able to get on line again tonight so I shall pursue this in the morning.

---

### Post by seawolf167 on 2011-02-22
The memory stick version will essentially be the same - download it and run an MD5 Hash comparison to ensure that nothing was corrupted during the download.

When you get to the install screens, you can either specific the partitions manually, in which case you should just delete the current Ubuntu partition, or you can have the installer automatically partition the drive for you. In the latter case, just select to overwrite your "current" Ubuntu installation.

---

### Post by Kixtosh on 2011-02-22
One other thing I'd like to mention, since you're intending to install alongside Vista, I presume: make sure you run the Vista defragment utility at least three times. It should help avoid errors within your Vista installation when Ubuntu resizes the partition.

---

### Post by Churchwarden on 2011-03-05
I never thanked you kind people for the help.  I am up and running with Ubuntu now, thanks

Nick

---


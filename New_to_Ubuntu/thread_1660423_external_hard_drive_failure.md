---
title: "external hard drive failure"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by dquiggin on 2011-01-05
I have a western digital 600gb external hard drive. it was working fine then failed! i think it was after it was turned off without safe removal within windows. on my windows 7 machine it says usb devic e unrecognised. in ubuntu absolutely nothing happeds at all. im not very experienced with ubuntu but im hoping it should be possible to recover within ubuntu.
i have loads of photos i need to recover - unfortuately was in process of backing up!
can anyone help?
cheers
d

---

### Post by seawolf167 on 2011-01-05
Do this first from your Windows machine (WD doesn't support Linux-based software, so you have to use Windows as far as I know).

Go [here ]("http://support.wdc.com/product/download.asp?groupid=609&sid=3&lang=en")and download the WD Data Lifeguard Tools (the hdd model doesn't matter as the software is the same for all models) and run the full tests against your disk in question.

If the disk is dead - well then its dead :(

But if the disk passes the tests, you can try to use [TestDisk ]("http://www.cgsecurity.org/wiki/TestDisk")to recover the partitions.

---


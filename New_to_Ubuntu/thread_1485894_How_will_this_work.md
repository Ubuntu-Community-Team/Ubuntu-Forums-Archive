---
title: "How will this work?"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by rramsay on 2010-05-17
I'm installing 10.4, and I'm going to load it onto a separate drive, so I'll have xp on one drive and 10.4 on the other.

I have an IDE system, what I need to know is the jumper settings, I plan on using Ubuntu as the main operating system, should I set that drive to master and the old drive to slave? Or should I set both to cable select?

After I learn what I'm doing I plan on discarding windows completely, thanks rramsay.

---

### Post by Nesaskewatch on 2010-05-17
I would set both to master.  You will have to hit f12 during boot to select which disk you want to spin up.

---

### Post by LowSky on 2010-05-17
It really doesn't matter how you set them up. 
A drive can be a slave and still be used as the main hard drive for booting from. The whole master/slave thing is just for the BIOS. It wont effect performance. Just set the the BIOS to boot the hard drive you wish to use.

But to warn you Windows XP doesn't like changing its loction once its installed. So if XP is currently the Master, keep it there and install the second hard drive as the slave. Then change which drive BIOSwill boot from to the slave drive.

---

### Post by rramsay on 2010-05-17
Okay, thanks bye bye Bill.

---

### Post by Mark Phelps on 2010-05-17
IF the two IDE drives use the same data cable, they can not BOTH be set to Master; instead, one has to be Master, the other Slave --  or BOTH set to Cable Select.

IF they use different data cables, they can both be set to Master.

The OSs don't care how the drives are jumpered.

---

### Post by Calash on 2010-05-17
> **Mark Phelps said:**
> IF the two IDE drives use the same data cable, they can not BOTH be set to Master; instead, one has to be Master, the other Slave --  or BOTH set to Cable Select.

IF they use different data cables, they can both be set to Master.

The OSs don't care how the drives are jumpered.


To add on, if the system is newer you should have to trouble setting the drives to cable select and letting them determine the settings automatically.

But as stated the OS really does not care about the jumpers.

---

### Post by cascade9 on 2010-05-17
Personally, I never use 'cable select'- its always seemed pretty daft that the 'master' on cable select is the far end of the cable. Longer cable, more chance of crosstalk, etc...besides the fact that normally the CD/DVD is at the top of the case, and HDDs under them. 

Since you almost always have 2x IDE channels (unless its a new STA motherboard with 1 x IDE), set both HDDs to master, and set the CD/DVD drive to slave. 

BTW, some places still say crazy things like 'if you have 2 devices on the same cable, transfer speeds will always be at the speed of the slowest device'- that was true, a long time ago, but for anything you are going to run ubuntu on, its not. So run both drives as master. 

Also, a neat hint- put the linux swap on the drive that doesnt have your linux OS.

---

### Post by -humanaut- on 2010-05-17
I've did just this except with netBSD and Opensolaris my bios had the ability to just shutoff one of the drives.

---


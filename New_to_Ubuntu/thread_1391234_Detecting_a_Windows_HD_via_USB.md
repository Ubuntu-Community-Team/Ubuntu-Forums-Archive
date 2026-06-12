---
title: "Detecting a Windows HD via USB"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by ovid9 on 2010-01-26
I have acquired 2 older hard drives, one is a Western Digital 20gig, another is..I can't remember, I seem to remember seeing an IBM logo on it.  Anyway, its a 15.8 gig drive.  
 
I have a IDE to USB adapter with power supply, both drives spin up though the 15.8 one sounds less than healthy.  Maybe its just a loud drive, I'm more concerned about actually getting my computer to recognize it first.  
 
However when plugging the USB cable into any of my external ports, nothing pops up.  I was expecting it to show it like it would a thumbdrive.
 
How do I get the drives to show up so I can attempt to format them to ext3?
 
I'm sure its something fairly simple, but I don't know for certain.

---

### Post by chewearn on 2010-01-27
I assumed you don't have anything in the drives that you wanted to keep.

Use Partition Editor (gparted) to reinitialise the partition table on the drive, then create a new partition followed by formatting.  It should be self-explanation thru the GUI.

---

### Post by ovid9 on 2010-01-27
Hmmm...  Ok, I'll give that a shot. 

So far though I haven't been able to get gparted to even see that they are there.  When I get home I'll see what I can do reinitializing them.
 
And yeah, if there is any data on them it can go goodbye.

---

### Post by chewearn on 2010-01-27
If it's not showing up in gparted, then the device detection is unsuccessful (i.e. no /dev/sd??).

In this case, plug in USB wait about 10 seconds, then run:
```
dmesg | tail -n 20
```

This will (hopefully) reveal any error messages from the kernel about the device detection.

---

### Post by ovid9 on 2010-01-27
Ok, great.  

These two drives MAY be junk, that's why I got them for free.  So, its the whole deal of nothing is lost if I can't get them to work.
 
Thanks and I'll see if I can get it to see what's going on with the drives.

---

### Post by ovid9 on 2010-01-28
Alright, I got the 20gig drive to be recognized and its now happily formatted to ext3.  

The 15.3 gig IBM drive I couldn't get anything to happen with.  Running the command posted earlier showed some I/O errors and I just decided I wasn't too worried about it. 
 
20gig is about the smallest usable data backup drive I want to have.  The 15.3 drive started sounded even less healthy after I plugged it back in last night.  It didn't sound quite like it had sand spread on the plates...but....it sounded far to much like that for me to mess around with it.  
 
Thanks.

---


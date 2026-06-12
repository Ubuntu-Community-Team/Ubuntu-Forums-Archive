---
title: "Very Interesting Swap Performance issue"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by Andy06 on 2009-05-29
So Swap is used as a memory holding area for apps and is faster than the hard drive but slower than RAM right?

Live CDs by default make a swap file on your system because reading/writing from the CD is quite slow. However if you already have linux installed on your system (any linux distro with a dedicated swap partition), the Live CD uses that partition to speed things up.

Now the interesting this happens when you use a LiveUSB instead of a LiveCD. Since it's the same files and everything as the Live CD, it will either create a temporary swap file on your hard drive or use the existing swap file from a full ubuntu/otherlinux install. BOTH of these are slower than the USB drive itself, completely defeating the purpose of a Swap area.

This is also true for a full install on a USB flash drive/external SSD without a swap on it. It uses the swap on your internal hard drive.

So should I start partitioning the external flash/SSDs and making a swap on them instead of relying on the existing swap on internal hard drive?

Or have I got the theory completely wrong.

---

### Post by whoop on 2009-05-29
I see swap more like an escape feature if you are using to much ram (it really comes to use if you suspend your system). I'm not that certain that the livecd or liveusb will create a swap on your hd if there isn't a swap already there.
I don't think swap is faster than the harddisk, it is (a part of) the harddisk.

Swap performance will always suck compared to ram (maybe not so much on ssd).

So I would say if you need to use swap all the time, do less, or get more ram.

I seldom use swap. Actually the only times it got used was with memory overflows (which shouldn't happen)

---

### Post by cariboo on 2009-05-29
I have to agreee with the previuos poster. Swap is only used when you have exhausted your ram. 

The swap partition on your hard drive is much slower than ram. 

The LiveCD doesn't make any changes to your hard drive, so how could it create a temporary swap file.

---

### Post by Andy06 on 2009-05-29
Thank you both for the explanation.

---

### Post by XCan on 2009-05-30
I'm not sure one can safely consider USB thumbdrives faster than harddrives though. Unless we are talking about 3.0 which might in practice be faster than most harddrives.

---

### Post by Paqman on 2009-05-30
> **XCan said:**
> I'm not sure one can safely consider USB thumbdrives faster than harddrives though. Unless we are talking about 3.0 which might in practice be faster than most harddrives.

+1

The USB bus is slower than your SATA bus. Just look at the performance drop you get between a USB external hard drive and an internal (or eSATA) one.

---

### Post by -kg- on 2009-05-30
It most definitely is dependent on how much RAM you have installed.  This laptop has 2 GB of RAM, and since I don't use the hibernate feature, I have sufficient RAM such that I have never used my swap partition at all (and I've checked on this).

If you use (or plan to use) hibernate, however, then swap will be used to store the settings and running applications, etc., of the state of the machine upon entry to hibernation.  Then once you leave hibernation all the information is loaded from swap back into RAM and your machine is at the same point it was upon entry.

Other than that, if you have sufficient RAM, then the swap area is almost never used, except in certain circumstances using software that might take more RAM to process, or that is so big that it won't all fit into RAM.

I agree with Cariboo...the Live CD doesn't make any changes to your hard drive.  If your hard drive has one big (Windows) partition with no free space on it, then it wouldn't have room to create a swap partition on it without resizing the existing partition, temporary or otherwise.  That would be a major change to your hard drive.

If you run out of RAM while running the Live CD, then it will load what it needs next from the Live CD, which is basically a "swap" itself.  If some data takes up that much room, Ubuntu will unload part of itself, deal with the data, and then reload the missing part from the Live CD.  It will be slow as sin (naturally), but it will work.

If you have RAM issues (i.e., your installed RAM is at or near the lower limit), then alternatively you can create a temporary swap partition, either on the hard drive or some other media, like a USB drive.  But if you have sufficient RAM, this should not be necessary.

Virtually the only reason you would have to run the Live CD is to test the computer's hardware compatibility to Ubuntu.  One likely will not try to run major software while using it, so swap space should almost never be an issue.  If it is, then it will just be slow as sin unless you yourself create a temporary swap space somewhere.

---

### Post by blueridgedog on 2009-05-30
> **Andy06 said:**
> 
This is also true for a full install on a USB flash drive/external SSD without a swap on it. It uses the swap on your internal hard drive.


I would say that is not the case.  A USB install could not randomly pickup swap off of a host hard drive.

Think of swap as the same as virtual memory in Windows...

---

### Post by The Cog on 2009-05-30
Oh yes it would. Try it. Fire up the live USB and run swapon -s. If finds and uses the swap partition.

I read some years ago that some forensics investigators used and modified knoppix and one of the most important mods was to stop it using the disk swap partition if it found one.

---

### Post by snowpine on 2009-05-30
Ubuntu Live will find and use an existing swap partition on your hard drive. It will not create a new swap partition if none exists.

---

### Post by blueridgedog on 2009-05-30
Interesting...so as long as it finds a partion of the right file system type, it will grab it.  I never knew.

---

### Post by Andy06 on 2009-05-31
Yeah it's very useful as a feature. Since the swap space is of questionable usefulness unless you use hibernation, you can use the same swap space for multiple installs of various linux distros even if you have them all on external USBs or LiveUSBs.
Helps save a lot of space. 

Else installing 3-5 distros with 4 GB of RAM (and hence at least 4 GB of swap space per distro = 20ish GB) would be a nightmare.

---

### Post by Paqman on 2009-05-31
> **Andy06 said:**
> Yeah it's very useful as a feature

It's also a really common stumbling block for people trying to resize partitions from the LiveCD/USB.

If the swap is within an extended partition (very common) then Gparted will lock out the whole extended partition and folks are unable to modify any other partitions within it. A simple swapoff solves the problem.

---

### Post by Andy06 on 2009-05-31
Hehe, yeah that's got me more than a couple of times. Never for more than a couple of seconds, but still...

---


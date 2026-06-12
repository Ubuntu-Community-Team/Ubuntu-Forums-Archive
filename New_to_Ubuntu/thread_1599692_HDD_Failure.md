---
title: "HDD Failure"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by expatCM on 2010-10-18
I have had a message for a few hours telling me that one of the hdd's is about to fail.  Ok so I have been warned.

I do not want to power off the system, I would like to put a new drive in a USB housing and then make an image of the existing drive on that new drive.  The challenge is that the drive is mounted since that is where the operating system exists.

My question is what program should I use to do this?  If I cannot do that then presumably if I use gparted to create the same partitions then at least I can copy over the partitions that are not the o/s and install fresh the operating system.

---

### Post by Paqman on 2010-10-18
First of all, you're doing the right thing. You want to make a backup of the data on that drive before it fails.

Depending on how much data you need to protect, you may not need to make a full image just now. Simply copying the data to the external drive will protect you in the meantime.

To create an image you can boot up into the LiveCD, install partimage and go for it.

---

### Post by indytim on 2010-10-18
> To create an image you can boot up into the LiveCD, install partimage and go for it.

As I recall, Partimage does not support ext4 filesystem.  

If I am correct, I would recommend using fsarchiver as it will support images for most filesystems.  Use it as part of the system rescue cd.  Links are supplied for both below.

[http://www.fsarchiver.org/Main_Page]("http://www.fsarchiver.org/Main_Page")

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

IndyTim / DataMan

---

### Post by expatCM on 2010-10-18
Thank you for the help.

Yes partimage does not support ext4.  It is not in the repositories now but the documentation is.

I was wondering if ddrescue or gddrescue are tools I should consider.

FSArchiver comments that "It's still under heavy development so it should not be used for critical data." so I wonder what that means.

I guess the decision I have to make is whether I can do anything without rebooting the system since the drive can be accessed at present.  I have backed up the data now ....  that took a long time but it is done so I am not quite at risk but it would be nice not to loose the present system setup.

---

### Post by Paqman on 2010-10-18
Btw, what is actually wrong with the drive? Which SMART metric is it that's gone critical?

---

### Post by expatCM on 2010-10-18
From Disk Utility

DISK FAILURE IS IMMINENT

#5  Reallocated Sector Count

Assessment - Failing

Normalized  35

Worst   35

Threshold  36

Value  2700 sectors.


I had a similar message two days ago with many fewer sectors which was preventing the system from booting (I got the message through the CD) so I thought that perhaps it was a problem with just the boot sector or the o/s but sadly not since I formatted the partition and reinstalled and today the message came again but rather more explicit.

fsck -a would not run and a manual fsck indicated nothing doing.

---

### Post by CharlesA on 2010-10-18
Clonezilla can clone the drive to another drive.

You'd have to reboot and boot off their livecd to do so tho.

---

### Post by Mark Phelps on 2010-10-18
I think the problem is that, regardless of what app you use, if you want to clone an image of the partition that is in use, you will have to unmount it first, and if that is your Ubuntu root partition, Ubuntu will then not run.

So, unless you just want to copy off a bunch of files, you will have to reboot -- from a CD -- and ensure that the partition you want to copy off is unmounted.  

Don't know of any way around this.

---

### Post by expatCM on 2010-10-18
CloneZilla is a good idea but like it is properly pointed out by both Charles and Mark I am going to need to reboot.

I think I am chicken ....  what could possibly go wrong .............  :)

Thank you for your suggestions everyone.  I will go forth and play now.

---

### Post by CharlesA on 2010-10-18
Best of luck. It should work ok unless you've been seeing stuff like "unrecoverable read errors" and whatnot in the SMART data.

---

### Post by indytim on 2010-10-18
> FSArchiver comments that "It's still under heavy development so it should not be used for critical data." so I wonder what that means.

I used it about 2 months ago to rebuild a 1Tb drive that went south permanently.  The re-build included ext4, ext3 and ntfs partitions (12 in total).

-IndyTim / DataMan

---

### Post by Paqman on 2010-10-19
> **CharlesA said:**
> Best of luck. It should work ok unless you've been seeing stuff like "unrecoverable read errors" and whatnot in the SMART data.

Exactly. The SMART data is telling you that the drive's built-in error handling systems are still coping, but that they will soon run out of ability to compensate. For now your data is still relatively secure, but you need to get it onto a fresh drive soon.

---


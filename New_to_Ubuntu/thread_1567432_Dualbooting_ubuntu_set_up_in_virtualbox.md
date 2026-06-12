---
title: "Dualbooting ubuntu set up in virtualbox"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by aNDoz on 2010-09-03
im a ultra n00b in linI've set up ubuntu in my virtualbox. it's fully working.

Using that OS/partition ( is it?) made with virtualbox, could I make it so I can dualboot?

---

### Post by TheWeakSleep on 2010-09-03
Unfortunately, as far as I can tell, as long as it's in virtualbox, it's confined to virtualbox itself. No partitions were made, but instead a virtual harddisk was created, that can only be loaded via the host operating system. If you want to dual boot, you could try wubi, assuming you're running windows.

---

### Post by QIII on 2010-09-03
Using Wubi would be of little use.  Wubi is a great way to test out Ubuntu and kick the tires, but it is not a "dual boot" and it is not really intended to be a permanent solution.

Having used VirtualBox, I suspect you have already had a chance to do that to your satisfaction.

Genuine dual boots require repartitioning the drive and installing the other OS on the new partition(s) so they run natively from your hard drive.

What may be of concern is that VirtualBox uses an Intel virtual GPU, among other virtual hardware.  When you do an actual dual boot, Ubuntu will be running on your machine, so video drivers and such may be at issue.

Could you give us some specs on your machine?

Some good instructions here for dual booting:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by aNDoz on 2010-09-04
thanks for the reply guys, and sorry for the very brief opening thread ( I was in a rush to post it) 

is the infomation from "dxdiag" good enough?

I have already used Wubi (friend informed me about it) but the final installation doesn't work for me. 
the percentage reads at 700% and an error pops up, if I press OK then it pops up again, I'm about to go out but will find out what the error is exactly and then edit this post. It's something about the Hard drive I think. Think.
(from a google search and trying to remember, I think it says this
```
No root file system is defined
``` )


I'm too worried to partition the hard drive because I heard I can loose data and as this computer is used by several people it would be a disaster. the C drive has about 176gb free BTW

---

### Post by t0p on 2010-09-04
> **aNDoz said:**
> 
I'm too worried to partition the hard drive because I heard I can loose data and as this computer is used by several people it would be a disaster. the C drive has about 176gb free BTW

If you back-up everything on the drive, there should be no need to worry about data loss.  But the fact that the computer is used by several other people may pose a problem: unless you have admin access to their accounts, how are you going to back up their stuff?  Knowledge of Linux (and computing in general) is in short supply, and there's no way I can predict what these other users are going to think when you say you want to back-up their data so you can install a dual-boot.  Some users might say "Go get your own computer to experiment on".  And I'd be inclined to agree with them.  For goodness' sake, *don't* do anything like this without the other users' permission.

---

### Post by aNDoz on 2010-09-04
The computer USED to be a family computer but now I'm the only user but the other accounts still remain, I do have admin privileges

---


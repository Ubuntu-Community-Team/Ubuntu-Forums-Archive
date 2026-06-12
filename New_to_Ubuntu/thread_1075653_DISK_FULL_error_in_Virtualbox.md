---
title: "DISK_FULL error in Virtualbox"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by steve70 on 2009-02-20
I have Virtual Box running on 8.10 64-bit edition. I was able to successfully create 3 Windows Servers (03) and 1 XP client. However, I get a VBox error message ('DISK_FULL'error) when I was doing updates, stating that I need to increase my HD space.

I found some solutions, but it involves gparted. Can I use the app on my desktop as an .iso file mount for the Virtual machines? If not, what's the best site to download a current .iso (d'loaded a couple, but crapped out when I mounted on machines.).....

---

### Post by blueridgedog on 2009-02-22
Perhaps I don't understand.  Is the partition the virtual machines on full?  Can you simply move/remove one and grow the others?

---

### Post by billgoldberg on 2009-02-22
I don't have VirtualBox installed on this pc, but can't you just "grow" the virtual harddrive that's full?

I doubt very much that Gparted can be used to grow virtual harddrives.

---

### Post by lkraemer on 2009-02-22
Steve70,
I've ran into the same problem by using the default 10Gig VDI size
when installing XP.  By the time I had XP installed I only had less
than 3 Gig for user data.  But, there are solutions.

Go to the VirtualBox Forum site, Register, Login, and search for
Expand VDI, Resize VDI, etc and you will find your solutions.

Or look here:
[http://ubuntuforums.org/showthread.php?t=723219](http://ubuntuforums.org/showthread.php?t=723219)

Google & Search are your friends.  Try them next time.....

lkraemer

---


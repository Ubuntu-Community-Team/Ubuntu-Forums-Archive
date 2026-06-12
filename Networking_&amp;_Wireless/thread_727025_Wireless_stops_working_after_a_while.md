---
title: "Wireless stops working after a while"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by Zalbor on 2008-03-17
I have an acer aspire 5920G laptop, and according to System>Preferences>Hardware information it has a "PRO/Wireless 4965 AG or AGN Network Connection" card by Intel.
Wireless worked out of the box, seemingly with no problems at all. Whenever I boot up the computer, it almost immediately connects and seems to be fine.

But after a while (which has been from 15 minutes to over an hour, up to now) it just stops working. It keeps detecting networks, but it won't connect to any of them. It shows the icon trying to connect and then it just goes to the icon with the two computers and the X in the corner. The only way to reconnect is to reboot the computer, and then it's fine again.
I've tried to update the driver following [this thread](http://ubuntuforums.org/showthread.php?t=493095) (although it was written for Feisty and I'm in Gutsy) but it doesn't seem to have worked. I also tried using alternative network managers, like wifi-radar and wicd, and it still happens.

I've looked in the forums for similar threads, but all of them seem to be either unanswered or to have been posted before Gutsy was released, so they're not really helpful to me.

If anyone has made it work or knows something more to try, please explain. Thank you.

---

### Post by myddewji13 on 2008-03-17
this may be irrelevant...but is this by any chance a wpa network?

---

### Post by Zalbor on 2008-03-17
Np, my own network just uses WEP, but I've tried making it a completely insecure network and the same still happens. And when it happens, it won't connect to any other network either, so it can't have to do with mine.

---

### Post by dca on 2008-03-17
Does this sound similar?
 
[https://answers.launchpad.net/ubuntu/+question/16768](https://answers.launchpad.net/ubuntu/+question/16768)
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/144621/comments/42](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/144621/comments/42)
 
...sounds like the bottom link actually resolves the issue, I just wanted to see if what you're encountering is actually an Ubuntu/Intel bug...

---

### Post by Zalbor on 2008-03-17
Thanks dca,
I installed the package from the second link and rebooted. It "broke" the kernel's usplash screen but the system seems OK. dmesg confirms the newer version of the driver is loaded, and wifi works still. I suppose all I can do now is keep the computer running for a while and see if it disconnects.

(To answer your question, that was/is exactly my problem as far as I could tell).

---


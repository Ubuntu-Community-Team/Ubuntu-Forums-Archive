---
title: "Movies choppy in full screen after upgrade to 9.04"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by TomGroff on 2009-09-05
Hulu Movies have become choppy in full screen immediatedly _after upgrade to 9.04_.  

This didn't happen in the previous version of Ubuntu.  Played shows smooth as glass.

I am using: Flash 10,0,32,18 installed

I've tried setting the flash preferences to LOW Quality. (Didn't have to before.)
I've also unchecked Hardware acceleration in flash. (This use to fix the problem)

Anyone else find a fix for this issue?

---

### Post by halitech on 2009-09-05
what video card do you have? did you check to see if there was a driver in System - Admin - Hardware drivers that you can install?

---

### Post by Ric_NYC on 2009-09-05
> **TomGroff said:**
> Hulu Movies have become choppy in full screen immediatedly _after upgrade to 9.04_.  

This didn't happen in the previous version of Ubuntu.  Played shows smooth as glass.

I am using: Flash 10,0,32,18 installed

I've tried setting the flash preferences to LOW Quality. (Didn't have to before.)
I've also unchecked Hardware acceleration in flash. (This use to fix the problem)

Anyone else find a fix for this issue?


It's like a "feature" of Jaunty...

If someone find a way to have a good performance playing flash videos in Ubuntu, please let us know!

---

### Post by TomGroff on 2009-09-05
Halitech:

VGA Controller
Model:  82865G Integrated Graphics Controller
Vendor: Intel Corporaton (Dell)
Connection: PCI

Hardware Drivers reports: Nothing. No Drivers listed at all.

Further testing shows:
System Monitor: Resources tab Reports:
CPU History Pegged at 100% at full screen video.

Ric:  
Lordy I hope its not part of Jaunty.  Had to format my drive and reinstall Hardy once before.  Major pain.

---

### Post by woedend on 2009-09-05
Aye.  I had the same problem on my laptop when I bought it, also intel graphics and initially thought "man, this computer is slow".  Then I got to reading a bit and found that Jaunty just shipped with horrible intel graphics support.  Follow the steps here - [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)
and you'll see your smooth as glass video again.

When I did this...I basically just did the kernel update and the latest intel driver as listed on that website...rebooted, and enjoyed.

---

### Post by halitech on 2009-09-05
> **TomGroff said:**
> Halitech:

VGA Controller
Model:  82865G Integrated Graphics Controller
Vendor: Intel Corporaton (Dell)
Connection: PCI

Hardware Drivers reports: Nothing. No Drivers listed at all.

Further testing shows:
System Monitor: Resources tab Reports:
CPU History Pegged at 100% at full screen video.

Ric:  
Lordy I hope its not part of Jaunty.  Had to format my drive and reinstall Hardy once before.  Major pain.

Tom,

unfortunately Ubuntu Jaunty shipped with a regression affecting Intel video chipsets but if you follow the steps in the link woedend posted, it should resolve your issue.


> **woedend said:**
> Aye.  I had the same problem on my laptop when I bought it, also intel graphics and initially thought "man, this computer is slow".  Then I got to reading a bit and found that Jaunty just shipped with horrible intel graphics support.  Follow the steps here - [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)
and you'll see your smooth as glass video again.

When I did this...I basically just did the kernel update and the latest intel driver as listed on that website...rebooted, and enjoyed.

thanks for posting that link and info for Tom, hopefully he can get things running smooth again.

---

### Post by TomGroff on 2009-09-05
Hmmm I've been searching myself and found the following fix which purports to revert to the Intrepid Xorg driver 2.4.

Would this be a safer bet than upgrading to an experimental workaround?
[Rollback Video]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

---

### Post by halitech on 2009-09-05
I haven't used either method (I've got an ATI card) so not sure but I think either method will be somewhat tricky as you are mixing programs that have not been tested by the devs to ensure it works properly.

---

### Post by woedend on 2009-09-05
You can use either method really...either one is undoable.  I'd try the kernel upgrade + new xorg before reverting, though.

---

### Post by TomGroff on 2009-09-14
Well neither worked worth a darn.  Ended up reformatting my drive and re-installing Hardy Heron from CD.  What a pain.
Upgraded all the Hardy packages.
Loaded Hulu and used the link to download the latest Flash.
 
Now I am getting wierd rainbow blocks randomly in the movies.  They happen approx every 30 seconds or so.  a bright red fading to green or purple at the edges is common.  about a half inch square or rectangular.
 
Gah!
 
Hardy used to be bullet proof!

---


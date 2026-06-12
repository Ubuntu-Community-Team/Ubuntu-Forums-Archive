---
title: "Tm2t with Ubuntu 11.04... problems!"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by rbusch90 on 2011-04-22
I've been wanting to assimilate myself into the Ubuntu community for quite a while.  I've tried multiple times, and every time I've had to give up for some reason.  Previously, I had an m11x, and although I eventually got Ubuntu working, it refused to ever turn off the graphics card, even though I was using the Intel on-board graphics (although it was happy to still give it power).  Essentially, this halved the battery power of my laptop, negativing the very reason I selected it in the first place.

I recently got a new computer, and I thought to myself that I'll give it another shot.  But this attempt has been just as difficult in different ways.

I have an HP tm2t touchsmart, and the touch functionality works fine.  I was able to find a script in these forums that made auto-rotate work well, too.  Now my frustration:

My computer refuses to boot!  I will turn it on, and the HP screen with hotkey to BIOS pops up, and when that leaves, sometimes the screen will turn a different color, like it's going to load something, and other times it doesn't.  In both cases, it eventually just becomes a black screen, although the computer seems to be running.  It seemed almost random how frequently it worked, and then I realized it seemed to boot up fine if it was plugged in to a power source.  But on battery, it would stay black forever.

When I go to standby, the same thing happens.  I try to come out of standby, and I am greeted with an eternally black screen.  Last time this happened, I restarted about 10 times, each of which resulted in another black screen.  This is when I simply plugged it into the wall, and it booted fine the first try (this may have been a fluke, but I have not tried trial-and-error enough to make a certain judgment on that).

Also, if this is in the wrong forum, I apologize.  I'm new, and this seemed like the appropriate place to me, but if it is not, just direct me to the more appropriate area to solve this problem.  Thanks!

---

### Post by madjr on 2011-04-22
welcome to the forums.

hm, this seems like a bug with your hardware when you go into sleep or hibernating.

you might want to report it or see if someone else has the same problem with your laptop model

[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

[http://ubuntuforums.org/showthread.php?t=734460](http://ubuntuforums.org/showthread.php?t=734460)

you want to give as much info as possible so follow the guide please. thx :p

---

### Post by rbusch90 on 2011-04-22
The problem is that it is not only occurring when waking up from sleep or hibernate (although admittedly, I have not even tried hibernate).  It happens when I am trying to start my computer up from being turned off as well.  I am kind of leaning towards thinking it has something to do with the incompatibility of my graphics card (switchable ATI Radeon).

Nonetheless, I will take your advice and follow these links to report the problem.  Thank you for the response.

---

### Post by dugh on 2011-04-30
> **rbusch90 said:**
> The problem is that it is not only occurring when waking up from sleep or hibernate (although admittedly, I have not even tried hibernate).  It happens when I am trying to start my computer up from being turned off as well.  I am kind of leaning towards thinking it has something to do with the incompatibility of my graphics card (switchable ATI Radeon).

Nonetheless, I will take your advice and follow these links to report the problem.  Thank you for the response.

Yeah I have the same issue and still haven't solved it, but there might be 3 possible solutions:

[LIST]
[*]-blacklist the i915 graphics driver (see thread linked to at bottom of this note)
[*]-use the new proprietary ATI driver just released a few days ago  [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
[*]-use the ppa edgers radeon driver (doesn't appear to be updated for natty yet) [https://launchpad.net/~xorg-edgers/+archive/radeon/](https://launchpad.net/~xorg-edgers/+archive/radeon/)
[/LIST]

Once we can get ubuntu booting well (and by the way, 10.10 does install), see this thread for tips on getting other stuff working like screen rotation and so forth:

[http://ubuntuforums.org/showthread.php?t=1716403](http://ubuntuforums.org/showthread.php?t=1716403)

---


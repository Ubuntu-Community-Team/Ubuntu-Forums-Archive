---
title: "Resolution problem.  Unsupported ATI card"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by Jereme2147 on 2011-04-07
I have searched and found several different and also seemingly opposing solutions to my problems.  

-Ubuntu 10.10, It's a solitary install, not running parallel to windows or anything.  I have very little experience, but I'm a fairly quick learner.  

The unsupported (best I can tell) card is ATI Raedon X300.  The system is being set up to run XBMC.  I don't have a standard monitor on it, just a TV via S-Video.  I make all the changes via VNC.  

I've given up trying to force an ATI proprietary driver, all I really care about now is adjusting the resolution.  I've been reading TONS of things, but this page seemed pretty close to a solution [https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)  My confusion is when you must edit the xorg.conf.  If I understand correctly, Ubuntu 10.10 doesn't use that? 

Any help is appreciated.  If this should be moved, I'm sorry. I felt as though this is a beginner as it gets.

---

### Post by timmy366 on 2011-04-07
Try going to System > Administration > Restricted drivers manager. I believe it will download the required drivers automatically.

---

### Post by Jereme2147 on 2011-04-07
> **timmy366 said:**
> Try going to System > Administration > Restricted drivers manager. I believe it will download the required drivers automatically.

"restricted drivers manager" doesn't exist in that menu.

---

### Post by timmy366 on 2011-04-07
Sorry, i'm not using Gnome...:)
Try System > Administration > Hardware drivers?

---

### Post by Jereme2147 on 2011-04-07
> **timmy366 said:**
> Sorry, i'm not using Gnome...:)
Try System > Administration > Hardware drivers?

gotcha.  Ya, I've done that. It doesn't show up as an available proprietary driver.  I realize this is the root of my problems.

---

### Post by Jereme2147 on 2011-04-07
I guess one big answer I need, should I be using xorg with 10.10?

---


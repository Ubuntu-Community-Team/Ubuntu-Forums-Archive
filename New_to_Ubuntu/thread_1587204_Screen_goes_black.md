---
title: "Screen goes black"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by ed_6678 on 2010-10-03
[SIZE=2]Hi,
I recently changed to Ubuntu on my old computer. It's a Dell Dimension 2350 that had XP on it before. The problem I am having is that occasionally the screen on my monitor will just go black. At first I noticed it only seemed to happen when using Gambas and Firefox. Tonight it occurred only while using Firefox, so I guess I can rule out Gambas, although it did seem to run longer without problem. When it does go black the LED on the monitor stays white, which tells me that the monitor doesn't go into the power save mode. The monitor is a Dell S2009W. I've looked into many other threads on this, and have checked: System>Hardware Drivers and it tells me there are no proprietary drivers in use. 
Any ideas would be appreciated. Thanks
[/SIZE]

---

### Post by jtarin on 2010-10-03
How do you get it to resume after this?

---

### Post by Old_Man_Unix on 2010-10-03
If that is an "out-of-the-box" 2350, it may not have enough RAM to run Ubuntu.

 Don't forget that part of your memory is scarfed up by the on-board video.  

Have you upgraded the RAM?  How much RAM does your system have?

The 8XX chipset is also problematic. See this

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes#Legacy%20Driver]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes#Legacy%20Driver")

---

### Post by ed_6678 on 2010-10-04
Thanks jtarin & Old_Man_Unix, I didn't realize this forum was that active.
To get it to resume I use Cntrl/Alt/Del. That starts me back at the login screen.
I did add RAM a while back, pretty sure I have 1GB installed.
Thanks for the link, I did the Install PPA Packages & Disable KMS, I hope that's what you meant for me to do. I'll give that a try and let you know how it works out.
Thanks again.

---


---
title: "Display issue ATI Radeon Xpress 1250"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by BugBuster on 2009-06-08
Hi All,

I have searched the forums extensively for a solution to a display problem that I have been having with Ubuntu since Hardy..

When I play movies, especially Xvid/Divx, I have this band of white horizontal white lines that are displayed at about an inch from the top of the screen.The band is about a centimeter thick vertically.

I have an Acer Al1916W monitor with ATI Radeon Xpress 1250 onboard graphics. In hardy I used this card with the fglrx drivers but now in jaunty i used it with the open source drivers in the repos.

In jaunty the problem is not that much as it was in hardy, but the lines are still there, so would like to get rid of them with your help.

I do not have any xorg.conf and its running with the auto detected settings in jaunty.

---

### Post by Mark Phelps on 2009-06-08
You're pretty much stuck in terms of drivers.  You can do "man radeon" in a terminal and get a list of parameters associated with the open source radeon driver.  You can also experiment with different video settings in the multimedia player.

Finally, you could go to the Phoronix forum and search their threads to see if anyone has found anything that specifically fixes this problem.

---


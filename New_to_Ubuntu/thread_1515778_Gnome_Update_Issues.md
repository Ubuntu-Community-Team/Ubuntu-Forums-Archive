---
title: "Gnome Update Issues"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by DevWolf on 2010-06-22
So, I'm pretty sure that I've got this in the right forum, consider I know next to nothing about Linux, Ubuntu, or command line. 

So, first off. 
I installed Ubuntu on an old beater of a laptop I got for free. Basically was told if I could fix it up, I could have it. So, right off the bat, bought a wireless card, and got the battery working, and got a new HDD for it. 
Here's the CURRENT specs:
Thinkpad T20
IDE 30 GB HDD 
SMC Wireless Card
256 MB of RAM

So, my first issue was that after downloading Ubuntu, it wouldn't shut down, I'd get an I/O error in several sectors. I bring this up only because I don't know if it's connected to my current issue. 
This was before I got the new HDD. So, I figured it was because the disk was going bad (it was). So I installed the new HDD, and tried again, and got the same sort of problem. I'm not sure if it was in the same sectors though, but they were I/O errors. 
So I figure I'll use the update manager, and see if updating Ubuntu would fix the problem. 
Now the Shut down issue is gone, but upon start up, it said something along the lines of FIFO not running right, and then when I logged on, several errors popped up, saying several components of GNOME cannot run. 

I'm missing the entire bottom portion of my task bar, I have no trash basket, and my windows are not showing up as the little... info box thingers on the bottom. 
How do I fix this? I know I need to somehow delete the right components, but I'm unsure which ones I need to get rid of, and how to reinstall them. Should I just try to run a reinstall of Ubuntu, and see if the update manager corrupted the GNOME files?

---

### Post by tango_ninja on 2010-06-23
Hmm.... 256 MB RAM is lower than the suggested [System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements").  Perhaps a lighter weight version, such as [Xubuntu]("http://www.xubuntu.org/"), would perform better?

But before you go there, have you checked to ensure the proper drivers are enabled?  Navigate to System > Administration > Hardware Drivers and enable any suspect drivers.

---


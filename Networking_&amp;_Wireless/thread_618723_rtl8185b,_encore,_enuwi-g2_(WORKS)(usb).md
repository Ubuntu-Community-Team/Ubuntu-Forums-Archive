---
title: "rtl8185b, encore, enuwi-g2 (WORKS)(usb)"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by sgt_urankar on 2007-11-20
I got it to work finally after about a week or so of trying.  Thanks for all the good resources.  I got it to install on fiesty, at first it was running rough.  Then I did 4 0r 5 re-installs of the os to make sure that what i did worked.  Today I can say that i have not had any issues with downloading anything,  I did a complete update of kubuntu, and install all the packages for ubuntu along with getting the 3d desktop installed and working.

With this device I found that the XP-32bit from the install cd work the best. All i did is as follows:

1 Install ndiswrapper from the dvd ( i used the dvd) in package manager.  Make sure to use all the packages I think there were 2 or three, and then wifi tools.

2 from the supplied cd copy the 2 files from the win xp dir to desktop (or where ever you normally put them.

3 cd to dir where you copyed them

4 (commands I used):
   sudo su
   ndiswrapper -i Net[tab complete] [enter]
   ndiswrapper -m (creates an alais for the driver)
   ndiswrapper -l (check to see if it installed)
   modprobe ndiswrapper
then connect to the net.  I kubuntu use the icon in the bottom right corner that looks like a light switch.

After all that I was picking up 2 wireless networks one in my house and my neighbors.  

I hope this works for the rest of ya!

---

### Post by sgt_urankar on 2007-11-20
my bad! had a typo that is rtl8187b

---


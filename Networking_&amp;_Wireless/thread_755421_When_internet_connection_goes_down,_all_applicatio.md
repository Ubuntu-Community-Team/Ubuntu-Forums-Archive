---
title: "When internet connection goes down, all applications are slow to load"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by Levander on 2008-04-14
I connect to the internet via a router my computer is connected to.  When my ISP is having problems and I can't connect to the internet, starting up applications is very slow.  Even when I'm starting something that has nothing to do with the internet, like a terminal window, it takes like 30 seconds to a minute for it to open up.  This is for all applications I've tried.  The internet connection comes back up without me rebooting or anything, and the applications start up in a blink of an eye.

Anybody know what causes this?  How to fix?

---

### Post by dchatterjee on 2008-07-05
Well try this...

system->administration->network

unlock it(if required)

click the wired connection option. -> click propertise-> in the configuration section select
"local zeroconf network(IPv4 LL)

then try opening any application i guess it will help...

---

### Post by Levander on 2008-07-06
This was so long ago, I barely remember what I did to fix it.  I think it was some networking thing I had to go into a text file and change.  

All it would take to test your solution is to run the init.d script to shutdown networking, then Ctrl-Alt-Backspace to kill X, relogin to GNOME, and fire up some applications.  If they're slow, try your solution.  If they speed up, it sounds like you fixed it.

I may try this tomorrow.

I'm trying to remember what it was...  It was like there was a GNOME service that no one really uses.  I think the service was really more for laptops and I'm on a desktop.  I'm pretty sure I turned off that service and the problem went away.

---


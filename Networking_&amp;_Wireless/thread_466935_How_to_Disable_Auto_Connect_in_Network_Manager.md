---
title: "How to Disable Auto Connect in Network Manager?"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by lifeempowered.com on 2007-06-07
I'm in an environment where there is a LAN and next door a WiFi.  The Wifi is open and non-secured, but it's one of those FON networks where you pay per month to access.  So, what's happening is my system, when I first log in, is trying to favor the wifi instead of the LAN, then I'm not getting the Net.  I have to manually disable Wifi at that location and then turn it back on when I'm home.  Very annoying and it seems there should be a way to either A: tell Network Manager to NOT auto connect or B: tell it to favor LAN for Internet traffic if LAN is available.

Anyone?

---

### Post by Atomic Dog on 2007-06-07
You can keep NM from connecting to that wireless by clicking Applications-->System Tools-->Configuration Editor.  Expand the system tab, expand networking, expand wireless, select the offending wireless name.  Right click on all the keys and select Unset Key.

This should stop NM from auto connecting to it.

---


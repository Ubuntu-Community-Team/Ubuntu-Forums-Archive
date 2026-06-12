---
title: "Ubuntu 7.04 appears connected, can't communicate"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by SWcisel on 2007-10-09
Hi guys,

I've read several posts that appeared similar to mine, but no fixes I've come across will do the trick for me. I'm trying to connect a Belkin F5D7050 to an unsecured wireless network. I've installed ndiswrapper, and confirmed that the drivers for the device are correctly installed. ndiswrapper is set to run at startup, and is linked to wlan0. I can plug the device in, and I can see the network when I left click the network connection icon on the top right side of the screen. When I attempt to connect to the network, I get "preparing device wlan0 for the wireless network <network name>", but it must be unable to connect. I'm getting > 84% signal, and I'm positive that the wireless adapter works (connected with it now via windows). 

I genuinely wish that I could copy and paste outputs of lspci, etc. However, I have no wired connection with which to post this. 

Any help would be greatly appreciated.

---

### Post by kevdog on 2007-10-09
Try this link to see if you can make a manual connection (just to see if everything is working).  Its not a long term solution but it may help troubleshoot your problem:

[http://ubuntuforums.org/showthread.php?t=571194](http://ubuntuforums.org/showthread.php?t=571194)

---

### Post by SWcisel on 2007-10-09
Wow, you must be on to something. I was able to connect VERY briefly (i loaded google just fine, but then after refreshing, I got nothing). 

That's a step in the right direction

anyone know what my next step would be?

---

### Post by kevdog on 2007-10-09
did you get anything in the terminal when it crashed??

can you ping yahoo or another site???

are you really far away from the router and the signal dropped -- check ifconfig for signal strength -- if it 15 or below probably what happened.

do you still have an ip address assigned?? can you ping router??

---


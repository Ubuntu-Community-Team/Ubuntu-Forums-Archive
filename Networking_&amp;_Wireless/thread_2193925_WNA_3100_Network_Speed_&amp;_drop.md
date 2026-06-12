---
title: "WNA 3100 Network Speed &amp; drop"
date: 2013-12-15
forum: Networking &amp; Wireless
---

### Post by dminuth on 2013-12-15
Hi, kinda of a linux noob here, got ndiswrapper 1.58 installed just fine, got the bcmwlhigh5.inf install, ndiswrapper -ma and modprobe all done and wireless is working... Kinda.
I am using it right now to write this and i have no option to use the wired network.

My problem is as follows.  The internet connection on here works just fine as long as i am not attemtping to either download anything big or try to do updates.  As soon as a somewhat bigger transfer is needed, the internet connection only on this pc still shows active but seems like speed is 0.  When that happens, nothing downloads, i cannot access any webpages, no access to my ssh tunnel to my small game server or anything network related.  
The wireless indicator still says connected to the net and the router and everything else attached to it still have internet but my machine.  I have tried ndiswrapper 1.57 /1.58 /1.59 all give me the same result.  I have searched for a linux friendly driver for the netgear wna3100 V1 but bcmwlhigh5.inf is the only 1 I can find.

I am assuming that it is either some kind of setup/config that i am missing or something wrong in the driver all together.
Can some1 give me a little light here pls.

---


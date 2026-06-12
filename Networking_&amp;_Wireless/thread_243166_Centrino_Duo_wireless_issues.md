---
title: "Centrino Duo wireless issues"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by rbrugman on 2006-08-24
Hello,
I just got a new Thinkpad R60 with the Centrino Duo chip.  Wireless works fine, but I cannot get Network Manager to load.  It says the daemon is running, but I can't launch nm-applet manually or via the "startup programs" in sessions.  Does anyone have any suggestions on how to get this to work?

I also tried installing the ndiswrapper and probing a few modules to no success.  It's funny that wireless works but NM won't.  I'm running the 656 kernel with SMP support.


Robert

---

### Post by SimonJW on 2006-08-24
Is it possible that you haven't install the network-manager-gnome package, and have only installed the network-manager package? Check in Synaptic. The network-manager package would include the daemon, but not UI to control it

I think there's also a network-manager-kde, if that's your poison ;)

Post back if that works, or if that's not the problem

---

### Post by rbrugman on 2006-08-24
No.  I installed the gnome package as well.  Nothing.  I even installed the debug packages to see if it would spit out any errors.  When I try to launch nm-applet manually it just sits there...never loads, but also never exits.

I'm confused.

Robert

---


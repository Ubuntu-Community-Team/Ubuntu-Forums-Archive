---
title: "why are there so many network config files?"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by deadowl on 2007-10-23
I can deal with xorg.conf, but seriously, there are way too many network configuration files. I'm trying to solve a problem and I'm confused as hell.

PROBLEM ONE: eth1 wireless, running through ndiswrapper, does not go up on start up. I don't know where I need to specify this in config files.

PROBLEM TWO: vpnc extension for nm-applet isn't communicating with keyring manager.

---

### Post by deadowl on 2007-10-23
Problem 1 is resolved, turns out I was loading ndiswrapper on the fly rather than at boot.
Problem 2 is still a problem

---


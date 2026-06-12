---
title: "Atheros wireless drivers: installed, enabled, inoperative?"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by mcovington on 2008-07-05
Toshiba laptop, Atheros AR5007G wireless network adapter (which definitely works under Windows), Vista/Ubuntu 8.04 dual-boot.

I'm new to (modern) Linux although I used to administer Solaris systems.

My problem is that wireless networking does not work.

System > Administration > Hardware Drivers shows two proprietary drivers (the card itself and a hardware layer), enabled and in use.

The wireless connection is not shown in the network administration tool.  The wired connection is shown, configured, and works.

The command "sudo lshw -C network" shows this device as "*-network UNCLAIMED" and its configuration is shown only as "latency=0" with no driver information.

Confusingly, Ubuntu doc. says to use "sudo lshw -C network" because the device may not be "turned on".  How do I interpret the results and what do I do if it's not turned on?

Ubuntu doc. also refers to System > Administration > Device Manager, which is not on the menu.

What should I do next?  Wireless networking is not mission-critical for me but will obviously keep me from using Linux as much as Windows.

---

### Post by mcovington on 2008-07-05
Found a thread apparently answering the same question, and will try it:
[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

---


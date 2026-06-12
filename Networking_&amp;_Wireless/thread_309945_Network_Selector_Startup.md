---
title: "Network Selector Startup"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by johndoe32102002 on 2006-11-30
I am unable to get the "Network Selector" starting up. I use it from switching from one to another wireless network. So far, in Edgy, it is the only software that successfully does what I need. What is the command to startup this program? I want to add it to:

System --> Preferences --> Sessions --> Startup Programs --> Add

Command line:
<Network Selector name here>

I need to know the Network Selector's name to startup the program. Also, is there a location where all the short names for all the programs can be found? This would be useful for going into terminal to start/install any program.

Thanks,
John

---

### Post by kcox5342 on 2007-01-16
Thanks to your information about how to add programs on startup, that was something I didn't know.  I just found Network Selector in Applications -> Internet, right clicked on it, added a launcher to the desktop, then I right clicked on that desktop icon and looked in the Properties.  The rightmost tab is "Launcher", the middle line is "command:", it says it's called "**netapplet**".  To make sure this is the one we wanted, I entered "man netapplet" in Terminal, and it sounded good, so I added it to the startup list, rebooted, and it appeared in the menu upon restart.  I still have to select the wireless network manually, though, but this is at least one less step I have to do upon booting.

---


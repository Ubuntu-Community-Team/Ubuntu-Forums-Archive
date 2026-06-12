---
title: "D-Link DWL-520 E1 refuses to work."
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by DizzyBum on 2007-09-12
I'm running Feisty.  I've tried every solution I've read on this forum, the wiki, and otherwise, to get my wireless card working:

- Using HostAP drivers
- Blacklisting HostAP drivers and using wlan-ng
- Using the latest version of ndiswrapper with Windows XP drivers

NOTHING works.

I can't apply any changes to the card using iwconfig.  It spits errors back at me that I can't find any info on anywhere.  If I blacklist hostap drivers, the wlan interface isn't automatically configured, and Ubuntu acts like the card's not there (although it does show up in that command that lists installed hardware which I can't recall off the top of my head).  Also, there's plenty of misinformation spread around; I thought I had to blacklist drivers in a file called /etc/hotplug/blacklist for a very long time until I  discovered it was actually /etc/modprobe.d/blacklist.

The closest I can get is using the HostAP drivers.  I can assign an ESSID using the graphical networking interface.  If I use any other solution, the interface ends up thinking that wlan0 is a wired connection and refuses to connect or make any changes to the card's configuration.

At this point, I'm giving up researching this.  It's too frustrating and I've wasted days on trying to figure it out.  I either need a solution that actually works, a tip that shows me I have something configured incorrectly, or a suggestion for a wireless USB adapter that works out-of-the-box in Linux and WinXP without having to go through all this ridiculous hassle.

Any advice?  If someone can help me figure this out, I would gladly write an updated summary on getting this thing working in Feisty.  If not, well... it's not like I wanted to stick with 802.11b forever...

---

### Post by BRAiN8 on 2007-10-27
any luck yet wit ur 520 e1?

---


---
title: "Saving a location in network settings"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by damnhappy on 2006-09-30
I have Ubuntu Dapper 6.06 LTS on an HP Pavillion zv5000. I use the built in Broadcom bcmwl5 wireless card with ndis wrapper. It usually works fine. The only problem is that when I reboot I can't get to the internet. 
I created a "Home" location in the network settings. The only way I can get back on the internet is to open Network settings and choose "Home" from the drop-down menu for location. Whenever I open Network settings this drop down menu is blank. "Home" is the second entry beneath the blank. This is true if I reboot or whenever I open Network settings. 
So my question is can I save "Home" to be the default location?  I looked in /etc/gnome-system-tools/network/profiles.xml and ther doesn't seem to be anything I can see that would set this to be the default. 

Thanks,

---

### Post by Parama on 2006-10-13
Just a post to tell you I have the exact same problem. 
I have also created a place (called "Basecamp") but it doesn't get selected by default either, even though it's the only selectable/managable network profile. I have also checked the /etc/gnome-system-tools/network/profiles.xml file, which holds just this one profile.
I'll get back to you when I find a solution - or read yours if you get there first :-)

---

### Post by Xama on 2006-12-11
Network "Locations" otherwise known as Profiles simply DO NOT WORK ... on Ubuntu ... I have tried creating profiles before and they either disapear or something else happens ... I gave up. It is simply a broken part of the system.

---


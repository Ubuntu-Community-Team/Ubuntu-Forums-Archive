---
title: "How do I get the wireless card to connect on boot???"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by Galactus on 2006-07-27
I am another Linux noob looking for a bit of help. I have Dapper 6.06 installed and working with just a few hiccups on my HP ze4805us laptop. The wireless is Broadcom 4306. I was able to get it working using the command line and NDISWRAPPER (thanks to the community forums :p ). 

The problems I am now having is that the wireless connection will not start up when I boot the computer. When i first boot up my wireless connection eth1 does not appear. I have to go into NDISWRAPPER and remove the wireless driver and then reinstall it. Then eth1 appears in the network config. I deactivate eth0 (wired connection) and activate eth1 (wireless) sometimes it connects on the first try sometimes not. A couple of times my system locked up and I had to do a hard reboot. 

Is there any way to get the wireless connection to "start/load" on boot up. My wife is not going to go for having to play around with drivers and network config when she wants to use the internet.

Thanks

---

### Post by x64Jimbo on 2006-07-27
You could put a script to start it up in your startup.
Gnome: [I]System - Preferences - Sessions - Startup Programs
[/I]KDE: [I]~/.kde/Autostart
[/I]

---


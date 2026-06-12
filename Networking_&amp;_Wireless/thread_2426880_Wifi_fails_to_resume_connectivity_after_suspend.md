---
title: "Wifi fails to resume connectivity after suspend"
date: 2019-09-15
forum: Networking &amp; Wireless
---

### Post by ranneyo on 2019-09-15
Xubuntu LTS 18.04 fully updated, on Dell laptop.  New problem within the past week, probably following an update.  
After resuming from suspend, network manager shows I am still connect to my wireless router, but I have no connection to the internet.  From another device I can confirm that the router is working normally.  A reboot restores normal operation of the laptop.
This thread, [https://ubuntuforums.org/showthread.php?t=2384252](https://ubuntuforums.org/showthread.php?t=2384252), now closed, contains some solutions which I have tried. However, I have noticed that running (as root) the command 
[COLOR=#000000][FONT=&amp]echo 1 > /sys/bus/pci/rescan[/FONT][/COLOR]  
after waiting until several minutes from resuming does usually restore the connection, but does nothing if I run it during the first few minutes after resume. It's a great nuisance, and since I had no problems for the 18 months I have run the system, I believe the bug has been introduced by a recent update.  I installed a new update yesterday, but that did not fix it.

---


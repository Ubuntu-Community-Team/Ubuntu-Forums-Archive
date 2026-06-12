---
title: "[SOLVED] Printer and File sharing"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by weemooseus on 2007-06-22
Ok, finally got my new Ubuntu up and running, would like to share my windowsXP printer and folders. I have enabled Samba and when I look at the network, the windows machine shows up, I have enabled file and printer sharing on it.

However, when I click on the XP machine, it doesn't show anything other than saying "the folder contents could not be displayed". I have no firewall on the Ubuntu machine, and the firewall on the XP is configured to be off for the local network. When I try to install a printer, it does not make the network connection.

Help:confused:

---

### Post by weemooseus on 2007-06-28
I now have my network up and running, can share files and print. Although there are some minor issues yet, I did get Samba working. 

One of the items to note is that the windows firewall I use is ZoneAlarm, even though I had the trusted zone open to access, I still had to add the IPs and names to the Zones part of the firewall. I added each user on the Ubuntu machine.

To configure Zone Alarm, right click on toolbar icon, click on "Restore ZoneAlarm Control Center", then turn off the trusted zone security, then click on the Zones tab and add the IP of your Ubuntu machines.:KS

---

### Post by spartan778 on 2007-07-03
what exactly did you do to solve this problem? Please help me because I think I am having the exact same problem as you.

---


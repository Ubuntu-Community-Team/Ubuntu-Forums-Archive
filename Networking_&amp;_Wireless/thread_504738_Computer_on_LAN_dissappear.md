---
title: "Computer on LAN dissappear"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by Chunen on 2007-07-19
Hello,

We have 5 Ubuntu 7.04, 1 embedded Linux D-Link NAS, 1 Windows Vista &  1 Windows XP on our LAN.
Every few days all computers disappear from the network; and re-appear after 24-48 hours.

Background:
[LIST=1]
[*]Windows Networking has been enabled on all computers.
[*]Workgroup is set to MSHOME
[*]There is no domain controller on the LAN
[/LIST]



Your help would be much appreciated.

---

### Post by chriseo22 on 2007-08-22
I am having the exact same problem with my LAN, the other two computers on my Network seem to randomly disappear (especially when needed).  I find restarting the computer or reconnecting to the network sometimes work, but it is getting to be a real hassle.  I would really appreciate it if someone has a much more practical solution than patience.

inconveniently,
Chris

---

### Post by chriseo22 on 2007-08-23
I have now found a fix for anyone else who has this problem.  If the network computers do not appear in the Network folder simply figure out what the IP Address of the computer you are trying to access, in my case 192.168.0.100, then simply put in the Location Bar:

smb://(The IP Address of the Computer)

in my case it was

smb://192.168.0.100/

I hope I helped,
Chris

---


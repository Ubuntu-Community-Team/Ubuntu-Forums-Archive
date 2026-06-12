---
title: "Problems with ndiswrapper (Feisty, BCM4310)"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by dspinell on 2007-06-22
Hi,

I am a new Ubuntu user (Feisty on a Dell Latitude D620), double boot (temporarily) with windows XP. I had my wireless card BCM4310 UART (rev 01) working with bcm43xx but, since only 11M connection speed is supported, I installed ndiswrapper+bcmwl5 (Windows XP drivers). Everything works as long as I connect to unprotected networks. However, whenever I try to connect to a network with mac filtering (at my place and on campus at my university), Network Manager attempts to connect but it does not succeed. 

With bcm43xx it worked perfectly. The weird part is that it works by executing the following steps:
[LIST]
[*]Select "Connect to Other Wireless Network" in the Network Manager pop up window;
[*]In the "Existing wireless network" window, type any string in the "Network Name" field, and leave "None" in the "Wireless Security" field;
[*]Network Manager attempts to connect to this fictitious network. Open the pop up window with the list of wireless networks, select the wireless network that previously failed to connect and at this points it connects without any problem.
[/LIST]

Did anybody experience the same behavior? If so, do you know how to fix this?

Thanks for your help

---

### Post by dspinell on 2007-06-26
I solved the problem by uninstalling ndiswrapper and reinstalling the latest version (1.47) following this HOWTO

[http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1390+ndiswrapper](http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1390+ndiswrapper)

with the windows drivers downloaded from

[http://ubuntuforums.org/showthread.php?t=476612](http://ubuntuforums.org/showthread.php?t=476612)

Davide

---

### Post by Astura on 2008-03-12
This was like the exact post I've been searching for during the last 4 hours. :D

---


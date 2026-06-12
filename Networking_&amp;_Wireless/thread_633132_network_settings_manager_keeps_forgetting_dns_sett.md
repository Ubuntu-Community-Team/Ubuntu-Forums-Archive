---
title: "network settings manager keeps forgetting dns settings!!!"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by NaSiO6 on 2007-12-06
hi!
i use static ip for my comp..not dhcp
problem is that every now and then the dns settings in the network settings manager change and point to the gateway.

this happens even though i have 'saved the location'- the location gets unselected automatically.

does anyone have a solution to this?

thanks!!

---

### Post by kevdog on 2007-12-06
Have you made any changes to the /etc/dhcp3/dhclient.conf file??  Here is an example if you wanted to use OpenDNS as your DNS server for example:

[http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---


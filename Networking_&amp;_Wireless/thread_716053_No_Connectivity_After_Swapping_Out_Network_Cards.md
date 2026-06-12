---
title: "No Connectivity After Swapping Out Network Cards"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by KeirB on 2008-03-05
Running a 7.10 Server as a router I had replaced both its nic cards. The server box wasn't able to see much after that. At first, it seemed like everything was fine (**ifconfig** reported All Is Well), without the connectivity. After a reboot, the dhcp server reported a red [fail] during start up and **ifconfig** reported only the **lo** device. After a fair amount of searching I found the file :

**/etc/udev/rules.d/70-persistent-net.rules**

Containing the MAC addresses of both the old and new cards... the new cards had been assigned to eth2 and eth3.  I nuked the whole file and rebooted.

(I've been thinking that I should have just removed the obsolete entries, renamed 2 to 0 and 3 to 1, and done a **/etc/init.d/networking restart** instead... it's hard to shake the heavy-handed lessons grown from a decade of windows abuse...)

Up and running great now.

Hope others find this useful.

~Keir

---


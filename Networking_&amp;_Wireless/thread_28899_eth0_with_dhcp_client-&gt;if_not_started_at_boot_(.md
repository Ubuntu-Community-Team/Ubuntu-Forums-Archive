---
title: "eth0 with dhcp client-&gt;if not started at boot (ctrl+c)-&gt; say &quot;active&quot; even if its not"
date: 2005-04-22
forum: Networking &amp; Wireless
---

### Post by iomicifikko on 2005-04-22
hi, i usually use my eth0 card to connect via dhcp, that means that if i connect the ethernet cable at boot, the network configuration at boot its ok and everything is up and running. the problem is if im not connected during boot,  i press ctrl+c at the right time to avoid loosing time trying to find ethernet connection. the bad is the if i give a look at network properties it said that the eth0 card is active. this situation causes a few problems:

-If i run totem-xine it exit saying "ERROR: Could not determine network interfaces, you must use a interfaces config line"
-if i connect the ethernet cable, connection is not available

the only thing i can do to solve the problem is to go to network properties and "disable eth0", then im able to use totem offline and to automatically activate network if i use the cable.

when i used warty i had not these problems, the only difference between my warty and hoary installation is that i configured network during warty install process while  i decided to wait the end of hoary install process before configure network.

ps:i have also used eth0 to do a pppoe connection but i dont remember if i already had this problem before pppoe config.



any help appreciated, thansk!;)

bye

---


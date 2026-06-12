---
title: "Local Wireless Network Issues"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by leetcharmer on 2006-08-12
I have a D-Link DI-624 wireless router w/ Verizon FiOS.  As well as a Sony LocationFree TV router dealie, and both send out wireless signals, both are encrypted w/ WEP as same key, and broadcast on same different wireless channels.  My problem is this:

As of recent, Ubuntu on this particular laptop has been giving me problems with connectivity to my home routers, yet -- I can still connect to WiFi and WLAN access to neighbor and restaurant encrypted / unencrypted networks.

Ubuntu and Windows on other machines in the house connect and work fine to the local wireless network, and Windows XP on this laptop connects just fine to this network.  Any ideas what would cause Ubuntu (under multiple kernels) to suddenly stop working like this?

Thanks!

ALSO -- I'm on an eMachines M6805 in case anyone was interested.

---

### Post by leetcharmer on 2006-08-13
*bump*

can anyone point me in the right direction, plz?

---

### Post by Szarzynski on 2006-08-13
I have the same machine, and the same problem.  This link got the wireless working for a while, but not for long.

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+howto](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+howto)

Now, network manager only sees the wired port, and when I change my default connection to e1 - it never 'sticks.'  In other words, after I set the wireless connection to my default connection using the netrwork settings tool, then I close the tool, then go back to it, the wireless connection is not selected.

Another weird thing is that if I hardwire the laptop to my hub it will connect using the ethernet port - then after I disconnect the cable, I can connect using my wireless card.

Other weird stuff - I can use the wireless card to connect using windows xp running in Virtual Machine in Ubuntu.  And I can ping my router using network tools.  So the wireless connection seems to be fine - but I cant get all my programs in Ubuntu to use it.    

My router is set to mixed mode.

---


---
title: "Network Manager or Driver Problem?"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by Jargv on 2008-08-18
I'm having problems with the network manager (I think). The wireless internet access at my apartment recently changed security to WPA2. Now the network manager will intermittently lose connection and begin reconnecting. Sometimes the NM will be able to reconnect, but other times it will not and the only way I can make it get a connection again is to restart the computer.

I'm wondering if this is a driver problem or a problem with NM. When I run 'lshw -C network' I get the following information for the wireless interface:

*-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:cf:c6:b6:13
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.105 multicast=yes wireless=IEEE 802.11g

There is no section 'driver=...' which to my knowledge means that the driver is not installed. 

What can I do to fix this problem? Is this a driver problem or a NM problem?

Let me know if there's any more information I can provide.

-Jargv

---


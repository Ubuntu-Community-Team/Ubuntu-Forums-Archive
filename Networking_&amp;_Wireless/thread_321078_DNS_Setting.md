---
title: "DNS Setting"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by kjazz16 on 2006-12-18
I am having this issue with DNS entries keep changing. I am running Ubuntu 6.10 on my Dell D410 using onboard NetXtreme Ethernet PCI. I use it at work and we have a DHCP server here. I configure network settings with DHCP and i get an IP and DNS  IP adress correctly, but after a while my DNS changes to something totally irrelevant starting with a 74.x.x.x IP address. Our DNS is 10.x.x.x. Then , i had to do a dhclient on command to requets from DHCP to fix the issue. After that, like another hour or so, DNS changes back to 74.x.x.x. and I again have to do another dhclient. This cycle keeps going on and on.
I even reserved an IP address for my PC and used static IP address instead. I configured network setting with static DNS address, but again DNS addess changes back to 74.x address. and I am also curious why DNS entries are not specific to each network connections like Windows but rather just one DNS location tab for all the network connections ( NIC , modem, and wireless)? 
I even deactivated wireless connection in network settings just to make sure it is not getting DNS from a wireless network( even though wireless disabled, network taskbar icon still shows wireless signals which is another issue).
I need help with this issue as it is getting annoying being knocked out of network due to DNS so often. I also manually put DNS addresses in config file ( do not remember name of the file), but noticed entries there changes as well.
Thank you****

---

### Post by emdeem on 2006-12-18
It sounds like something else on your Ubuntu box is changing the DNS entries.  Are you running anything that would do this (such as a VPN client)?

---

### Post by Iowan on 2006-12-18
[http://www.ubuntuforums.org/showthread.php?t=317721]("http://www.ubuntuforums.org/showthread.php?t=317721")
[http://www.ubuntuforums.org/showthread.php?t=282034]("http://www.ubuntuforums.org/showthread.php?t=282034")

**dhclient ** may be requesting DNS server list from DHCP server. The above links have details involving **prepend** and/or removing **domain name servers** from the **request** line.

---

### Post by kjazz16 on 2006-12-18
No. I am not running VPN. I disabled wireless and modem. Couple of my other co-workers use Ubuntu as well, but they do not have the same issue. Must be due to they all using previous versions of Ubuntu. I am the only one using 6.10.

---

### Post by kjazz16 on 2006-12-18
DHCP server is configured to give out correct DNS addresses to the clients. Those DNS numbers that it keeps changing is irrelevant to our Network. There is no such DNS configured with that IP address or any IP address within our DHCP server configured for clients for that matter. I am thinking, even though I disabled Wireless, it still somehow detects a wireless network and changes DNS from the wireless. Maybe I should just kill dhclient process ever loading at all?

---


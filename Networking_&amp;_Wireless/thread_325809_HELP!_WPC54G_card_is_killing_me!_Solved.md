---
title: "HELP! WPC54G card is killing me! Solved"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by Achetar on 2006-12-26
Here is my situation. I have a Linksys WPC54G wireless card in my laptop. I am running Ubuntu 6.10. I have it to where the system finds the card, and it can find wireless networks, but it wont connect. Just so u know, I am using the Gnome Network Manager. It worked it out to the point that i could find the network, but not any farther. I think i need the firmware. help?:confused: ](*,) :confused: ](*,) :confused: ](*,) :confused:](*,)

---

### Post by Vorian on 2006-12-26
> **Achetar said:**
> Here is my situation. I have a Linksys WPC54G wireless card in my laptop. I am running Ubuntu 6.10. I have it to where the system finds the card, and it can find wireless networks, but it wont connect. Just so u know, I am using the Gnome Network Manager. It worked it out to the point that i could find the network, but not any farther. I think i need the firmware. help?:confused: ](*,) :confused: ](*,) :confused: ](*,) :confused:](*,)

Have you changed to ath1?

sudo dhclient ath1

---

### Post by Achetar on 2006-12-26
> **Vorian said:**
> Have you changed to ath1?

sudo dhclient ath1

When i do that it returns this:

[B]Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath1: ERROR while getting interface flags: No such device
ath1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
[/B]

did u mean eth1?

---

### Post by Achetar on 2006-12-26
I Tried using eth1 instead of ath1. It returned this:

[B]There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:16:b6:c2:e4:8d
Sending on   LPF/eth1/00:16:b6:c2:e4:8d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[/B]

oh wait, i have 2 Wifi cards, lemme tri using eth2

---

### Post by Achetar on 2006-12-26
Eth 2 returned this: 

[B]There is already a pid file /var/run/dhclient.pid with pid 5622
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth2/00:02:8a:7a:9b:56
Sending on   LPF/eth2/00:02:8a:7a:9b:56
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[/B]

---

### Post by riven0 on 2006-12-26
Do you know what version your card is, because there is a fix for ver 2 of WPC54G [here]("http://www.ubuntuforums.org/showthread.php?t=233565&highlight=WPC54G"). 

Otherwise, what happens when you do **iwconfig**?

---

### Post by Vorian on 2006-12-26
edit - redundant

---

### Post by Achetar on 2006-12-26
Nvr mind. It works now
Thnx soooooooooooooooooooooooooo much. I think it was using that that fixed it.
Thnx again.

---


---
title: "Can't get wireless connection after inital success"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by PaulFXH on 2007-09-09
I'm using a new MacBook (2.16GHz, 1GB RAM, Atheros wireless card) in a multiboot setup with various Linux OSes (including Ubuntu Feisty).
While wireless internet works absolutely perfectly when I'm in Mac OSX, it is troublesome to say the least in Ubuntu.
I first set up wireless in Ubuntu about 1 week ago and after some effort (using this [guide]("https://help.ubuntu.com/community/MacBook") and this [howto]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") from Madwifi) it did actually work without problems.
However, because of a problem I had in that the wireless connection had to be manually re-connected whenever I booted back into Ubuntu from Mac OSX I tried the wicd manager in place of Network-Manager.
Because wicd did not resolve the problem, I moved back to network-manager. Since then I have not been able to get a wireless connection from Ubuntu despite having gone through the same guides at least 10 times.
My wireless AP is wep encrypted and I always use the encryption key when trying to connect.
The problem, from what I can see, is that no DHCP "offers" are available.
Here's what I get when I type "dhclient ath0" in a terminal after connecting to an AP:
```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1c:b3:b4:9e:98
Sending on   LPF/ath0/00:1c:b3:b4:9e:98
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
As this is my first real experience with wireless it could well be that I'm making some silly errors. But it's strange that it worked the first time and not at all since then.
Would be grateful for some advice.
Thanks
Paul

---


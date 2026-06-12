---
title: "HH5 plus another router"
date: 2016-10-25
forum: Networking &amp; Wireless
---

### Post by Leechpool on 2016-10-25
Hi,
I have a Home Hub 5 which connects to the internet over my phone line. At the moment I have it configured as 192.168.1.1 and running DHCP.
I have a cisco e4200 running dd-wrt with its wan port connected to one of the lan ports of the HH5 and DHCP switched off on the e4200. I've set the HH5 to always give the e4200 the same address (192.168.1.79) and set this as the DMZ zone of the HH5. This I understand causes all external connections to go straight to the e4200.
The address of the e4200 is hub is 192.168.0.1 and I have a server connected to the e4200 fixed as 192.168.0.5 which provides DHCP to everything else I connect to it (GW 192.168.0.1 and DNS 192.168.0.5). It effectively uses the HH5 as a modem and all things I plug into the e4200 can access each other and the internet.
This is fine but I've run out of ports on the e4200. Is there anyway I can configure this to use the modem of the HH5 for internet, with the e4200 and HH5 connected and configured  such that all lan ports take their clients addresses from my connected PC running the DHCP server?
At present if I connect a client to the HH5 its given a 192.168.1.# address and it can connect to the internet but not my 192.168.0.# machines. Obviously, I'm limited by the settings on the HH5 as its provided by BT but I can do anything I want with the e4200....
Thanks for your help,
:D

---

### Post by Leechpool on 2016-10-25
Ok,
Think I've got it working. Connected lan on e4200 to lan on HH5. Switched of DMZ on HH5. Disable DHCP on both. Set HH5 to 192.168.0.1 and e4200 to 192.168.0.X. The DHCP server has an ip fixed by its network settings of 192.158.0.5 and sets GW 192.168.0.1 and DNS 192.168.0.5 for all clients; all appears to work. Had to configure firewall on HH5 to the same port forwards as it had been on e4200. So simple. Not sure why it eluded me so long....
Thought this might help someone.
Thanks

---


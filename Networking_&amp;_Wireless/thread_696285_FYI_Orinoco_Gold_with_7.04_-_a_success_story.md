---
title: "FYI: Orinoco Gold with 7.04 - a success story"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by icky.thoomp on 2008-02-13
Hi All,

I installed Ubuntu 7.04 on a Sony Vaio P3 laptop and have had some problems with getting an Orinoco Gold PCMCIA wireless card to connect to my ADSL modem/router/AP. Last night I got it to work. Here's how -

* installed PCMCIA card and verified using lspcmcia command that it was being found OK by the OS and that it is using the orinoco_cs driver. 
* Opened Network Manager and chose "Connect to Other Wireless Network", typed in the SSID of the AP and left the password as None (as I don't have any security other than MAC filtering on the AP)
* opened the admin page on the router/AP and went into the wireless section. I found the Orinoco card in the list of available clients and then added it to the ACL for MAC filtering. It then connected and got a DHCP address and I was done.

My main problem previously was that I had entered the MAC of the Orinoco Gold card to the ACL with the name "Vaio Laptop" when the card was actually calling itself "UNKNOWN". I'm thinking that this discrepancy was causing me the problem.

Hope it helps.

Cheers
Icky

---


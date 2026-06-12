---
title: "Very strange network settings overridden."
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by adamr on 2007-04-18
I have an edgy install with a wireless Broadcom chipset PCI card. The card works fine (as in, I can connect, surf the web etc) but the network settings in Ubuntu seem to act very strangely.

DHCP normally refuses to work from either of my wireless access points / routers, but seems to work manually, so under Administration > Networking, I have a manual entry set up. However, sometimes when I start up, I notice that the PC has connected to the other wireless network in the house (there are two, and both on different channels), seemingly through DHCP. If I check with ifconfig, it's connected on the 192.168.1.x subnet, whereas my preferred connection is on the other network on the 192.168.8.x subnet.

If it connects this way, and I check in Administration > Networking, the manual entry for my wireless card is still there (192.168.8.18 etc), but the eth1 interface is still showing on the 192.168.1.x subnet (in ifconfig) and the DNS entries I've had to manually enter are now replaced by 192.168.1.1 which I assume is the other access point dishing itself out via DHCP. If I disable the card and re-enable it (still in the Networking control app), it now joins the x.x.8.x subnet, but I have to re-enter the DNS settings.

Is there two separate configurations working against one another? How can I force it to use one rather than the other. How can I stop it overwriting my DNS settings?

(also I notice if I leave the PC idle with no network activity for a while, I need to disable/enable the wireless card to get connectivity back again).

---


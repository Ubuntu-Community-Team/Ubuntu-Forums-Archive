---
title: "Broadcom 570x Ethernet &amp; Ubuntu"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by Copps on 2006-10-04
My laptop has the Broadcom 570x Gigabit ethernet adapter installed, with Ubuntu 6.06.1 OS and the latest kernel.

The network performace is flakey at best and dmesg periodically comes up with "Link is down" messages. This also seems to cause a performance hang in Ubuntu where the system is not responsive.

I connect to the internet via a DHCP router from the home and the office. I have a couple of questions;

Are the in-kernal drivers in Ubuntu good enough to run the card? [http://www.broadcom.com/support/ethernet_nic/faq_drivers.php#97](http://www.broadcom.com/support/ethernet_nic/faq_drivers.php#97) makes mention of tg3 drivers, and there are some drivers for download at [http://www.broadcom.com/support/ethernet_nic/downloaddrivers.php](http://www.broadcom.com/support/ethernet_nic/downloaddrivers.php) - is it worth giving these a go?

Also, port speed seems to be set at auto negotiation. You can force 100M full duplex easily enough in Windows, which is what I'd like to do in Ubuntu as a troubleshooting step. How can I force the port speed?

Finally, any other ideas on troubleshooting this issue would be appreciated. It's getting to the stage where Ubuntu is only useable when I disable the network card, which makes it largely useless to me. I don't want to go down the route of trying another distro.

---


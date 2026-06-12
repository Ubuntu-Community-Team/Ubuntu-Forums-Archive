---
title: "udev.rules for two NIC's"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by grunf on 2007-05-19
Hi,

I have one network card and one wifi card on my laptop. I've put the following lines in my 10-custom.rules udev file:

KERNEL=="eth1", ATTR{address}=="00:18:XX:XX:XX:XX", NAME="wifi"
KERNEL=="eth0", ATTR{address}=="00:16:XX:XX:XX:XX", NAME="lan"

After reboot, eth0 interface got the name "lan", but eth1 was stil eth1. What seems to be the problem? BTW, I'm running Feisty.

Thanks.

---


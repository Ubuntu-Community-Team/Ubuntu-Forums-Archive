---
title: "dhclient crashes with ppp"
date: 2015-05-03
forum: Networking &amp; Wireless
---

### Post by francach on 2015-05-03
Hi,

I'm using ubuntu 15.04.

dhclient causes a segmentation fault when I try to log into my mobile 4G provider via ppp. But it works fine for an ethernet connection.

I stop NetworkManager and ModemManager before I start ppp using:

ppd call vodafone


The 4G modem itself works - i have tried it on a windows system.

Syslog output:

May  2 17:20:27 flap pppd[28820]: Script /usr/sbin/chat -vsf /etc/chatscripts/vodafone finished (pid 28821), status = 0x0
May  2 17:20:27 flap pppd[28820]: Serial connection established.
May  2 17:20:27 flap pppd[28820]: using channel 19
May  2 17:20:27 flap pppd[28820]: Using interface ppp0
May  2 17:20:27 flap pppd[28820]: Connect: ppp0 <--> /dev/ttyUSB1
May  2 17:20:27 flap systemd[1]: Found device /sys/subsystem/net/devices/ppp0.
May  2 17:20:27 flap systemd[1]: Started ifup for ppp0.
May  2 17:20:27 flap systemd[1]: Starting ifup for ppp0...
May  2 17:20:27 flap dhclient: Internet Systems Consortium DHCP Client 4.3.1
May  2 17:20:27 flap dhclient: Copyright 2004-2014 Internet Systems Consortium.
May  2 17:20:27 flap dhclient: All rights reserved.
May  2 17:20:27 flap dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May  2 17:20:27 flap dhclient: 
May  2 17:20:27 flap sh[28826]: Internet Systems Consortium DHCP Client 4.3.1
May  2 17:20:27 flap sh[28826]: Copyright 2004-2014 Internet Systems Consortium.
May  2 17:20:27 flap sh[28826]: All rights reserved.
May  2 17:20:27 flap sh[28826]: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May  2 17:20:27 flap kernel: [65940.166822] dhclient[28838]: segfault at 200 ip b73ca2f4 sp bf826340 error 4 in libc-2.21.so[b7388000+1b4000]
May  2 17:20:27 flap sh[28826]: Segmentation fault (core dumped)
May  2 17:20:27 flap sh[28826]: Failed to bring up ppp0.
May  2 17:20:27 flap systemd[1]: [email]ifup@ppp0.servic[/email]e: main process exited, code=exited, status=1/FAILURE

Does anybody know of a workaround for this problem?

Thanks,
Martin.

---

### Post by coffeecat on 2015-05-03
Mobile Technology Discussions is for chat about smartphones and tablets. You'll be better off here:

*Thread moved to **Networking & Wireless**.*

---


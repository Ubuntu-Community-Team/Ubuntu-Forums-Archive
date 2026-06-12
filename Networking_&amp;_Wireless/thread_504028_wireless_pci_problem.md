---
title: "wireless pci problem"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by highcliff on 2007-07-18
I use D-Link pci card for wirless and its configured OK and campatible with fawn feisty,but when i make ifconfig ath0 down and then up(in order to change my mac) i can't connect to my provider  i do every thing i know like:
/etc/init.d/networking restart
killall dhclient3 then dhclietn3( i know this from command"ps ax")
invoke.rc.d networking restart
that happen even i don't change my mac only make interface down then up and unless i restart my pc,i can't reach my provider router(but without changing mac address i can't connect to internet
i need your help

---

### Post by highcliff on 2007-07-18
may be this has the another face of the problem:
when i change /etc/network/interfaces and add:

hwaddress ether 00:00:00:00:00:00 ( new mac)
in order to change the mac permenently and reboot my pc and then use:ifconfig ath0, i found the old mac!

---


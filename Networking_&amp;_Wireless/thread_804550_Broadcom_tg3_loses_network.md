---
title: "Broadcom tg3 loses network"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by zwit on 2008-05-23
Hi all,

I've been stumped for a couple of days now trying to figure out what's going on...

machine Dell latitude D830 with Broadcom netExtreme
Hardy clean install.
Might be relevant : VMware WorkStation 6.0.3

I can connect to the network but after several minutes I lose this connection.
ifconfig shows like it's connected, hW-leds on the back are on and blinking (as they should).

I've already tried (with no luck) :

ethtool -K eth0 tso off
ethtool -A eth0 autoneg off rx off tx off

if I request a new DHCP lease I get the same IP but now the network is back (for a while).

wlan0 has no problems whatsoever !

Had no problems with 7.10

Thx for any help and/or info

---


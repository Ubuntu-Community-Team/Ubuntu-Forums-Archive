---
title: "Howto: WEP Authentication"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by Sipswitch_Peter on 2007-07-22
Greetings,

As I've just been fighting to get my laptop connected (again), I thought I would share what I've observed since WEP dosent appear to be adequately covered in this forum.

(Using Fiesty 7.04)

1. Keys must be entered in hex and in the format XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX
2. The authentication type must be specified: 'open' for open and 'restricted' for shared (this is something the graphical interface does not set)

Example entry for /etc/network/interfaces using shared WEP key:

iface eth1 inet dhcp
wireless-essid mywirelessnetwork
wireless key restricted 1234-5678-9ABC-DEF0-1234-5678-9A

Trial and error - deviating from those 2 rules resulted in no connectivity for me.  Not sure if it will apply to everyone.

---


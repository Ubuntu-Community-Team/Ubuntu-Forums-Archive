---
title: "Linksys WPC11 version 3 Wireless Card Help"
date: 2005-05-05
forum: Networking &amp; Wireless
---

### Post by O11Y on 2005-05-05
Hi, I was given a Lynksys WPC11 version 3 wireless card by a friend and I'm having some problems. The wireless card is detected when I put it in and appears in the networking configuration tool as "eth1". I've configured the device and it claims to be "activated" but it doesn't seem to be working and the networking icon on the task bar shows two blank computer monitors with a yellow warning sign.

---------------------------------------------------------------------------------------------------
My output from iwconfig is as follows:

lo    no wireless extensions.

eth0   no wireless extensions

eth1

IEEE 802.11-DS 
ESSID:  "77Howell" 
Nickname:  "Prism I"
Mode: "managed"
Frequency:  2.447ghz
Access Point: 44:44:44:44:44:44
Bit Rate:   2mb/s
Tx-Power=15dBm
Sesitivity:   1/3
Retry Min Limit:   8
RTS thr:  off
Fragment thr:  off
Encryption key:   0123-4567-8910-1112-1314-1516-17
Security mode:   open
Power Management:   off
Link Quality:   0/92
Signal Level:   68dBm
Noise Level: 122dbm
Rx invalid nwid:  0
Rx invalid crypt:  0
Rx invalid frag:   0
Tx excessive retries:  0
Invalid misc:   0
Missed Beacons:   0

sit 0   no wireless extensions
-------------------------------------------------------------------------------------------

The only immediate problems (using my severely limited knowledge of wireless networking) is the security mode which should read "shared".

Anyone have any ideas?

Cheers,

Olly

---

### Post by O11Y on 2005-05-05
sorry am an idiot, changed the security setting to read "restricted" and now it works perfectly, gotta love ubuntu :D

Olly

---


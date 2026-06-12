---
title: "Cannot connect to modem"
date: 2014-03-18
forum: Networking &amp; Wireless
---

### Post by doublerainbow64 on 2014-03-18
Hello,

I'm trying to connect to my Cisco EPC3212 Cable Modem to go online. It is working properly on my first laptop Kubuntu 12.04. It used to work on my second laptop Kubuntu 13.10. I can't remember to have changed anything, but it isn't working anymore on my second laptop. The configurations in the network-manager are just the same on the two computers. However on the second laptop, after I click 'connect' it takes a while and then it says 'ip configuration unavailable'. I configured both computers to use DHCP on ipv4 and ipv6.

What cmds should I run in terminal to get a log about what exactly is going wrong?

Thanks in advance,
doublrainbow64

---

### Post by Iowan on 2014-03-18
Frequently, a modem "locks onto" a MAC address, and won't acknowledge a second. You may be able to reset the modem (turn power off, leave it for a minute, power back on). This might be required each time you attach a different computer (or... attach a router, which would present a constant MAC address to the modem).

---

### Post by doublerainbow64 on 2014-03-18
Did the job. :) I had tried this before, but maybe I did not wait long enough. Thanks again!

---


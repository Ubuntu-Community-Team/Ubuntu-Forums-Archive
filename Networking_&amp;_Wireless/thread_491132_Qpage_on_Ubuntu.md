---
title: "Qpage on Ubuntu"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by sundevil04 on 2007-07-03
Hello Everyone,
I am very much a freaking n00b when it comes to anything Linux and Ubuntu.  I have Nagios up and going on a box where I also have an external serial modem for dial up.  I am trying to get up Qpage to dial out and send SMS messages in the event that my network is down.  I am having issues with the ttyS0 already being in use when I try to send a test message.  It seems as if the daemon doesn't want to let go of the serial port so Qpage can Dial out. Any ideas would be awesome!!!

Thanks!

Tony H

root@nagios:~/qpage-3.3# qpage Tony Test -i
giving up root privileges
new service: Verizon
locking /dev/ttyS0
/dev/ttyS0 already in use

---


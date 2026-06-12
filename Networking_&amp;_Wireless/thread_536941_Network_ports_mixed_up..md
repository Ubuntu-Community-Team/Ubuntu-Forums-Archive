---
title: "Network ports mixed up."
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by xcape on 2007-08-28
I just installed Ubuntu server 7.04 on a sun fire x2100 that has two nvidia network ports and two broadcom ports.  I can communicate with the server when I am connected to eth2 in the back of the server.  When I ssh to the server, ifconfig reports I am using eth3.  Any suggestions would be appreciated.

Thank you.

---

### Post by xcape on 2007-08-29
I solved the problem. 

I first went into /etc/iftab and manually assigned the ethernet devices their proper hardware address.

Second, I downloaded the latest driver from broadcom, compiled the source, and inserted the updated module.

After a reboot everything was working fine.

-xCape

---


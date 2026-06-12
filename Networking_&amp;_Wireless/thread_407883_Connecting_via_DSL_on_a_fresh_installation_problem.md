---
title: "Connecting via DSL on a fresh installation problem"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by pqnelson on 2007-04-12
OK, so I have an AlienWare sentia m3400 that I installed Ubuntu 6.10 on; however, I can't connect to the internet.

I have an older laptop that runs ubuntu 6.06 that can connect to the internet through this connection; could I simply copy/paste the ip address from that computer to my new alienware one?

---

### Post by pqnelson on 2007-04-12
My eth0 connection on the alienware laptop appears to receive packets but does not send them, if that helps any.

It doesn't have an ip address, subnet mask, or gateway too.

This is all rather confusing for me :(

---

### Post by pqnelson on 2007-04-12
Okay so I typed into my terminal:

~$ sudo dhclient eth0

and it gave me:

Listening on LPF/eth0/00:90:f5:4a:be:02
Sending on LPF/eth0/00:90:f5:4a:be:02
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - seleeping.

Hmm what now?

---


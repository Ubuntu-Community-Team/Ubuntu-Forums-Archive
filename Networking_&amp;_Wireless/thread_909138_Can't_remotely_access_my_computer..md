---
title: "Can't remotely access my computer."
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by mat28590 on 2008-09-03
Using Ubuntu Hardy Heron.
D-Link DI - 524 Router
Linksys Am200 Router
Intel 82566DC Gigabit Network Card

Web browsing and e-mails work completely fine.
Torrent's are very slow, a few kb's a second, network testing in vuze says "NAT Error - Connection to your computer refused"
Cannot access my computer via ssh or ftp from outside my home network (I CAN access my computer from within my home network).
OS Settings allow remote connections.
Ports have been forwarded on router.
ISP says they are not blocking any ports.

Please help. I have had this problem for so long, with both xp, vista and now ubuntu. 

Thanks

---

### Post by justleen on 2008-09-03
sounds like a NAT problem with your router/modem.
You need to tell your router what it should do with incoming traffic on port 22 (ssh).

---


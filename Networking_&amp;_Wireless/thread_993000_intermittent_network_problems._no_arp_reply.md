---
title: "intermittent network problems. no arp reply"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by awkward42 on 2008-11-25
since upgrading to 8.10 I've been having intermittent connection drops on my wired network.

The computer (name "argon") has a manual IP configured (192.168.1.67) but it seems that at no time does it reply to the router's arp who-has requests.

The network works fine for between 20 minutes and a few hours, and then fails to connect to anything for between 2 minutes and an hour.

I can see no difference in the "ifconfig", "ip ad" or "ip ro" setups on the computer using 8.10 and the one using 8.4 (name "nitrogen" manual IP 192.168.1.69) that works no problem.

The only difference I can see is that nitrogen is sending arp reply packets, argon isn't.

---


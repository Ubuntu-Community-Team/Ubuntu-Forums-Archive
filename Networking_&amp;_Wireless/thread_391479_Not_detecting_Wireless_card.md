---
title: "Not detecting Wireless card"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by Repoman1966 on 2007-03-23
I am new to Linux and have just installed Ubuntu 6.10. I can connect to the internet using my Ethernet connector, as that was found automatically.Unfortunately it hasn't detected my internal wireless Lan card. According to lspci my card is the following:

0a:05.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

What is the best way to get it installed?

---

### Post by Kobalt on 2007-03-23
Unfortunately I believe the IPN2220 doesn't have GPL drivers, which means you will need to use the proprietary drivers and the tool to use them, ndiswrapper.
Here is some [guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") on how to install ndiswrapper.

---


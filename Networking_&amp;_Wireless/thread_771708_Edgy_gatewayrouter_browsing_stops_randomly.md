---
title: "Edgy gateway/router browsing stops randomly"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by SilentMobs on 2008-04-27
Hi guys,
I am far from a linux guru and I've tried troubleshooting it on my own as far as I can.
I have a server set up at home as the gateway which handles the ADSL connection using a bridged modem. The server was originally a Dapper Drake install which I upgraded to Edgy a couple months ago.
The last 3 weeks however, browsing from the other(WinXP) boxes connected to it, the browsing stops randomly for anywhere from 10 seconds to several minutes. Strangely however, my downloads (either http or torrents) don't stop, and using ssh to the server and browsing via w3m works fine.
I've tried things like disabling ipv6, clearing out logs etc. Nothing seems to work.

---

### Post by superprash2003 on 2008-04-28
it could be a DNS Problem.. try changing the DNS servers of the other pcs to opendns - their server ips are 208.67.222.222 and 208.67.220.220

---

### Post by SilentMobs on 2008-04-28
I've tried multiple DNS servers already. The thing that I don't understand is why is the server about to browse perfectly while everything else craps out?

---


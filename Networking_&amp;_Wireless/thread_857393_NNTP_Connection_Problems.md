---
title: "NNTP Connection Problems"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by rpcutts on 2008-07-12
I have installed LottaNZB which is a GUI for HellaNZB.

It doesn't seem to be working properly and I'm not sure where exactly the problem lies. I have set up Port forwarding on my router and have tried disabling the firewall but when I start the software it seems fine (600KB/s) for a few seconds then drops to very slow speeds (20KB/s). When this happens my web browsing also becomes impossible due to slowness.

When I quit the software web browsing goes back to normal.

I went to [www.canyouseeme.org](www.canyouseeme.org) and it said port 119: connection refused
I also ran: nmap -P0 xx.xx.xxx.xx
This gave the following:

Not shown: 1710 filtered ports
PORT     STATE  SERVICE
22/tcp   open   ssh
80/tcp   open   http
119/tcp  closed nntp
1723/tcp open   pptp

despite having port forwarding set up and no firewalls on 119 shows as closed Could this be my ISP?

I ran nmap after closing the software because it will not respond when it is running I assume for the same reason my web browsing dies.

---

### Post by rpcutts on 2008-07-12
They had given me the wrong server address.
Strange how it didn't just refuse me access but just went super slow instead but there you go.

---


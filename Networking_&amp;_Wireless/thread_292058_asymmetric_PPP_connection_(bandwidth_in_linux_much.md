---
title: "asymmetric PPP connection (bandwidth in linux much lower than in windows)"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by Carlos Santiago on 2006-11-03
Hi. I have an Internet connection via an UMTS Wireless PCMCIA card (a Novatel Merlin U630 UMTS Modem). In windows I can get about 220Kbps in downstream and 50Kbps in upstream.
However in Ubuntu 6.06 (Dapper) I can only get 50Kbps in both directions. I try to increase the baud rate from the default 115200 to 460800 but nothing changes.

 - The connection between the PC and the card is PPP.
 - The modem accepts AT commands.

How can I make an asymmetric PPP connection in order to take advantage of the downstream bandwidth provided by my ISP?

I think this problem could be similar to ADSL modems that uses PPP to communicate with the PC, as for example USB ADSL modems, because as far as I know ADSL also has different bandwidths in upstream and downstream.

A 2nd question: 
After the PC is booted, this PCMCIA modem could came identified by /dev/ttyS0 or by /dev/ttyS4. If its /dev/ttyS* is different from the one that is configured on my /etc/ppp/peers/ppp0 file, I have to start my internet connection manually. Is there a way to force my modem to always have the same ttyS*?

Thanks for all help

Carlos

---

### Post by Carlos Santiago on 2006-11-03
Problem solved with

setserial /dev/ttyS0 spd_warp low_latency

Now the speed is equal on both systems

---


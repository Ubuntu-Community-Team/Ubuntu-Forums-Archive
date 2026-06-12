---
title: "Network Manager - how to automatize?"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by ais77 on 2008-02-16
I've set up my USB ADSL modem and bring it to live (I'm writing from Ubu 7.10 now).
One thing drives me crazy:
when I use 
$ pon dsl-provider  (as described here [http://ubuntuforums.org/newthread.php?do=newthread&f=136]("http://http://ubuntuforums.org/newthread.php?do=newthread&f=136"))
- nothing happens: in terminal I got one message
[I]$ pon dsl-provider
Plugin rp-pppoe.so loaded.[/I]

And no Internet connection... :(

plog gives me:
[I]$ sudo plog
Feb 17 02:08:23 sev77u pppd[5864]: Plugin rp-pppoe.so loaded.
Feb 17 02:08:23 sev77u pppd[5866]: pppd 2.4.4 started by ais77, uid 1000
Feb 17 02:08:23 sev77u pppd[5866]: sendPacket: send: Network is down
Feb 17 02:08:23 sev77u pppd[5866]: Exit.[/I]

[B]
BUT:[/B]

if I use **Network Menager** (there is menu Modem connections/Connect to dsl-provider via Modem...) -** it works**!

[I]$ sudo plog
Feb 17 02:13:20 sev77u pppd[6164]: CHAP authentication succeeded: CHAP authentication success, unit 523
Feb 17 02:13:20 sev77u pppd[6164]: CHAP authentication succeeded
Feb 17 02:13:20 sev77u pppd[6164]: peer from calling number 00:30:88:00:75:CE authorized
Feb 17 02:13:20 sev77u pppd[6164]: Cannot determine ethernet address for proxy ARP
Feb 17 02:13:20 sev77u pppd[6164]: local  IP address 91.76.89.225
Feb 17 02:13:20 sev77u pppd[6164]: remote IP address 91.76.88.1
Feb 17 02:13:20 sev77u pppd[6164]: primary   DNS address 195.34.32.116
Feb 17 02:13:20 sev77u pppd[6164]: secondary DNS address 212.188.4.10[/I]

Question is - [B]what different commands does Network Manager execute when I click  
Modem connections/Connect to dsl-provider via Modem...?[/B]
I want to place them in rc.local to get connection at startup automatically.

And what's wrong with pon dsl-provider? It should work but it doesn't.. :(

Thank you in advance.

---


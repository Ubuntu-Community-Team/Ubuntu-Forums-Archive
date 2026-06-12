---
title: "Issue with L2TP VPN, Ubuntu 14.04"
date: 2015-07-07
forum: Networking &amp; Wireless
---

### Post by randolph2 on 2015-07-07
I'm trying to connect to my school's VPN with L2TP over IPsec using this GUI application L2TP Ipsec VPN Manager. I'm having no issues when I'm on Windows 8.1. However, I'm getting an error message when I tried to connect on Ubuntu 14.04.

Here are the settings in both linux and windows:
[ATTACH=CONFIG]263071[/ATTACH][ATTACH=CONFIG]263072[/ATTACH]

I get the following message from the VPN manager:
```
Jul 08 22:34:05.083 xl2tpd[1480]: death_handler: Fatal signal 15 received
Jul 08 22:34:05.083 Stopping xl2tpd: xl2tpd.
Jul 08 22:34:05.097 ipsec_setup: Openswan IPsec apparently already active, start aborted
Jul 08 22:34:05.104 recvref[30]: Protocol not available
Jul 08 22:34:05.104 xl2tpd[10135]: This binary does not support kernel L2TP.
Jul 08 22:34:05.105 xl2tpd[10136]: xl2tpd version xl2tpd-1.3.6 started on randolph-linux PID:10136
Jul 08 22:34:05.105 xl2tpd[10136]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
Jul 08 22:34:05.105 xl2tpd[10136]: Forked by Scott Balmos and David Stipp, (C) 2001
Jul 08 22:34:05.105 xl2tpd[10136]: Inherited by Jeff McAdams, (C) 2002
Jul 08 22:34:05.105 xl2tpd[10136]: Forked again by Xelerance (www.xelerance.com) (C) 2006
Jul 08 22:34:05.105 xl2tpd[10136]: Listening on IP address 0.0.0.0, port 1701
Jul 08 22:34:05.105 Starting xl2tpd: xl2tpd.
Jul 08 22:34:12.569 ipsec__plutorun: Starting Pluto subsystem...
Jul 08 22:34:12.575 ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d
Jul 08 22:34:12.607 ipsec__plutorun: 002 loading certificate from randolph-linuxCert.pem 
Jul 08 22:34:12.611 ipsec__plutorun: 002   loaded host cert file '/etc/ipsec.d/certs/randolph-linuxCert.pem' (1074 bytes)
Jul 08 22:34:12.615 ipsec__plutorun: 027 bad right --id: does not look numeric and name lookup failed (ignored)
Jul 08 22:34:12.618 ipsec__plutorun: 002 added connection description "schoolvpn"
Jul 08 22:34:12.623 ipsec__plutorun: 002 added connection description "schoolvpn2"
Jul 08 22:34:13.626 ipsec__plutorun: whack: read() failed (104 Connection reset by peer)
Jul 08 22:34:13.627 003 FATAL ERROR: unable to malloc 9223372036854775807 bytes for private key
Jul 08 22:34:13.630 ipsec__plutorun: !pluto failure!:  exited with error status 1
Jul 08 22:34:13.630 ipsec__plutorun: restarting IPsec after pause...
Jul 08 22:34:13.632 whack: Pluto is not running (no "/var/run/pluto/pluto.ctl")
Jul 08 22:34:13.635 [ERROR  300]   'IPsec' failed to negotiate or establish security associations


```

Would appreciate any help. Thanks.

---


---
title: "didn't receive an Internal IP4 Address from ppp (VPN PPTP)"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by Blackhand on 2008-09-29
Hi, I'm trying to connect to Microsoft VPN using the Network Manager. I added a VPN connection, set it up correctly and it seems to connect, however, pppd reports that it didn't receieve an internal IP4 address.

I'm pretty sure this is incorrect as the line JUST above that error clearly assigns the IP.

This is just a snippet from the end of the log, there are no other errors further up.

```
Sep 29 22:13:53 blackhand-desktop pppd[12971]: Cannot determine ethernet address for proxy ARP
Sep 29 22:13:53 blackhand-desktop pppd[12971]: local  IP address 10.10.10.73
Sep 29 22:13:53 blackhand-desktop pppd[12971]: remote IP address 10.10.10.5
Sep 29 22:13:53 blackhand-desktop pppd[12971]: nm-pppd-plugin: didn't receive an Internal IP4 Address from ppp.
Sep 29 22:13:53 blackhand-desktop pppd[12971]: Script /etc/ppp/ip-up started (pid 12977)
Sep 29 22:13:53 blackhand-desktop pptp[12976]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
Sep 29 22:13:53 blackhand-desktop pptp[12976]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Sep 29 22:13:53 blackhand-desktop pptp[12976]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Sep 29 22:13:53 blackhand-desktop pppd[12971]: Terminating on signal 15

```

Ubuntu Hardy 8.04

Any ideas?

---

### Post by Blackhand on 2008-09-29
I did some further digging on this and found a bug report with a patch:

[http://bugzilla.gnome.org/show_bug.cgi?id=517468](http://bugzilla.gnome.org/show_bug.cgi?id=517468)

The description matches exactly the setup and problem I'm having.

Does anyone have a workaround until we see this fix implemented?

---


---
title: "trouble logging on with vnc"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by gene02 on 2007-05-20
I'm having some trouble logging on to the vnc server from a remote computer.  After entering my username and password, I am simiply returned to the username screen.  This shows up in the logs:

May 20 14:37:51 howler gdm[11375]: Sending QUERYLOGIN == <secret> for slave 11375
May 20 14:37:51 howler gdm[4286]: Handling message: 'QUERYLOGIN 11375 gene'
May 20 14:37:51 howler gdm[4286]: Got QUERYLOGIN gene
May 20 14:37:51 howler gdm[11375]: QUERYLOGIN response: :0,0 
May 20 14:37:51 howler gdm[11375]: Running gdm_verify_cleanup and pamh != NULL


Xvnc is being started by xinetd with the following arguments:
-inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -f /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd

This setup did use to work, so I'm not sure what's changed.

Anyone have any suggestions?

Thanks.

---


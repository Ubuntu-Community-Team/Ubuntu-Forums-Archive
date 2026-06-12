---
title: "Ubuntu 14.10 server no longer sees all Ubuntu clients via OpenVPN"
date: 2014-12-04
forum: Networking &amp; Wireless
---

### Post by Ulf_Dunkel on 2014-12-04
I run an Ubuntu server which communicates with various Ubuntu clients via the OpenVPN gateway. This worked fine so far, until I updated the server from Ubuntu 14.04 to 14.10. Now the server can only "see" a few clients via OpenVPN, while others can no longer be ping'ed, ssh'ed, etc.

I just did the usual "do-release-upgrade" on the server, nothing else. I didn't see any special notes for OpenVPN changes. The currently running version on the server is OpenVPN 2.3.2, while the clients have various versions of Ubuntu (from 12.01 over 13.10 up to 14.10) with various versions of OpenVPN.

What can I do to re-enable the server to accept VPN connections from all clients?

PS: The server and clients do **not** use any GUI network-manager. All OpenVPN stuff is done via scripts or Terminal access.

---


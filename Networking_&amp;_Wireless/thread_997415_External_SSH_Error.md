---
title: "External SSH Error"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by Yuki_Nagato on 2008-11-29
Setting up SSH.  A connection between two local machines works perfectly.  It is public key connection with password authentication disabled.

When I attempt to connect to that same machine, but instead of using the LAN IP address, I use the DYNDNS name (XXX.YYY.com), the connection is almost immediately refused.  I do this because I will need to access the machine from non-local locations.

The error states "connection refused."

DYNDNS and ddclient are working.  Checking my account against 3rd party IP checkers works out.

The router is forwarding the proper ports to the correct machine.

"iptables -L" shows the three sections with no entries, leading me to believe there are no firewall rules present.

Any other ideas as to what is refusing my connection?

---


---
title: "Best method to access multiple unbalanced network connections"
date: 2022-02-08
forum: Networking &amp; Wireless
---

### Post by Andrew_Welham on 2022-02-08
I'm running on ubuntu Jammy ubuntu servers (two separate servers with keepalived) as an internal router , and will have two internet connections (each with a router/modem)
1 x 70 MB with static IPs and local hosting
1 x 1.1GB single IP (traditional natting)

All inbound connections to the DMZ hosted service MUST come and go via the 70mb connection. The default route for these devices must be the 70MB connection

All general traffic should use the 1.1GB connection, except where the 1.1 GB connections is not available then the 70MB connection should automatically be failed over to. (or balancing across both of fine, but the balancing must be uneven given the difference i connection size.


Also is there is way to detect the connections availability/stats  (from the ubuntu router) without agents being installed on the router/modems.

I have seen some old docs about IP route2, but they are quite old.


What's the current recommended method for this

Kind Regards
Andrew

---


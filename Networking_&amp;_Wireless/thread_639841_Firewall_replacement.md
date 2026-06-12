---
title: "Firewall replacement"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by DarkHorizon on 2007-12-13
Hello all,

I am currently in the process of creating a drop-in replacement for the company LAN gateway/firewall appliance due to some of its limitations.

I have so far created my necessary forwarding rules for http(s), ftp, h323 (this was a pain!), and some security rules.

What I am currently faced with is enabling employees outside the firewall to remote into the network via Windows PPTP client. The current firewall in place authenticates PPTP clients against the Active Directory (Windows network!).

What I am having difficulty understanding is, how do PPTP clients typically connect to a network when a Linux system is the gateway? Does the pptpd pass-thru authenticate each client? Do I just need to port-forward or proxy incoming PPTP connections? Should there be a PPTP server running on the gateway, and it handles the bulk of the connections and give network access to the clients?

I don't know enough about VPN at this level, so any help/docs/tutorials/websites would be very helpful.

Best regards,
- DH

---


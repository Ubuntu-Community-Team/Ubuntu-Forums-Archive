---
title: "VPN/surfing the web setup"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by waterwheel2 on 2014-02-04
How do I set up a vpn under openvpn running on ubuntu so that sites on our internal network use the VPN connection, but access to a regular website like google goes through the computer's regular wired connection instead of the VPN?  Would like to do so by modifying the client, not the server.  Ive set this up on the past under mandriva and it just worked that way automatically.  I'm at the level of a trained monkey on this stuff so I can push a series of buttons but when it goes wrong, I don't even quite know what to Google :).  (Right now the client/desktop access internal sites correctly, but external websites are timing out, which I believe means they're going through the vpn.)

Thanks.

---

### Post by waterwheel2 on 2014-02-04
NM - I went into the 'ROUTES' tab under the VPN and checked off 'use this connection only for sites on this network.  Restarted the network, and it's fine!

---


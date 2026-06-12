---
title: "Really simple VPN setup?"
date: 2013-11-02
forum: Networking &amp; Wireless
---

### Post by 1clue on 2013-11-02
Hi,

The firewall/router is a Cisco/Linksys E4200.  It has NAT that works right, but unfortunately it doesn't handle DNS translation through NAT, and it has no VPN endpoint.  This is NOT my router, and it's 1400 miles away from me so I can't install another firmware like dd-wrt.  We're stuck with stock firmware.  The good news is it supports a DMZ, but whatever I put there has to work with NAT.

I have a single public IP.

I'm looking for something I can put on a VM that can act as a VPN with very little setup time.

Here's what I'd like:
[LIST=1]
[*]Don't trash/restrict the client's other network connections.
[*]Use the network's internal DNS while connected.
[*]Default access is granted through the vpn, with a list of equipment to disallow.
[/LIST]

Thanks.

---

### Post by SeijiSensei on 2013-11-02
I use point-to-point [OpenVPN tunnels with a shared static key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") for these tasks.  You can run OpenVPN as a client on a computer behind the remote router and have it set up the tunnel to any machine it can see on the Internet.  What you do with the tunnel obviously depends on the rules you write for routing, firewalling, etc., but it will be entirely invisible to anyone at the remote location.  It's a great arrangement when you need to communicate with a network far away since all the connectivity is handled at that end.

---

### Post by 1clue on 2013-11-02
I'll look into it, thanks.

---


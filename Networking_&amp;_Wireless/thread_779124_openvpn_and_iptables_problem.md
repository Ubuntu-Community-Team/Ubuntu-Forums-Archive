---
title: "openvpn and iptables problem"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by tigerknight on 2008-05-02
I am running a debian box at home with openvpn as a server, and my desktop at work is ubuntu connecting to it as a client.

My debian box has two physical interfaces - eth1 (external/public) and eth2 (internal/private). My home network uses the internal IP (192.168.1.3) as the gateway to the internet, with traffic going through iptables' masquerade rules and having some various portmaps setup for things like irc and torrents and etc.

openvpn server listens on the external interface (eth1) and is set to use ethernet bridging (tap devices), with eth2 having br0 laid down over it using the 192.168.1.3 address.

So far what I can determine is that connecting from the client to the server works perfectly, the client is assigned an address of 192.168.1.90 but traffic does not flow properly.

Using a basic ping and tcpdump it is apparent that traffic is flowing over the vpn tunnel, but fails to properly get handled.

In my system logs I am getting the following message:
"kernel: MASQUERADE: Route sent us somewhere else."

In my iptables scripts the following is what I use to setup masquerading and allow my network to access the world:
/sbin/iptables -t nat -A POSTROUTING -j MASQUERADE

It seems that the masquerade setup I have is directing traffic incorrectly so how should I re-write this to allow the vpn traffic to be directed back to where it should be going?

---


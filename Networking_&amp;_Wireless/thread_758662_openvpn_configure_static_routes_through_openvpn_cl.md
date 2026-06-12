---
title: "openvpn configure static routes through openvpn client virtual ip?"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by robklg on 2008-04-18
Hello members,

My first post here.

Well here's my dilemma...

I know that the way you normally add static routes is in /etc/network/interfaces. How to do so with OpenVPN tunnels?

My OpenVPN server accepts connections from several clients. My purpose is to make it possible to access one of the VPN client's network, from the gateway (and internal lan). For this I used client-config-dir in server.conf, and created a file for this client, containing its internal network: iroute 192.168.9.0 255.255.255.0

Now what I did next on the gateway, is to use route add -net 192.168.9.0/24 tun0

Now I can access the client's network through my OpenVPN server.

However, where can I permanently configure this route? I cannot use the /etc/network/interfaces, can I?

I think there must be a way to configure this in the OpenVPN server. But the iroute itself is not enough it seems. OpenVPN does not modify the routing table. So my server will just forward anything to that subnet onto the Internet (if I don't manually add this route).

How to get this working? So that when the client connects, the client's Virtual IP address is used as a gateway to its internal network?

I think it must be some trivial openvpn setting, but cannot figure it out.

---

### Post by robklg on 2008-04-21
Thanks for your help ;-)

I finally figured out the obvious solution...

Aside from the iroute I just needed to define 'route 192.168.9.0 255.255.255.0' in the server.conf. That way openvpn would add the correct route table entry to the kernel. A sample config entry is right under client-config-dir.

---


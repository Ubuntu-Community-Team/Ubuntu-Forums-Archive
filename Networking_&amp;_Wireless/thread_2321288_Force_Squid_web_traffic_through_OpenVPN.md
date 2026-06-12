---
title: "Force Squid web traffic through OpenVPN"
date: 2016-04-21
forum: Networking &amp; Wireless
---

### Post by darren35 on 2016-04-21
I have an OpenVPN server setup at an external site and a Squid Proxy server setup at home.

I'm trying to force all web traffic from Squid through an OpenVPN connection.

The reasoning behind this is to allow clients to conceal their identities behind the OpenVPN server's public IP without necessarily requiring them to setup an OpenVPN connection. This also allows simpler devices which are not OpenVPN/VPN capable to use some form of anonymity.

I've considered an obviously simpler method which would be to setup proxying on the external server but I'm trying to maximize security and I don't think a public Squid proxy is as secure as an OpenVPN server with 4096 bit DH, 256-AES and SHA-512 and certificates required for authentication.

I know the solution is probably very simple but please bare with me as I'm still fairly new to Linux servers.

Let's assume that the home Squid server IP is x.x.x.x/x and the external OpenVPN server IP is y.y.y.y/y for the purpose of this discussion.

Thank you!

---

### Post by slickymaster on 2016-04-21
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by darren35 on 2016-04-24
Bump

---


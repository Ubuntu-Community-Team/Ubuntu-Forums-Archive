---
title: "OpenVPN slow using Network Manager"
date: 2014-04-26
forum: Networking &amp; Wireless
---

### Post by naxiz on 2014-04-26
I've installed OpenVPN server on my Debian server with a 1 Gbps symmetric link.

At home I've 150 Mbps down and 15 Mbps up.

If I connect to my VPN using the Network Manager and go to Speedtest.net, I always get ~30 Mbps down, regardless of the server I choose.

But when I connect using OpenVPN directly (openvpn --config user.conf) I always get 150 Mbps down or even more (I think because I'm using compression). On Windows I get 150 Mbps down or more as well.

So why is Network Manager slowing it down so much? How can I disable this limit?

**Note:**
I've manually entered everything from OpenVPN's config file in Network Manager because Network Manager crashes as soon as I try to import it.

Some options were not available in Network Manager so I skipped them. I don't think they would make any difference but here they are:
```
resolv-retry infinite
nobind
persist-key
persist-tun
ns-cert-type server
verb 3
```

---


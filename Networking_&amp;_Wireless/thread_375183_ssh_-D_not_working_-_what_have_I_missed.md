---
title: "ssh -D not working - what have I missed?"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by Zelut on 2007-03-03
I am trying to setup a proxy for privacy and I am using the following steps:

local:
ssh -D 9000 remote.server
authenticates, connects

local:
I set, within firefox, to use localhost:9000 as the proxy.  I have tried setting as SOCKS4 and SOCKS5 or even just using localhost:9000 for http connections.

I get no errors when I connect via ssh or when I try to resolve a site via firefox.  However firefox does not resolve any web pages.

What am I missing here?

---


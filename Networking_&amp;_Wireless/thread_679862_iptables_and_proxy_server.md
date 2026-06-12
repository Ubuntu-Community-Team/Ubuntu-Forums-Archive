---
title: "iptables and proxy server"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by MarkCrossley on 2008-01-27
I want to ensure that all network traffic passes through a specific proxy.

After browsing many websites I've come across the following:

```
iptables -t nat -A PREROUTING -p tcp --dport 80 -i eth0  -j DNAT --to 
1.2.3.4:3128
```

Would this iptables command force all network traffic to go through the proxy 1.2.3.4:3128?

Basically I don't want to have to set up the proxy settings in every application I use. Additionally I don't want anyone to be able to change the proxy settings.

---


---
title: "Why is the IP all the same?"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by trigg3r on 2007-01-22
hi everyone, i would please love to hear your opinion on this. it's non-distro-specific, but i've already tested this on a Dapper server install, without success.

i have 3 available public IPs on a dedicated server. i installed a proxy there and made it listen to those IPs.

for example:

http_port 192.168.1.2:3128 192.168.1.3:3129 192.168.1.4:3130

then i proceeded to test this, setting a browser to use proxy on the 3 IPs. going to ipchicken.com or whatismyip.com, i expected to get the 3 distinct IPs to show. instead, these services give me an IP which is the IP of the server, the one really bound to the ethernet device not just as a virtual interface. and the IP that is showing is not among the 3 i use.

is this normal behavior if you use virtual interfaces? or am i missing something in the proxy configuration?

---

### Post by kidders on 2007-01-22
Hi there,

Your post is a little confusing.

> **trigg3r said:**
> hi everyone, i would please love to hear your opinion on this. it's non-distro-specific, but i've already tested this on a Dapper server install, without success.

i have 3 available public IPs on a dedicated server. i installed a proxy there and made it listen to those IPs.

for example:

http_port 192.168.1.2:3128 192.168.1.3:3129 192.168.1.4:3130

then i proceeded to test this, setting a browser to use proxy on the 3 IPs. going to ipchicken.com or whatismyip.com, i expected to get the 3 distinct IPs to show.Everything makes sense up as far as here, but then you mention virtual interfaces. :confused:

Your http_port example suggests you have three network adapters on your server. Is that the case?

---


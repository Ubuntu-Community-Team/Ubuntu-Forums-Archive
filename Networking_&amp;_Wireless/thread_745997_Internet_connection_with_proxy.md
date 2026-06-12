---
title: "Internet connection with proxy"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by OlivierJ on 2008-04-05
Hi,

I've just installed Ubuntu 7.10 Gutsy on a network computer but I cannot get access to the internet.  please see my config below:-

I've got a router with DHCP enable.

IP range 10.15.44.129 to 10.15.44.254

Subnet 255.255.255.128

Proxy 192.168.66.5 port 8783

I've put the proxy address in Firefox but I'm getting the following message:

Firefox is configured to use a proxy server which is refusing connections

I've also tried to configure a static IP:-

IP 10.15.44.130
Subnet 255.255.255.128
Gateway 10.15.254.254

but still the same message.  when I ping the router 10.15.254.254 i get a reply.

Please help...  :(

---

### Post by brian_p on 2008-04-05
> **OlivierJ said:**
> Hi,

I've just installed Ubuntu 7.10 Gutsy on a network computer but I cannot get access to the internet.  please see my config below:-

I've got a router with DHCP enable.

IP range 10.15.44.129 to 10.15.44.254

Subnet 255.255.255.128

Proxy 192.168.66.5 port 8783

I've put the proxy address in Firefox but I'm getting the following message:

Firefox is configured to use a proxy server which is refusing connections

I've also tried to configure a static IP:-

IP 10.15.44.130
Subnet 255.255.255.128
Gateway 10.15.254.254

but still the same message.  when I ping the router 10.15.254.254 i get a reply.

Please help...  :(

The proxy is on a different subnet. Is that your intention?

---

### Post by OlivierJ on 2008-04-09
HI,

actually the proxy server is for my ISP.  I've read somewhere that I should disable network manager.  How will i configure my network then??


P.S sorry for the late reply.

---


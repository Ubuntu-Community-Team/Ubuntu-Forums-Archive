---
title: "Setting up inline content filtering with e2guardian"
date: 2020-07-07
forum: Networking &amp; Wireless
---

### Post by albertcuy on 2020-07-07
Hi All,

    We are trying to set up an open source replacement. We mean to make it inline so as not to make too many changes to our network.

   So i've used this as a rough guide, and adapted it to use nftable for the packet mangling:

     [http://www.theopensourcerer.com/2014/04/how-to-install-a-squid-dansguardian-content-filter-on-ubuntu-server/](http://www.theopensourcerer.com/2014/04/how-to-install-a-squid-dansguardian-content-filter-on-ubuntu-server/)

It does work, however the result is that all web traffic is getting NAT'd to the filter's bridge IP address. On the other hand, our old web filtering box doesn't seem to do any NAT magic, it simply inspects the traffic and, if allowed, passes the packet along unmangled, i.e. source IP intact. Dunno how they did it, it seems technically impossible to forward the packet to the web filtering process w/o mangling it first.

    Any ideas on how to achieve this? This is the nftables script i used on the bridge interface:

BRIDGE_MAC=12:34:56:78:90:ab


nft add table bridge table1
nft add chain bridge table1 chain1 { type filter hook prerouting priority 0\; }
nft add rule bridge table1 chain1 tcp dport 80 meta pkttype set host ether daddr set $BRIDGE_MAC counter
nft add rule bridge table11 chain1 tcp dport 443 meta pkttype set host ether daddr set $BRIDGE_MAC counter


nft add table inet table2
nft add chain inet table2 chain2 { type nat hook prerouting priority 0\; }
nft add rule inet table2 chain2 tcp dport 80 counter redirect to 8080
nft add rule inet table2 chain2 tcp dport 443 counter redirect to 8443



Thanks

---

### Post by TheFu on 2020-07-08
And using a squid-proxy to filter isn't an option?

---

### Post by albertcuy on 2020-07-08
> **TheFu said:**
> And using a squid-proxy to filter isn't an option?


i'd consider that option, but my main issue is can't don't know how to pass those packets to the web filtering process, and then sending the original packet(with original source IP) back out if the filtering rules allow.

---

### Post by TheFu on 2020-07-08
squid becomes the filter and can be setup as a transparent proxy.  I'm probably missing some subtle requirement.

---

### Post by albertcuy on 2020-07-09
Sorry for the confusion. What i meant to do is set up a machine that will inspect all port 80/443 packets against a blacklist of sites/URLs. And, if it's allowed, pass the traffic along as is....as against a transparent proxy configuration where the source is NAT'd to the proxy's public IP.

e.g.

Client PC  ----- [src ip =Client] ---> In-line proxy ---> [src ip = Client ] 

as opposed to

Client PC  ----- [src ip =Client] ---> In-line proxy ---> [src ip = proxy IP ]

This is what i observed on the Lightspeed Rocket box we have at work. It doesn't NAT the traffic, it passes it along. i just can't wrap my head around how you can pass the packet without mangling it first to pass it up the filtering agent, then have the filtering agent put the packet in its original state out to the internet.


Thanks

---

### Post by TheFu on 2020-07-09
You can't for SSL encrypted traffic without performing a MiTM certificate setup and having a machine that all clients support as authorize certificate system.  I've seen this with Bluecoat setups, but most home users can't afford those "nation-state" level MiTM systems.  For typical home users, using squid as a transparent proxy + content filter is sufficient. Just be certain to not allow the client machines a route or DNS to the internet, so the only way out is through the squid machine.

But if you have your heart set on doing it using NF, I'll wish you good luck and hopefully someone else will respond who knows more.

---


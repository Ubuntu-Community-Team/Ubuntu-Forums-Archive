---
title: "Docker frames/packets escaping host with docker local ip still set"
date: 2021-06-01
forum: Networking &amp; Wireless
---

### Post by molotch2 on 2021-06-01
Hi,

I have this peculiar problem I haven't been able to understand and it's driving me nuts. :)

I run the apt version of docker on a Ubuntu 20.04 LTS server and one of my docker containers manage to send packets that hit my firewall/routers LAN interface with it's docker internal IP intact (172.17.0.3). The peculiar thing is this only affects a few connections from the container, most of it's traffic is MASQUERADED as it should. Everything works, I can ping internet addresses from within the container, I can access the container through all exposed ports as I should. It's just these few packets that gets blocked in my firewall since they come from the wrong subnet. By far the majority of the traffic from the container gets MASQUERADED as it should.

The container is running linuxserver's qbittorrent image.

If I tcpdump I can see the packets leaving the physical nic with the docker local source IP still set.

I've tried setting up a trace by adding a TRACE target in the RAW tables OUTPUT chain and added a specific SNAT rule for just this docker local IP on the NAT tables POSTROUTING chain. Nothing gets logged and no difference in behavious. I'm quite sure the packets don't traverse the iptables chains.

I started a thread on the docker forums to get some help but it's been quite silent there (the title should probably be POSTROUTING MASQUERADE not applied...).
[POSTROUTING SNAT not applied on all outgoing traffic - General Discussions - Docker Forums]("https://forums.docker.com/t/postrouting-snat-not-applied-on-all-outgoing-traffic/109542/5")

Anyway, is there any way to trace the packets leaving the physical interface with the source ip set to the docker local IP to understand why these few packets aren't handled as 99.9% of their siblings?

---


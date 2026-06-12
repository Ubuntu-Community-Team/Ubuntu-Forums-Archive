---
title: "Load balancing and failover across two ISPs"
date: 2014-04-02
forum: Networking &amp; Wireless
---

### Post by lincoln-stein on 2014-04-02
I thought folks on this forum might be interested in a DIY solution I put together for load balancing across two or more Internet Service Providers (ISPs) using a Linux-based home router and conventional Cable & DSL modems. You can find a full HOWTO at [lstein.github.io/Net-ISP-Balance]("http://lstein.github.io/Net-ISP-Balance").

**Motivation**: After an ice storm in Toronto brought down my family's internet for nearly a week, I decided to run both cable and DSL connections simultaneously via two independent ISPs. After a lot of research and experimentation, I was able to configure my home Ubuntu-based router so as to combine the bandwidth across both ISP connections when both connections are working well, and to automatically fail over to one or the other connections when one ISP becomes unavailable. The system has now been running for a couple of months, during which time one of the ISPs briefly lost connectivity a couple of times. Both times this happened the failover worked automatically and nobody noticed the outage.

**How it Works**: The load balancing occurs at the per-connection level. Although no single connection sees the combined bandwidth of the two ISPs, the family as a whole sees double the bandwidth. BitTorrent transfers are also blazingly fast because a single BitTorrent is composed of many individual connections. The balancing uses two techniques: multipath routing for connections originating or terminating on the router itself, and iptables-managed firewall marks for connections originating or terminating within the LAN. I'm using an open source package called Link Status Monitor (LSM) to periodically ping known good hosts via each of the ISPs and to invoke a script that adjusts the routing and firewall tables when the connectivity changes.

**Lessons learned**: The main difficulty I ran into was that though there are many HOWTOs on the web to do this, none of them worked 100%. In some cases the recipes were designed for older versions of the kernel, while others handled either load balancing or failover but not both. None of the handful of comprehensive packages I tried worked as advertised.

**Software Package: **To make it easier for others to reproduce my setup I've distilled what I learned into an open source package called Net-ISP-Balance. You can find it on GitHub at [lstein.github.io/Net-ISP-Balance]("http://lstein.github.io/Net-ISP-Balance"). It works well with Debian-based Linux distributions such as Ubuntu and Mint, as well as RedHat-based distributions such as CentOS. The package is highly configurable and will support a number of network topologies, including three or more ISPs, private subnetworks, VPNs, incoming services and so forth.

---

### Post by tetractys on 2014-09-10
Great.
I'll test it soon. Thank you to share!
David

---


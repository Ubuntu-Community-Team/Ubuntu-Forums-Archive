---
title: "Any good ubuntu-based web filtering packages for a smallish office?"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by syntek on 2007-05-11
I'm managing a smallish (30 or so PCs) network that's a few Windows 2003 servers and a bunch of XP Pro machines. We've got a DSL modem (requiring PPPoE) and I'm tasked with setting up a proxy server that we can VPN into. Obviously management would like to be able to monitor individuals internet usage, and block certain websites.

I could easily setup a Win2k3 Server with ISA Server to do the trick, but would prefer an open source solution based off Ubuntu, which I've been running on all of my home PCs since 4.10 and now 7.04.

We already have the hardware, but I've never used Linux as a firewall/proxy/VPN server. I was considering installing 7.04 on the box, but would like to know what packages I can use for this.

I would also require the server to host a site presumably running Apache/PHP so management can login and see how employees are spending their time online. Something easy for them to use, that can filter content so it's easy to understand is important, pretty graphics and charts would be a plus.

I've seen some great 3rd party systems for ISA server, and was basically wondering if there was anything equivalent in the linux arena.

Any tips, links, or advice would be greatly appreciated and helpful.. So, thanks in advance for any info!

---

### Post by spd106 on 2007-05-12
Squid Cache and Dans Guardian are among the most popular proxy and web-filtering solutions on Linux systems. I don't have any particularly useful links though. 

This is a topic that is often discussed in the server and security sub-forum, so perhaps have a look through the threads over there.

---


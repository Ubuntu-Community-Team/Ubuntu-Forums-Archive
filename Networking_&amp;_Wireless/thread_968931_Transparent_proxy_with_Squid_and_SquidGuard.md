---
title: "Transparent proxy with Squid and SquidGuard?"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by Gurth12345 on 2008-11-03
For a computer running Ubuntu 7.04 in a classroom environment, I've set up a web filter to block unwanted content, using Squid and SquidGuard following the article at [help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard). This works fine, but I now need to set it up for transparent filtering so users can't simply change the preferences in Firefox to get round the filter. Basically, I want all http traffic to go through Squid automatically without the need to configure the web browser to do so.

My problem now is that I can find all sorts of generic instructions for setting up a firewall for this purpose using iptables, and instructions for Squid + Dansguarding, but none for the Squid/SquidGuard combo from the article above -- and I don't particularly want to spend *another* week becoming an expert on Linux firewalls just to set up this one thing ... So I guess I'm looking for the exact commands needed to set up the iptables to do this :)

Thanks in advance :)

---


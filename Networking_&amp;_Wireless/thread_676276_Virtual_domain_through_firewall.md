---
title: "Virtual domain through firewall?"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by stewartbutler on 2008-01-23
I think those are the terms I am looking for. My problem is this: I own a domain name, for the sake of this document we can assume it is domain.com. I have all my computers positioned behind a firewall running Ubuntu 7.10, running dnsmasq and shorewall, that is named Gebler (Xenogears reference). My primary server is a Fedora 8 system, named Solaris.

I want to configure my domain so that I can run the command "ssh solaris.domain.com" from * outside the local network * to connect to solaris, and similarly run "ssh gebler.domain.com" to connect to Gebler.

My question is, what modifications are necessary to allow this, if it is even possible? I know that you can redirect, say, [www.domain.com](www.domain.com) to a different server than ftp.domain.com, but I am not sure how this works behind a domain. Would this setup work, or am I barking up the wrong tree entirely?

--Stewart

---


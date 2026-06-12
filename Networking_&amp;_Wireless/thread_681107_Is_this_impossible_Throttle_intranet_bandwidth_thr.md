---
title: "Is this impossible? Throttle intranet bandwidth through linux firewall"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by gat0man on 2008-01-28
Hi all,

I am relatively new to linux yet am quite intuitive so please keep any replies understandable for a newer user if this is possible :p

I have a small office network, the T1 line goes into a linux firewall box running some old version of red hat with iptables set up as our company's firewall, and from that machine to our cheap switch with no management features such as QoS which would make this quite a bit easier. This machine was set up before I came here and I can access it and am pretty comfortable with the console/editing iptables/installing stuff or whatever.

So we have someone in our office who is not computer savvy at all, and uses a windows based stock monitering program that absolutely kills our available bandwidth. As this person is the owner of the company and comes from a culture and era as well as has an attitude towards this office that would make it near-impossible to negotiate him NOT using this stock monitoring software, I would like to throttle the available bandwidth to his computer, and I'm guessing the best way to do this would be to set something up like tc on the linux firewall machine that feeds our internet line, all nice and malicious-traffic free, into our switch.

I've spent a good hour reading these and other forums, googling, reading old newsgroup postings, and am stuck. Does anyone have any advice on how to throttle this user's bandwidth by setting up something/changing something with iptables on the linux firewall? Thanks much.:guitar:

---

### Post by HermanAB on 2008-01-28
I think it  is described in the Advanced Routing Howto on tldp.org.  Also, if you compile netfilter from source code, then you can enable many features that are not normally available.  Rusty Russel's website will have more information.

Cheers,

Herman

---


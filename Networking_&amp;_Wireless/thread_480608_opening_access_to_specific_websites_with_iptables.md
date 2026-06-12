---
title: "opening access to specific websites with iptables"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by jhloaded on 2007-06-21
Good afternoon everyone,

I had the good fortune of picking up Linux on the fly after a recent departure by our Linux sys admin.  Being completely new to the Linux environment, I have already picked up quite a bit.  However, I stumbled on a problem with iptables.  Currently we have our laptops with locked access to everything except our internal network.  What I want to do is open up a specifc set of IP ranges for certain websites while continuing to restrict all other websites.  Below is a snapshot of what we are currently using:

> Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
REJECT     all  --  anywhere            !customer-reverse-entry.69.59.144.116 reject-with icmp-port-unreachable

My first question is how would I add an opening for the computer to access yahoo.com and continue to restrict access to all other non-internal websites?

My second question is more for my own knowledge.  Would it be possible for someone to provide a simple explanation of what the INPUT & OUTPUT chains are actually doing here?  

I appreciate any help with this.  

Thank you,

---


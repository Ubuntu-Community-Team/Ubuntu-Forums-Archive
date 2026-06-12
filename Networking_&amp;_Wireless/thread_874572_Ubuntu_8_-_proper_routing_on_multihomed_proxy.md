---
title: "Ubuntu 8 - proper routing on multihomed proxy"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by intercept_ns7 on 2008-07-30
The setup: 30 user windows domain connected to a DSL router. Fixed IPs.

The objectives: Install a linux based proxy to filter http traffic between clients and DSL router. The filter must have per user level control. Clients must still be able to pop to the internet.

What I have done so far:
- Installed webmin and squid onto a multihomed ubuntu 8.04 desktop box. Set 192.168.1.0 on internal network, 10.0.0.0 external to router. Configured NAT on webmin with often incomplete online guides.
- The routing and proxy seems to work fine, but the problem is I can not get the clients to pop to internet mail servers. I can't ping the pop servers on the net but the domains does resolve to IPs from a client, and the mail clients (TBird) cant get mail.
- After some more webmin fiddling I could pop to the internet. But everything was open and bypassing the proxy was as easy as changing the settings in the browsers, which defeats the purpose of the whole exercise off course.

It is probably clear that I am a routing/linux noob.

So the questions: How do I get to set this up so pop access and the HTTP proxy works simultaneously without it being too easy to bypass? Am I on the right track here at least? Is there an easier way to do this, perhaps a single program of some sort? Scripts perhaps?

---


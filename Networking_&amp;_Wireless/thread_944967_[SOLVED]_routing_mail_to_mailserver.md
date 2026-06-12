---
title: "[SOLVED] routing mail to mailserver"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by belfasttim on 2008-10-11
Hi all--

I set up a dedicated machine called zimbra on my home network to be a mail server (trying out the zimbra collab. suite). I have bind9 working on another machine (call it www) that serves as webserver, DNS server (bind9) and storage. DynDNS handles the IP issues, sending traffic from the internet to my IP.

The zimbra machine has an mx record in the bind9 zone and as far I can tell the zone is configured correctly. However, I don't know how to route the mail from the internet so it gets to the right machine internally. For www stuff I just used my router's port forwarding, to send port 80 requests to the www machine, and it works great, the [www.mysite.com](www.mysite.com) works fine from inside and outside the network.

I thought that if I forwarded the normal mail ports to the zimbra machine that might work too-- unfortunately, it doesn't. Outbound mail (form zimbra to the internet) works fine. But mail from the internet to zimbra never arrives.

What am I missing? 

Thanks for any help.

---

### Post by belfasttim on 2008-10-12
ok, turns out it was a badly formed A-record on the zimbra machine. so the port forwarding at the router does work, which is nice.

---


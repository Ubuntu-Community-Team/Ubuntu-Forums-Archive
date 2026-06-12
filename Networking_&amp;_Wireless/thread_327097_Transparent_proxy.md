---
title: "Transparent proxy"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by Baddox on 2006-12-28
Hey guys, I've finally found some time to delve back into Linux (it's been a good year, sadly).  Right now, I'm wanting to set up a transparent proxy for my home LAN.  I've got a machine with ubuntu 6.10 installed.  What I'm wondering, is there any way to make a transparent proxy WITHOUT that computer also being the router to the outside world?  I don't know if this would work, but it seems that if I instructed my router (cheap D-Link) to assign everyone in my LAN (through DHCP) my linux box as the gateway instead of the D-link, then everything would first go through the linux box, thereby making the proxy work transparently.  Please let me know if I'm way off base here.  Thanks folks.

---

### Post by koenn on 2006-12-31
you sort of got the right idea.
Your proxy machine would still have to provide a route to the internet for applications your proxy can not handle  - assuming you want a http proxy : non-http traffic should still find its way to the internet, and as your 'proxy' is the default gateway, he'lll have to handle it because  your hosts will send all traffic (except with destination LAN) to their 'gateway'.

---

### Post by Baddox on 2006-12-31
Ok, that makes good sense.  So could I set up a simple router on the linux box (proxy) that would forward everything (other than http traffic which squid would handle) on to the d-link router?  Is that a relatively simple task?

---

### Post by jonathan.lees on 2006-12-31
I've had this [link]("http://wiki.squid-cache.org/SquidFaq/InterceptionProxy") in my.del.icios, the squid faq/InterceptionProxy or how can I make my users browsers use my cache without configuring the browsers for proxying!

---

### Post by Baddox on 2006-12-31
Thanks a lot man!  That looks like good stuff (I'll get around to reading it soon hopefully).

---

### Post by koenn on 2006-12-31
> **Baddox said:**
> Ok, that makes good sense.  So could I set up a simple router on the linux box (proxy) that would forward everything (other than http traffic which squid would handle) on to the d-link router?  Is that a relatively simple task?

relatively simple, yes. 
it involves setting up squid and configuring it. You'll have to edit the squid conf file and have a reasonbably good idea of what your doing in order to fill in the correct values or enable/disable certain statements. There's a lot of explication in the file itself. 

You'd need iptables to detect traffic to any IP address : tcp port 80 and redirect it to your proxy : port 3128 (or the port you'll have squid listening on)? This is a tricky part, because the replies (the webpages) also need to find their way back to the host that requested them. They'll expect a return from some webserver on the internet, not from your proxy. 
you may have to look up some iptables (aka netfilter, aka many 'firewall' frontends) documentation to get it right - it may involve some NAT or Masquerading stuff.   

Then, if you make the D-link router the default router for the proxy machine, 
- it will be able to connect to web servers on the internet
- it can route traffic from hosts to internet via its default route

Judging from the TOC, the link you got deals with all of this, but on first sight the routing question is handled a bit differently. 
There is, in fact a 2nd way of doing this, by letting the router (in your case : the D-link) do the rerouting of "port 80" traffic to the proxy. This is called policy-based routing, and I'm not sure that D-Link can do it. Letting the linux box handle the routing between the hosts and the D-link is imho a valid alternative. 


When you've worked out the details, check that you did not create routes directly from the internet into your proxy or other hosts on the LAN as well. That would be kinda silly, and dangerous.

---


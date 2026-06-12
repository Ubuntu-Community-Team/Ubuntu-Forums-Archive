---
title: "OpenVPN and stopping Windows 8 DNS lookups"
date: 2015-05-09
forum: Networking &amp; Wireless
---

### Post by Jason_Burrell on 2015-05-09
I have a setup over here which involves OpenVPN. When my Windows machine connects to it, all traffic is supposed to be diverted through the VPN interface. While I only trust Windows about as far as I can throw it on doing what it's supposed to do, I've run into something curious with DNS lookups.

OpenVPN sets the default route to run through the server. I can verify that this is the case, as if I block traffic on the VPN server things break on the client side. However, I want to have the thing use **only** a specific DNS server. Logic would dictate that you either push this as a DHCP option, or you manually configure the TAP interface to use the internal DNS server. Here's the weiredness:

If I kill the internal DNS server, the client should have no place to connect to in order to resolve a domain name. When I do this, it does take noticably longer for each DNS lookup, but Windows manages to find it anyway. This implies to me that Windows is going off of its own accord and using some hardcoded secondary DNS server. I haven't gone as far as to load up a packet sniffer yet and analyze that, but it seems the only possibility. 

How the hell do I get Windows to stop doing that, and do what it's supposed to do? (In this case, if the internal DNS server is down, then break.)

For anyone wondering why I care, it has to do with security. If I use my internal DNS server, I could theoretically tunnel the requests, run it through Tor, or whatever. With Windows going off and doing this crap, it's leaking information in cleartext to the network by the way of DNS lookups.

---


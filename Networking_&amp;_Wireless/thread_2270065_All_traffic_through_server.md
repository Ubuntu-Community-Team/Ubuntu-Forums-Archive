---
title: "All traffic through server"
date: 2015-03-20
forum: Networking &amp; Wireless
---

### Post by Tanner_White on 2015-03-20
Hi,

I am interested in redirecting all traffic from a LAN through a Ubuntu server with the ability of blocking or redirecting certain domains or IP addresses. I want to do something similar to OpenDNS but on a LAN level...

Does anyone know an efficient way of going about this? There is one server, three Windows PCs and a couple of mobile devices on this network. 

I don't really have any reason for doing this other than just learning how. 

Any help would be appreciated. Thank you!

---

### Post by papibe on 2015-03-20
Hi Tanner_White. Welcome to the forum ):P

This is not trivial, but it is can be done with some work.

There are several 'levels' on what you can control what's happening in your network.

You should start taking a look at your DHCP server. In most cases, it is your ISP router. That is the protocol the server uses to give 'network' information to the machine that what to get into the LAN (and access the Internet).

There are 2 important pieces of information that are relevant: the DNS server, and the default gateway.

**DNS**
If you can control which DNS server to give to your local machines, you can effectively block domain names from being translated to proper addresses. For instance, you can set that facebook.com be translated in something invalid like 0.0.0.0

You would have to setup  a local DNS server in order to do that. There are 2 common options: dnsmasq and bind.

**Gateway**
You can also give the machines a different address than the router to pass the traffic to the Internet. If you point your machines to one of your own, you can setup a transparent proxy. Then you can add rules on which traffic should be allowed and what not. Squid is a common alternative to setup a proxy, and iptables for filtering rules.

Another step would be to turn off your DHCP service in your router, and setup your own. You can do that with dnsmasq or isc-dhcp-server,

Does that help? Let us know if you have more questions or if you need more details on one of the subjects.

Come here often and have fun.
Regards.

---


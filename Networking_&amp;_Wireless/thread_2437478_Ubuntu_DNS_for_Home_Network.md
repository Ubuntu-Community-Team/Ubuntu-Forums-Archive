---
title: "Ubuntu DNS for Home Network"
date: 2020-02-24
forum: Networking &amp; Wireless
---

### Post by ob2s on 2020-02-24
My router has static IP addresses for DNS and seems to be dns.google, I'd like to put the ip address of my ubuntu box first and have it look in /etc/hosts and if it not there go to dns.google -> 8.8.8.8. This seems like it would not be too complicated to do, but I can't sort it out without posts I see where you do full implementation with a domain name etc. I just want to be able to do in my home network [http://outsidelights](http://outsidelights)  so I don't have to memorize the ips of my ICTs (internet control of things, internet of things [iot] is too vague a term for my taste).
Thanks !

---

### Post by TheFu on 2020-02-24
/etc/hosts is not DNS.  It can't only be used by the local machine.  Sadly, the hosts file doesn't have all the necessary details that a DNS server needs.

You can use avahi, DNS, or copy the hosts file to each of your systems.  Avahi works with many Unix desktops. It is the Linux zeroconf implementation.  When hosts get on a network, they announce their IP and hostname.lan to other zeroconf listeners on the same subnet.  To access a hostname, romulus, from another system, use romulus.local (or is it romulus.lan?), I never recall.  I disable avahi on my network. I don't remember ever seeing avahi on any server.

DNS can be provided by any Unix system on the network. Many routers have a method to run a local DNS with lookups for local systems too.  My attempt to explain this with an example for dd-wrt: [https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)
Many people have decided to use a local DNS AND ad-blocking DNS by installing a pi-hole.  [https://pi-hole.net/](https://pi-hole.net/)  It works on any Linux, but also works using a cheap Raspberry Pi computer.

And of course, you can copy the /etc/hosts files to all the system on your subnet. I do this for all the computers, but that doesn't help IoT or network TV-tuners or locked android devices.

Anyway, you have a few options.

---

### Post by ob2s on 2020-02-24
Thanks, so I will never be able to configure my ubuntu server to serve up an ip address to my ipad if I use an URL like [http://lightswitch](http://lightswitch) ? or [http://lightswitch.local](http://lightswitch.local) ?

---

### Post by wildmanne39 on 2020-02-24
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by TheFu on 2020-02-24
> **ob2s said:**
> Thanks, so I will never be able to configure my ubuntu server to serve up an ip address to my ipad if I use an URL like [http://lightswitch](http://lightswitch) ? or [http://lightswitch.local](http://lightswitch.local) ?

Not what I intended to say.

  You can setup a DHCP+DNS server on your ubuntu server if you like.  Those are not usually attempted by beginners. Apple uses IP just like every other Unix like OS.  You didn't say anything about a router on the network, so I didn't assume there was one. Having a router for a subnet solves all sorts of these little problems.  Not having a router means each system has to be individually, manually, configured. A $5 router makes this a solved problem.

If you can modify the /etc/hosts file on the ipad, then you can use [http://lightswitch/](http://lightswitch/) immediately.  If apple doesn't allow it, complain to Apple.

---

### Post by kevdog on 2020-02-24
I'm not sure you can modify the /etc/hosts file on an ipad unless you unlock it.  Your choice for name resolution are going to be either at the individual host level - /etc/hosts or by running a dns server or dns resolver at the router level.  At the router level you would add a DNS override that would map lightswitch to an IP address on the LAN (or I suppose it could be elsewhere).   Usually on the individual hosts the DNS servers are setup to first query the router (ie like 192.168.1.1 or 10.0.1.1) and then have secondary options such as Google (8.8.8.8 or 8.4.4.8) or Cloudflare (1.1.1.1) for example.  I'm not sure if cheap consumer routers have the ability for a DNS override but from my Linksys WRTGL days - I believe they do.  Honestly its been so long since I'm now using pfsense as my router software (which btw if you have either that hardware or capability to virtualize pfsense within a VM is a great little side project).

---


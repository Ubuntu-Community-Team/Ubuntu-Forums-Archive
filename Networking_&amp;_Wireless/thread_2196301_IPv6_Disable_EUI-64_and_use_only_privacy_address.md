---
title: "IPv6: Disable EUI-64 and use only privacy address?"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by martinblank64 on 2013-12-28
I'm running Lubuntu 13.10 (32-bit version) and I have manually configured static IPv4 addressing and auto IPv6 configuration by editing my /etc/network/interfaces file, which is shown below in the attached image. The extent of my IPv6 configuration is just the one auto line.

The issue that I have is that this configuration results in eth0 being assigned two global IPv6 addresses, one using the privacy extensions that has a randomized interface ID, and another that is generated with EUI-64 and has an interface ID using my MAC address.

I want to totally disable the EUI-64 generated address so that I have just a single global IPv6 address, the one generated with a random interface ID. How can I achieve this?

---

### Post by Whoopie on 2013-12-29
Quoting [http://andatche.com/blog/2012/02/disabling-rfc4941-ipv6-privacy-extensions-in-windows/:](http://andatche.com/blog/2012/02/disabling-rfc4941-ipv6-privacy-extensions-in-windows/:)

> 
Normally, when using privacy extensions it’s typical to maintain the  EUI-64 derived address on an interface for inbound connections while  using RFC 4941 temporary addresses when establishing outbound  connections. This offers a balance between privacy and the convenience  of static addressing and is the default when using RFC 4941 on Linux or  OS X.


So, why would you disable EUI-64? From my point of view, it makes no sense, as the temporary addresses are always used for outbound connections.

---

### Post by martinblank64 on 2013-12-29
I know what it is for but it doesn't make sense. Neither of the addresses are static (the prefix can change). Unless there is some other reason that I am missing? I would like to configure the privacy address for both inbound and outbound connections, and remove the EUI-64 address. Is that even possible?

---

### Post by sanderj on 2013-12-30
> **martinblank64 said:**
> remove the EUI-64 address. Is that even possible?

Have you even tried? [http://www.tldp.org/HOWTO/Linux+IPv6-HOWTO/x1050.html](http://www.tldp.org/HOWTO/Linux+IPv6-HOWTO/x1050.html)

---

